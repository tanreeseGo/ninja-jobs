<template>
    <div v-if="job">
        <h1>{{ job.title }}</h1>
        <p>The job id is {{ idss }}</p>
        <p>{{job.details}}</p>
    </div>
    <div v-else>
        <p>loading job details...</p>
    </div>
    
    
</template>

<script>
export default {
    props: ['idss'],
    data() {
        return {
    //         id: this.$route.params.idss

            job: null
        }
    },
    mounted() {
        fetch('http://localhost:3000/jobs/' + this.idss)
            .then(res => res.json())
            .then(data => this.job = data)
            .catch(err => console.log(err.message))
    }
}
</script>

<style>

</style>