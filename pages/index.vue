<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <p>{{ description }}</p>
    <NuxtLink to="/other">
      otherへ
    </NuxtLink><br>
    <validation-observer ref="obs" v-slot="ObserverProps">
      <validation-provider v-slot="ProviderProps" rules="required">
        <div class="form-group">
          <label for="name" class="d-inline">お名前</label>
          <input
            id="name"
            v-model="name"
            type="text"
            name="名前"
            class="form-control d-inline col-3"
          >
          <div class="error">
            {{ ProviderProps.errors[0] }}
          </div>
        </div>
      </validation-provider>
      <button
        type="button"
        :disabled="ObserverProps.invalid || !ObserverProps.validated"
      >
        送信
      </button>
    </validation-observer>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title: 'Nuxt.js',
      description: 'let`s learning Nuxt.js'
    }
  }
}
</script>
<style>
.container {
  padding: 30px
}
</style>
