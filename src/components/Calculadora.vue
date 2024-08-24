<script setup>
    import { reactive } from 'vue';
     const estado = reactive({
        primeiroNumero: '',
        segundoNumero: '',
        operacoes: {
        soma: (a, b) => a + b,
        subtracao: (a, b) => a - b,
        multiplicacao: (a, b) => a * b,
        divisao: (a, b) => (b !== 0 ? a / b : 'Divisão por zero'),
    },
        resultado: 0
     })

     const calcularResultado = () => {
    const { primeiroNumero, segundoNumero, operacaoMatematica } = estado;
    estado.resultado = estado.operacoes[operacaoMatematica](parseFloat(primeiroNumero), parseFloat(segundoNumero));
};
</script>

<template>
<div class="container">
    <header class="p-5 mb-5 bg-light">
        <h1>Calculadora</h1>
    </header>
    
    <form action="">
      <div class="row">
        <div class="col-5">
            <input v-model="estado.primeiroNumero" @input="calcularResultado" type="number" class="form-control" placeholder="Digite o primeiro numero">
        </div>
        <div class="col-5">
            <input v-model="estado.segundoNumero" @input="calcularResultado" type="number" class="form-control" placeholder="Digite o segundo numero">
        </div>
        <div class="col-2">
            <select class="mt-3 mb-1"  v-model="estado.operacaoMatematica" @change="calcularResultado" >
              <option value="soma">Soma</option>
              <option value="subtracao">Subtração</option>
              <option value="multiplicacao">Multiplicação</option>
              <option value="divisao">Divisão</option>
            </select>
        </div>
        <span class="mt-5">Resultado: {{ estado.resultado }} </span>
    </div>
    </form>

   
</div>
</template>

<style scoped>
h1{
    text-align: center;
}
 .row{
    align-items: center;
 }
</style>