<template>
  <div class="tab-control" >
    <div v-for="(item,index) in titles" :key="item.index" 
    class="tab-control-item" 
    :class="{active: index===currentIndex}" @click="itemclick(index)">
      <span>{{item}}</span>   
    </div>
  </div>
</template>

<script>
  export default {
    name:'TabControl',
    props:{
      titles:{
        type:Array,
        default(){
          return []
        }
      }
    },
    data(){
      return {
        currentIndex:0
      }
    },
    methods:{
      itemclick(index){
        this.currentIndex = index
        this.$emit("tabClick",index)
      }
    }
  }
</script>

<style scoped>
  .tab-control{
    display: flex;
    height: 40px;
    line-height: 40px;
    font-size: 15px;
    text-align: center;
  }
  .tab-control-item{
    
    flex:1;

  }
  .active{
    color:var(--color-high-text);
    
  }
  .tab-control span{
    padding: 5px;
  }
  .active span{
    border-bottom: 3px solid var(--color-high-text);
  }
</style>