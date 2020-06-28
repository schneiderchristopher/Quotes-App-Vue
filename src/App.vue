<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quotes-grid :quotes="quotes" @quoteDeleted="deleteQuote()"></app-quotes-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a quote to Delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>
import QuotesGrid from "./components/QuotesGrid.vue";
import NewQuote from "./components/NewQuote.vue";
import Header from "./components/Header.vue";

export default {
  data() {
    return {
      quotes: [
        "Just a quote to start with",
        "It's my life, it's now or never."
      ],
      maxQuotes: 10
    };
  },
  components: {
    appQuotesGrid: QuotesGrid,
    appNewQuote: NewQuote,
    appHeader: Header
  },
  methods: {
    newQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        return alert("Please delete quotes first.");
      }
      this.quotes.push(quote);
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  }
};
</script>

<style>
</style>
