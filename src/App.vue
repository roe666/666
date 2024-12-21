<template>
  <div class="app">
    <!-- 导航栏 -->
    <nav class="navbar">
      <div class="nav-links">
        <a v-for="item in navItems" 
           :key="item.id" 
           :href="item.href" 
           @click.prevent="scrollToSection(item.href)">
          {{ item.text }}
        </a>
      </div>
    </nav>

    <!-- 个人展示区 -->
    <section id="home" class="profile-section">
      <div class="profile-container">
        <img :src="profileImage" alt="个人照片" class="profile-image">
        <h1>{{ name }}</h1>
        <p class="tagline">{{ tagline }}</p>
        <p class="bio">{{ bio }}</p>
      </div>
    </section>

    <!-- 社交媒体区域 -->
    <section id="social" class="social-section">
      <div class="social-icons">
        <a v-for="social in socialLinks" 
           :key="social.id"
           :href="social.url" 
           class="social-icon"
           target="_blank">
          <i :class="social.icon"></i>
        </a>
      </div>
    </section>

    <!-- 页脚 -->
    <footer>
      <p>&copy; {{ new Date().getFullYear() }} {{ name }}. 保留所有权利.</p>
      <p class="contact">{{ contact }}</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      name: '你的名字',
      tagline: '你的个性标语',
      bio: '这里是你的个人简介...',
      contact: 'contact@example.com',
      profileImage: '/path/to/your/image.jpg',
      navItems: [
        { id: 1, text: '首页', href: '#home' },
        { id: 2, text: '关于我', href: '#about' },
        { id: 3, text: '作品集', href: '#portfolio' }
      ],
      socialLinks: [
        { id: 1, icon: 'fab fa-weibo', url: 'https://weibo.com/youraccount' },
        { id: 2, icon: 'fab fa-weixin', url: '#' },
        { id: 3, icon: 'fab fa-instagram', url: 'https://instagram.com/youraccount' }
      ]
    }
  },
  methods: {
    scrollToSection(href) {
      const element = document.querySelector(href)
      element?.scrollIntoView({ behavior: 'smooth' })
    }
  }
}
</script>

<style scoped>
:root {
  --primary-color: #ffffff;
  --accent-color: #4a90e2;
  --text-color: #333333;
  --background-color: #f5f5f5;
}

.app {
  font-family: 'PingFang SC', 'Microsoft YaHei', sans-serif;
  background: linear-gradient(to bottom, #f5f5f5, #ffffff);
  min-height: 100vh;
}

.navbar {
  position: fixed;
  top: 0;
  width: 100%;
  background-color: rgba(255, 255, 255, 0.95);
  padding: 1rem 0;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  z-index: 1000;
}

.nav-links {
  display: flex;
  justify-content: center;
  gap: 2rem;
}

.nav-links a {
  color: var(--text-color);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s;
}

.nav-links a:hover {
  color: var(--accent-color);
}

.profile-section {
  padding: 8rem 2rem 4rem;
  text-align: center;
}

.profile-image {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  object-fit: cover;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  transition: transform 0.3s;
}

.profile-image:hover {
  transform: scale(1.05);
}

.tagline {
  color: var(--accent-color);
  font-size: 1.2rem;
  margin: 1rem 0;
}

.social-section {
  padding: 2rem;
}

.social-icons {
  display: flex;
  justify-content: center;
  gap: 2rem;
}

.social-icon {
  color: var(--text-color);
  font-size: 1.5rem;
  transition: all 0.3s;
}

.social-icon:hover {
  color: var(--accent-color);
  transform: translateY(-3px);
}

footer {
  text-align: center;
  padding: 2rem;
  background-color: var(--primary-color);
  margin-top: 2rem;
  box-shadow: 0 -2px 4px rgba(0,0,0,0.1);
}

@media (max-width: 768px) {
  .nav-links {
    gap: 1rem;
  }
  
  .profile-image {
    width: 150px;
    height: 150px;
  }
}
</style> 