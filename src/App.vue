<template>
 <p> Hello </p>
</template>

<script>
import Icon from './components/icon.vue'
import Swal from 'sweetalert2/dist/sweetalert2.js'

export default{
  name:'App',
  components:{Icon},
  data(){
    return{
      winMessage: '',
      isCross:true,
      itemArray: new Array(9).fill("empty")
    }
  },
  watch:{
    winMessage: function(message){
      if(message){
        this.showDialog();
      }
    }
  },
  methods:{
    showDialog(){
      Swal.fire({
        icon:"info",
        title:"GAME OVER",
        text:`${this.winMessage}`
      })
    },
    handleClick(itemNumber){
      if(this.winMessage){
        this.showDialog()
      }
      if(this.itemArray[itemNumber]==='empty'){
        this.itemArray[itemNumber]=this.isCross?"cross":"circle";
        this.isCross=!this.isCross
      }
      else{
        return Swal.fire("Already Filled")
      }
      this.checkIsWinner()
    },
    checkIsWinner(){
      //checking winner of the game
      if(this.itemArray[0]===this.itemArray[1] && 
      this.itemArray[0]===this.itemArray[2] && 
      this.itemArray[0]!="empty")
      {
        this.message=`${this.itemArray[0]} Won`


      }
      else if(this.itemArray[0]===this.itemArray[3] && 
      this.itemArray[0]===this.itemArray[6] && 
      this.itemArray[0]!="empty")
      {
        this.message=`${this.itemArray[0]} Won`


      }
      else if(this.itemArray[0]===this.itemArray[4] && 
      this.itemArray[0]===this.itemArray[8] && 
      this.itemArray[0]!="empty")
      {
        this.message=`${this.itemArray[0]} Won`


      }
      else if(this.itemArray[1]===this.itemArray[4] && 
      this.itemArray[1]===this.itemArray[7] && 
      this.itemArray[1]!="empty")
      {
        this.message=`${this.itemArray[1]} Won`


      }
      else if(this.itemArray[2]===this.itemArray[5] && 
      this.itemArray[2]===this.itemArray[8] && 
      this.itemArray[2]!="empty")
      {
        this.message=`${this.itemArray[2]} Won`


      }
      else if(this.itemArray[2]===this.itemArray[4] && 
      this.itemArray[2]===this.itemArray[6] && 
      this.itemArray[2]!="empty")
      {
        this.message=`${this.itemArray[2]} Won`


      }
      else if(this.itemArray[3]===this.itemArray[4] && 
      this.itemArray[3]===this.itemArray[5] && 
      this.itemArray[3]!="empty")
      {
        this.message=`${this.itemArray[3]} Won`


      }
      else if(this.itemArray[6]===this.itemArray[7] && 
      this.itemArray[6]===this.itemArray[8] && 
      this.itemArray[6]!="empty")
      {
        this.message=`${this.itemArray[6]} Won`


      }
      


    },
    reloadGame(){
      this.winMessage = " ";
      this.isCross =true;
      this.itemArray = new Array(9).fill("empty")
    }
  }
}
</script>

<style>
main {
  height: 100vh;
}
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 5px;
}

.box {
  height: 150px;
}
</style>
