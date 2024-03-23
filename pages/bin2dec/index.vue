<script setup lang="ts">
const bin =  ref('')

const dec = computed(() => {
  if (bin.value === '') return 0
  if (message.value) return 0
  return parseInt(bin.value, 2)
})

const isValidBinary = computed(() => {
  if (/\D/.test(bin.value)) return false
  if (/[23456789]/.test(bin.value)) return false
  return true
})

const message = computed(() => {
  if (!isValidBinary.value) return 'Only 0 and 1 is allowed.'
  return ''
})
</script>

<template>
  <div class="bin2dec">
    <div class="container">
      <label for="binary">Binary: </label>
      <input
        id="binary-input"
        v-model="bin"
        type="text"
        name="binary"
      >
      <p v-if="message">
        {{ message }}
      </p>
      <p v-else>
        Decimal: {{ dec }}
      </p>
    </div>
    <NuxtLink to="/">
      Back to Home
    </NuxtLink>
  </div>
</template>

<style scoped>
.bin2dec {
  position: relative;
  width: 100vw;
  height: 100vh;
  background-color: #2dd7c3;
}

.container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  padding: 2rem;

  width: 20rem;
  background-color: white;
  border-radius: 1rem;
}
</style>