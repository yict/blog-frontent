<template>
    <div>
        <!-- Page Header -->
        <header class="masthead" :style="{backgroundImage: `url(${GRIDSOME_API_URL+$page.post.cover[0].url})`}">
            <div class="overlay"></div>
            <div class="container">
            <div class="row">
                <div class="col-lg-8 col-md-10 mx-auto">
                <div class="post-heading">
                    <h1>{{ $page.post.title }}</h1>
                    <h2 class="subheading">Problems look mighty small from 150 miles up</h2>
                    <span class="meta">yict
                    <a  href="#">Start Bootstrap</a>
                    on </span>
                </div>
                </div>
            </div>
            </div>
        </header>
            <!-- Post Content -->
        <article>
            <div class="container">
            <div class="row">
                <div class="col-lg-8 col-md-10 mx-auto" v-html="mdToHtml( $page.post.content )"></div>
            </div>
            </div>
        </article>
          <!-- Footer -->
        <footer>
            <div class="container">
            <div class="row">
                <div class="col-lg-8 col-md-10 mx-auto">
                <ul class="list-inline text-center">
                    <li class="list-inline-item">
                    <a href="#">
                        <span class="fa-stack fa-lg">
                        <i class="fas fa-circle fa-stack-2x"></i>
                        <i class="fab fa-twitter fa-stack-1x fa-inverse"></i>
                        </span>
                    </a>
                    </li>
                    <li class="list-inline-item">
                    <a href="#">
                        <span class="fa-stack fa-lg">
                        <i class="fas fa-circle fa-stack-2x"></i>
                        <i class="fab fa-facebook-f fa-stack-1x fa-inverse"></i>
                        </span>
                    </a>
                    </li>
                    <li class="list-inline-item">
                    <a href="#">
                        <span class="fa-stack fa-lg">
                        <i class="fas fa-circle fa-stack-2x"></i>
                        <i class="fab fa-github fa-stack-1x fa-inverse"></i>
                        </span>
                    </a>
                    </li>
                </ul>
                <p class="copyright text-muted">Copyright &copy; Your Website 2020</p>
                </div>
            </div>
            </div>
        </footer>
    </div>
</template>
<page-query>
query ($id: ID!){
  post: strapiPost(id: $id) {
    id
    title
    content
    cover {
      url
    }
    tags {
      id
      title
    }
  }
}
</page-query>
<script>
import MarkdownIt from 'markdown-it';
const md = new MarkdownIt();
export default {
    name: 'PostPage',
    methods: {
        mdToHtml(markHtml) {
            return md.render(markHtml);
        }
    }
}
</script>