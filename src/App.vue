<template>
  <div id="app">
    <h1>word translator</h1>
    <h5>powered by vue js</h5>
    <TranslateForm v-on:formSubmit="translateText"> </TranslateForm>
    <TranslateOutput v-text="translatedText"> </TranslateOutput>
  </div>
</template>

<script>
/* eslint-disable */
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function(){
    return {
      translatedText:''
    }
  },
  methods: {
    translateText:function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181027T202818Z.a13a32ff0dda253b.d7343ddd7a74a719baa61b39f079b4e47dbb3276&lang='+language+'&text='+text)
      .then((response) => {
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
  body {
    background: #fefefe;
  }
</style>
