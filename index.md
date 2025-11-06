<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yu - 个人网站</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
            color: #333;
            overflow-x: hidden;
            background: #0f0f0f;
        }

        /* 动态渐变背景 */
        .gradient-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
            z-index: -1;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* 导航栏 */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 1.5rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            z-index: 100;
            transition: all 0.3s;
        }

        nav.scrolled {
            background: rgba(255, 255, 255, 0.95);
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            color: white;
            transition: color 0.3s;
        }

        nav.scrolled .logo {
            color: #667eea;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: all 0.3s;
            position: relative;
        }

        nav.scrolled .nav-links a {
            color: #333;
        }

        .nav-links a:hover {
            transform: translateY(-2px);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: white;
            transition: width 0.3s;
        }

        nav.scrolled .nav-links a::after {
            background: #667eea;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        /* Hero 区域 */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: white;
            padding: 2rem;
        }

        .hero h1 {
            font-size: 4rem;
            margin-bottom: 1rem;
            animation: fadeInUp 1s ease;
        }

        .hero .subtitle {
            font-size: 1.5rem;
            margin-bottom: 2rem;
            opacity: 0.9;
            animation: fadeInUp 1s ease 0.2s both;
        }

        .hero .description {
            font-size: 1.1rem;
            max-width: 600px;
            margin-bottom: 3rem;
            line-height: 1.8;
            opacity: 0.85;
            animation: fadeInUp 1s ease 0.4s both;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .cta-button {
            display: inline-block;
            padding: 1rem 2.5rem;
            background: white;
            color: #667eea;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            transition: all 0.3s;
            animation: fadeInUp 1s ease 0.6s both;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .cta-button:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.3);
        }

        /* 内容区域 */
        section {
            min-height: 100vh;
            padding: 6rem 2rem;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        .section-white {
            background: white;
        }

        .section-light {
            background: #f8f9fa;
        }

        .container {
            max-width: 1200px;
            width: 100%;
        }

        h2 {
            font-size: 3rem;
            margin-bottom: 3rem;
            text-align: center;
            color: #667eea;
            position: relative;
        }

        h2::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: linear-gradient(90deg, #667eea, #764ba2);
            border-radius: 2px;
        }

        /* 项目卡片 */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .project-card {
            background: white;
            border-radius: 20px;
            padding: 2.5rem;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
            transition: all 0.3s;
            border: 2px solid transparent;
        }

        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 60px rgba(102, 126, 234, 0.3);
            border-color: #667eea;
        }

        .project-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: #667eea;
        }

        .project-card p {
            color: #666;
            line-height: 1.6;
        }

        /* 技能标签 */
        .skills-container {
            display: flex;
            flex-wrap: wrap;
            gap: 1.5rem;
            justify-content: center;
            max-width: 800px;
            margin: 0 auto;
        }

        .skill-tag {
            padding: 1rem 2rem;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            border-radius: 50px;
            font-weight: 600;
            box-shadow: 0 5px 20px rgba(102, 126, 234, 0.3);
            transition: all 0.3s;
            cursor: default;
        }

        .skill-tag:hover {
            transform: scale(1.1) rotate(2deg);
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.5);
        }

        /* 联系方式 */
        .contact-info {
            text-align: center;
            background: white;
            padding: 3rem;
            border-radius: 20px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
            max-width: 600px;
            margin: 0 auto;
        }

        .contact-info a {
            color: #667eea;
            text-decoration: none;
            font-size: 1.2rem;
            display: block;
            margin: 1rem 0;
            transition: all 0.3s;
        }

        .contact-info a:hover {
            transform: translateX(10px);
        }

        /* 页脚 */
        footer {
            background: #1a1a1a;
            color: white;
            text-align: center;
            padding: 2rem;
        }

        /* 响应式 */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5rem;
            }

            .hero .subtitle {
                font-size: 1.2rem;
            }

            h2 {
                font-size: 2rem;
            }

            .nav-links {
                gap: 1rem;
            }

            nav {
                padding: 1rem;
            }

            .projects-grid {
                grid-template-columns: 1fr;
            }
        }

        /* 滚动提示 */
        .scroll-indicator {
            position: absolute;
            bottom: 2rem;
            left: 50%;
            transform: translateX(-50%);
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateX(-50%) translateY(0);
            }
            40% {
                transform: translateX(-50%) translateY(-20px);
            }
            60% {
                transform: translateX(-50%) translateY(-10px);
            }
        }

        .scroll-indicator svg {
            width: 30px;
            height: 30px;
            fill: white;
        }
    </style>
