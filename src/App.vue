<template>
  <div class="feedback-form">
    <h1>Feedback Form</h1> <br>
    <p>
      We would love to hear your thoughts, suggestions, concerns or problems with <br> anything so we can improve!
    </p> <b></b> <br>

    <h4>Feedback Types</h4> <br>


    <div class="radio-group">
      <input type="radio" id="one" value="One" v-model="picked" />
      <label for="one">Comments</label>

      <input type="radio" id="two" value="Two" v-model="picked" />
      <label for="two">Suggestions</label>

      <input type="radio" id="three" value="Three" v-model="picked" />
      <label for="three">Questions</label>
    </div> <br>

    <span>Describe Your Feedback:</span>
    <textarea
      v-model="message"
      placeholder="Do not abuse"
      required
      @keyup.enter="submitForm"
      style="width: 100%; height: 150px;"
    ></textarea>

    <label for="first-name">First Name:</label>
    <input
      type="text"
      id="first-name"
      v-model="firstName"
      required
      @keyup.enter="submitForm"
    />

    <label for="last-name">Last Name:</label>
    <input
      type="text"
      id="last-name"
      v-model="lastName"
      required
      @keyup.enter="submitForm"
    />

    <label for="password">Password:</label>
    <input
      type="password"
      id="password"
      v-model="password"
      minlength="6"
      required
      placeholder="At least 6 characters"
      @keyup.enter="submitForm"
    />
    <label for="email">E-mail:</label>
<input
  type="email"
  id="email"
  v-model="email"
  placeholder="ex: myname@example.com"
  @keyup.enter="submitForm"
/>
<p v-if="email.length > 0 && !isValidEmail">Invalid email format</p>


    <div class="submit-button-container">
      <button type="submit" @click="submitForm">Submit</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      picked: '',
      message: '',
      firstName: '',
      lastName: '',
      password: '',
      email: '',
    };
  },
  computed: {
    isValidEmail() {
      const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return re.test(this.email);
    },
  },
  methods: {
    submitForm() {
      if (this.firstName && this.lastName && this.password.length >= 6 && this.isValidEmail) {
        alert('Form submitted successfully!');
      } else {
        alert('Please fill in all fields correctly.');
      }
    },
  },
};
</script>

<style scoped>
.feedback-form {
  background-color: rgb(250, 250, 250);
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  color: black; 
}

.feedback-form:hover {
  transform: scale(1.02);
}

.radio-group {
  display: flex;
  gap: 1rem;
}

input[type="text"],
input[type="password"],
input[type="email"],
textarea {
  width: 100%;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 10px 20px;
  background-color: rgb(38, 233, 233);
  color: rgb(15, 1, 1);
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
  color: gold;
}

.submit-button-container {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}
</style>





