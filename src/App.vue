<script setup>
  import { ref } from "vue";

  const results = ref([]);
  const n = ref(0);

  const addN = () => {

    if(isNaN(n.value)) {
      alert('input an integer');
      return
    }

    results.value = [];

    if(n.value == 0) {
      return
    }

    const data = {

      result: n.value

    }

    results.value.push(data);

    compute()

  }

  const compute = () => {

    for(let i = 0; results.value[results.value.length - 1].result !== 1; i++ ) {

        const lastResultsNumber = results.value[results.value.length - 1].result

        if(lastResultsNumber % 2 == 0) {

          const data = {

            result: lastResultsNumber / 2

          }

          results.value.push(data)

        } else {

          const data = {

            result: lastResultsNumber * 3 + 1

          }

          results.value.push(data)

        }

    }

}
  

</script>

<template>

  <main>
    <div class="container">
      <h1> 3n + 1</h1>
      <div class="card">
        <p  v-for="result in results" :key="result.id" >{{ result.result }}</p>
      </div>
      <div class="input-button">
        <div class="input-info">
          <input v-model="n" type="text" name="" id="">
          <span>Input random number</span>
        </div>
        <button @click="addN">Compute</button>
      </div>
    </div>
  </main>

</template>

<style scoped>

  .card p {
    font-size: 12px;
    animation: test123 1s forwards ease;
  }

  @keyframes test123 {
    0% {
      transform: scale(2);
    }

    100% {
      stransform: scale(1);
    }
  }

  main {
    height: 100vh;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .card {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1rem;
    min-height: 20vh;
    max-width: 40vw;
  }

  .input-button {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: .5rem;
  }

  .input-button .input-info input {
    outline: none;
    padding: .5rem;
  }

  .input-info {
    position: relative;
    /* background-color: red; */
  }

  .input-info ion-icon {
    position: absolute;
    right: 2%;
    bottom: 15%;
    color: grey;
    font-size: 1.5rem;
    z-index: 10;
  }

  .input-info span{
    visibility: hidden;
    height: auto;
    width: 100%;
    background-color: green;
    position: absolute;
    color: white;
    left: 0;
    top: 0;
    opacity: 0;
    z-index: 1;
    overflow: auto;
    font-size: .8rem;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: all ease-in 200ms;
    pointer-events: none;
  }

  .input-info:hover span {
    transform: translateY(100%);
    visibility: visible;
    opacity: 1;
  }

  .input-button button {
    background-color: transparent;
    outline: none;
    border: 1px solid white;
    color: white;
    padding: .3rem 1rem;
    cursor: pointer;
  }

  .input-button button:active {
    scale: .95;
  }
</style>
