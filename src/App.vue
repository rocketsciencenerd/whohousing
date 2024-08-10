<script setup lang="ts">
import { ref } from 'vue';

// Importing Google Font
const fontLink = document.createElement('link');
fontLink.rel = 'stylesheet';
fontLink.href = 'https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap';
document.head.appendChild(fontLink);

const message = ref('');
const email = ref('');

const sendEmail = () => {
  const subject = encodeURIComponent("Inquiry from Website");
  const body = encodeURIComponent(`Message from: ${email.value}\n\n${message.value}`);
  const mailtoLink = `mailto:whohousing@gmail.com?subject=${subject}&body=${body}`;
  window.location.href = mailtoLink;
};
</script>

<template>
  <div class="main-content">
    <header>
      <img alt="34815TH" class="picture" src="@/assets/34815TH.png"/>
      <div class="text-container">
        <h1>WhoHousing LLC</h1>
        <p>Residential Rentals in Minneapolis, MN</p>
        <!--<RouterLink to="/about">About Us</RouterLink>-->
      </div>
    </header>

    <footer class="contact-section">
      <section class="contact-form">
        <h2>Contact Us</h2>
        <form @submit.prevent="sendEmail">
          <div class="form-group">
            <label for="email">Your Email:</label>
            <input type="email" id="email" v-model="email" required>
          </div>
          <div class="form-group">
            <label for="message">Your Message:</label>
            <textarea id="message" v-model="message" required></textarea>
          </div>
          <button type="submit">Send</button>
        </form>
      </section>
    </footer>
  </div>
</template>

<style scoped>
/* Global font styling */
* {
  font-family: 'Roboto', sans-serif;
}

/* Main container styling to structure the page content */
.main-content {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  align-items: center; /* Center content horizontally */
}

/* Header for the image and text */
header {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center; /* Center content horizontally */
  justify-content: flex-start;
  text-align: center;
  width: 100%;
}

.picture {
  width: 100%;
  height: 75vh;
  object-fit: cover;
}

.text-container {
  background-color: white;
  color: black;
  width: 100%;
  padding: 2rem;
  text-align: center;
  max-width: 800px; /* Center text and limit width */
}

/* Footer for the contact form */
footer.contact-section {
  background-color: white;
  color: black;
  text-align: center;
  width: 100%;
}

footer h2 {
  font-size: 2rem;
  margin-bottom: 1.5rem;
}

.contact-form {
  max-width: 600px;
  margin: 0 auto;
  background-color: white;
  text-align: left;
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: 500;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: #f9f9f9;
  color: black;
}

.form-group textarea {
  resize: vertical;
}

button {
  background-color: black;
  color: white;
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
  font-weight: 500;
}

button:hover {
  background-color: #333;
}
</style>
