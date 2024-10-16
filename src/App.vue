<template>
  <div>
    <h2>Task List</h2>
    <input v-model="newTask" placeholder="Add a new task" />
    <button @click="addTask">Add Task</button>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
        <button @click="removeTask(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '', // Holds the input for a new task
      tasks: [],   // Array to store the list of tasks
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) { // Check if new task is not empty
        this.tasks.push(this.newTask.trim()); // Add new task to the list
        this.newTask = ''; // Clear the input field
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1); // Remove task at the specified index
    },
  },
};
</script>

<style scoped>
input {
  margin-right: 10px;
}
button {
  margin-left: 5px;
}
ul {
  list-style-type: none;
  padding: 0;
}
</style>