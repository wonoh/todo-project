<template>
  <div class="container">
    <h2>Todo List</h2>
    <div class="input-group" style="margin-bottom:10px;">
      <input type="text" class="form-control" placeholder="할일을 입력하세요" v-model="name"
        v-on:keyup.enter="addTodo(name)">
      <span class="input-group-btn">
      <button class="btn btn-default" type="button" @click="addTodo(name)">추가</button>
    </span>
    </div>
    <ul class="list-group">
      <li class="list-group-item" v-for="(todo, index) in todoList">
        {{todo.name}}
        <div class="btn-group pull-right" style="font-size: 12px; line-height: 1;">
          <button type="button" class="btn-link dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            더보기<span class="caret"></span>
          </button>
          <ul class="dropdown-menu">
            <li><a href="#" @click="deleteTodo(index)">삭제</a></li>
          </ul>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
    export default {
        name: "TodoList",
      data (){
          return {
            name: null,
            todoList: [
              {
                name:'스프링'
              },
              {
                name:'알고리즘'
              }
            ]
          }
      },
      methods:{
        /**
         * todo name 을 입력받아 (input tag v-model="name") todoList push
         * @param name
         */
          addTodo (name) {
              if(name != null){
                this.todoList.push({name:name}); // todoList array  push
                this.name=null; // input 값 초기화 v-model 로 양방향 바인딩
              }
          },
        /**
         * 삭제할 todo 항목의 index 를 받아 목록에서 index 삭제
         * @param index
         */
        deleteTodo (index) {
            console.log(index)
            this.todoList.splice(index,1)
        }
      }
    }
</script>

<style scoped>

</style>
