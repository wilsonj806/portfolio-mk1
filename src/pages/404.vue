<template>
<section>
  <h1>404 Page not found!</h1>
  <h2>Perhaps you meant:</h2>
  <ul>
    <li v-for="(page, index) in pages" :key="index">
      <g-link :to="page.path">{{ page.path }}</g-link>
    </li>
  </ul>
</section>
</template>

<page-query>
query {
  allPage {
    path
  }
}
</page-query>

<script>
export default {
  name: 'Base404Page',
  computed: {
    pages() {
      return this.$page.allPage.filter(page => page.path !== '/404/');
    }
  }
}
</script>

<style>

</style>