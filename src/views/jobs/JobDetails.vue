<template>
    <h1>Job Details Page</h1>
    <div v-if="job">
        <p>The job id is {{id}}</p>
        <p>Job: {{job.title}}</p>
        <p>Details: {{job.details}}</p>
    </div>
    <div v-else>
        <p>Loading job details...</p>
    </div>
</template>

<script>
export default {
    props: ['id'],
    data() {
        return{
            job: null
        }
    },
    mounted(){
        fetch('http://localhost:3000/jobs/'+this.id)
            .then(resp => resp.json())
            .then(data => this.job = data)
            .catch(err => console.log(err.message));
    }
}
</script>

<style>

</style>