</head>
<body>
    <!-- 动态背景 -->
    <div class="gradient-bg"></div>

    <!-- 导航栏 -->
    <nav id="navbar">
        <div class="logo">Yu</div>
        <ul class="nav-links">
            <li><a href="#home">首页</a></li>
            <li><a href="#about">关于</a></li>
            <li><a href="#projects">项目</a></li>
            <li><a href="#skills">技能</a></li>
            <li><a href="#contact">联系</a></li>
        </ul>
    </nav>

    <!-- Hero 区域 -->
    <section class="hero" id="home">
        <h1>欢迎来到我的世界</h1>
        <p class="subtitle">探索 | 创造 | 成长</p>
        <p class="description">
            你好！我是 Yu，一个充满热情的探索者。我热爱学习新技术，享受网球带来的活力，
            目前正在为硕士申请而努力奋斗。
        </p>
        <a href="#about" class="cta-button">了解更多</a>
        
        <div class="scroll-indicator">
            <svg viewBox="0 0 24 24">
                <path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z"/>
            </svg>
        </div>
    </section>

    <!-- 关于我 -->
    <section class="section-white" id="about">
        <div class="container">
            <h2>关于我</h2>
            <div class="contact-info">
                <p style="font-size: 1.3rem; color: #333; line-height: 2; margin-bottom: 2rem;">
                    我是一个充满好奇心的学习者，对技术和运动都充满热情。
                    编程让我能够创造，网球让我保持活力，而不断的学习让我持续进步。
                </p>
                <p style="color: #666;">💡 座右铭：永远保持学习的热情</p>
            </div>
        </div>
    </section>

    <!-- 我的项目 -->
    <section class="section-light" id="projects">
        <div class="container">
            <h2>我的项目</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <h3>🎓 硕士申请</h3>
                    <p>
                        正在准备研究生申请材料，包括个人陈述、推荐信和研究计划。
                        目标是进入理想的学府，继续深造学习。
                    </p>
                </div>
                <div class="project-card">
                    <h3>🎾 网球</h3>
                    <p>
                        热爱网球运动，定期训练和参加比赛。
                        网球不仅锻炼了我的身体，更培养了我的专注力和决心。
                    </p>
                </div>
                <div class="project-card">
                    <h3>💻 个人网站</h3>
                    <p>
                        搭建了这个个人网站，用于展示我的项目和技能。
                        不断学习前端技术，让网站变得更加美观和实用。
                    </p>
                </div>
            </div>
        </div>
    </section>

    <!-- 技能 -->
    <section class="section-white" id="skills">
        <div class="container">
            <h2>技能树</h2>
            <div class="skills-container">
                <div class="skill-tag">HTML/CSS</div>
                <div class="skill-tag">JavaScript</div>
                <div class="skill-tag">Python</div>
                <div class="skill-tag">问题解决</div>
                <div class="skill-tag">团队协作</div>
                <div class="skill-tag">持续学习</div>
            </div>
        </div>
    </section>

    <!-- 联系我 -->
    <section class="section-light" id="contact">
        <div class="container">
            <h2>联系我</h2>
            <div class="contact-info">
                <h3 style="margin-bottom: 2rem; color: #667eea;">让我们保持联系！</h3>
                <a href="mailto:ydq001027@gmail.com">📧 ydq001027@gmail.com</a>
                <a href="https://github.com/yu1dq" target="_blank">🔗 GitHub: yu1dq</a>
            </div>
        </div>
    </section>

    <!-- 页脚 -->
    <footer>
        <p>&copy; 2024 Yu. Made with ❤️</p>
    </footer>

    <script>
        // 导航栏滚动效果
        const navbar = document.getElementById('navbar');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // 平滑滚动
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
    </script>
</body>
</html>
