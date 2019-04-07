<template>
  <div id="app">
  		{{msg}}

  		<div>
  			<!-- v-model 双向绑定 -->
  			<input type="text" name="输入框" v-model='info'>
  			<button @click='handleClick'>提交</button>
  		</div>

  		<ul>
  			<todo-item v-for="item in list" :key="item" >
  			    <template v-slot:item="itemProps">
  			        <span :style="{fontSize: '20px', color: itemProps.checked ? 'red' : 'blue'}">{{item}}</span>
  			    </template>
  			</todo-item>
  		</ul>
  	</div>
</template>

<script>
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'app',
  data() {
        return {
            msg: 'hello syj',
            info: '',
            list: []
        }
    },
    methods: {
        handleClick() {
            console.log(this.info)
            this.list.push(this.info)
            this.info = ''
        }
    },
  components: {
    TodoItem
  }
}
</script>

<style>
</style>
