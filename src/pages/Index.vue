<template>
  <Layout>
    <h1>Welcome to my blog :)</h1>
  </Layout>
</template>

<page-query>
query($page: Int){
  tags: allWordPressPostTag {
    edges {
      node {
        slug
        belongsTo(perPage: 12, page: $page) @paginate {
          pageInfo {
            totalPages
            currentPage
          }
          edges {
            node {
              ...on WordPressPost{
                id
              }
            }
          }
        }
      }
    }
  }
}
</page-query>

<script>
import { Pager } from "gridsome";
import Post from "~/components/Post.vue";

export default {
  components: {
    Pager,
    Post
  },
  metaInfo: {
    title: "Welcome to my blog :)"
  }
};
</script>
