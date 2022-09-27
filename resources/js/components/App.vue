<template>
    <section>
        <h1>Lista Vue</h1>
        <ul>
            <li  v-for="post in posts" :key="post.id">
                {{post.post_title}} with ID = {{post.id}}
            </li>
        </ul>
    </section>
</template>

<script>
import axios from 'axios';

export default {
    data:function(){
        return{
            posts:[],
        }
    },
    methods: {
        getPosts(){
            axios.get('/api/posts')
            .then((result) => {
                console.log(result.data.results.data)
                this.posts = result.data.results.data
            }).catch((err) => {
                console.error(err)
            });
        }
    },
    created() {
        this.getPosts();
    },
}
</script>

<style>

</style>
