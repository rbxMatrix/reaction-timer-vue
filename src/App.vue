<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying"> play</button>
  <Block v-if="isPlaying" v-bind:delay ="delay" @end="endGame"/>
  <p v-if="showResult">Reaction Time : {{ score }} ms</p>
</template>

<script>
import Block from './components/Block.vue'
export default {
  name: 'App',
  components: {Block },
  data(){
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }

  },
  methods:{
    start(){
      this.delay= 2000 +Math.random() * 5000
      this.isPlaying= true
    },
    endGame(reactionT){
      this.score= reactionT
      this.isPlaying= false
      this.showResult= true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
