<template>
  <div>
    <h3>{{user}}</h3>
   <!--  <button @click="toEn">EN</button>
    <button @click="toZh">ZH</button> -->
    <!-- <el-date-picker
      v-model="value"
      type="date"
      :placeholder="$t('account.选择日期')">
    </el-date-picker> -->
    <router-link to="/login">To Login</router-link>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data () {
    return {
      isloop: true
    }
  },
  computed:{
    user(){
      return this.$t('userRole.超级管理员')
    },
  },
  methods:{
    tt(){
      if(this.isloop){
        axios.get('/api/chain_trends',{
          headers:{
            Authorization: 'Token 014ca8fe27070d53c5fee521e6287993416eea6f'
          }
        }).then(r=>{
          console.log('r')
          setTimeout(this.tt,3000)
        }).catch(()=>{
          console.log('error')
          setTimeout(this.tt,3000)
        })
      }
    }
  },
  created(){
    this.tt()
  },
  beforeDestroy(){
    this.isloop=false
    // console.log('beforeDestroy')
    // if(this.timer){
      // clearTimeout(this.timer)
      // this.timer = null
    // }
    // else
    //   setTimeout(()=>{clearTimeout(this.timer)},2000)
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
