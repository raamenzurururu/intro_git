<template>
  <div class="home">
    <div class="list">
      <Item 
        v-for="whisper in orderBy(whispers,'date',-1)"
        :key="whisper.id"
        :id="whisper.id"
        :uid="whisper.uid" 
      />
    </div>
  </div>
</template>

<script>
import Item from '@/components/Item.vue'
import { db } from '../main'
import Vue2Filters from 'vue2-filters'

export default {
  name: 'home',
  data () {
    return {
      whispers: []
    }
  },
  firestore () {
    return {
      whispers: db.collection('whispers')
    }
  },
  components: {
    Item
  },
  mixins: [Vue2Filters.mixin]
}
</script>
