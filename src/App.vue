<!-- App.vue -->
<template>
  <div id="app">
    <h1>Welcome Guys!</h1>
    
    <!-- 1. Click Counter -->
    <div class="task-section">
      <h2>1. Click Counter</h2>
      <p>Count: {{ count }}</p>
      <button @click="incrementCount" class="btn">Increment</button>
    </div>

    <!-- 2. Box Color Changer -->
    <div class="task-section">
      <h2>2. Box Color Changer</h2>
      <div :style="{ width: '100px', height: '100px', backgroundColor: boxColor }" class="color-box"></div>
      <button @click="changeBoxColor" class="btn">Change Color</button>
    </div>

    <!-- 3. Image Carousel -->
    <div class="task-section">
      <h2>3. Image Carousel</h2>
      <div class="carousel">
        <img :src="currentImage" alt="Carousel Image" class="carousel-image">
        <div class="carousel-controls">
          <button @click="previousImage" class="btn">Previous</button>
          <button @click="nextImage" class="btn">Next</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      boxColor: 'red',
      images: [
        'https://i.pinimg.com/564x/68/d3/de/68d3de35a9a827091c772eca685f539d.jpg',
        'https://i.pinimg.com/564x/a0/7f/c3/a07fc3aca5685e57dead1c79dae3d3c5.jpg',
        'https://i.pinimg.com/736x/bb/a6/75/bba675a1a145a6762837167d06170dd5.jpg'
      ],
      currentImageIndex: 0
    }
  },
  computed: {
    currentImage() {
      return this.images[this.currentImageIndex]
    }
  },
  methods: {
    incrementCount() {
      this.count++
    },
    changeBoxColor() {
      const colors = ['red', 'blue', 'green', 'yellow', 'purple']
      const randomColor = colors[Math.floor(Math.random() * colors.length)]
      this.boxColor = randomColor
    },
    nextImage() {
      this.currentImageIndex = (this.currentImageIndex + 1) % this.images.length
    },
    previousImage() {
      this.currentImageIndex = (this.currentImageIndex - 1 + this.images.length) % this.images.length
    }
  }
}
</script>

<style scoped>
#app {
  font-family: Arial, sans-serif;
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f0f0f0;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
  color: #333;
  text-align: center;
}

h2 {
  color: #666;
}

.task-section {
  background-color: white;
  padding: 20px;
  margin-bottom: 20px;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.btn {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.btn:hover {
  background-color: #45a049;
}

.color-box {
  margin: 10px 0;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.carousel {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.carousel-image {
  width: 300px;
  height: 200px;
  object-fit: cover;
  border-radius: 5px;
  margin-bottom: 10px;
}

.carousel-controls {
  display: flex;
  gap: 10px;
}
</style>