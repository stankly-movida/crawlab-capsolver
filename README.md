# Crawlab + CapSolver: The Ultimate Captcha-Solving Solution 🚀

<p align="center">
  <img src="https://assets.capsolver.com/prod/posts/crawlab-capsolver/xEVIfFqkKUQe-a216c1c33dd1a9528142e4bf963575b4.png" alt="Crawlab CapSolver Integration" width="600">
</p>

<p align="center">
  <a href="https://github.com/crawlab-team/crawlab"><img src="https://img.shields.io/github/stars/crawlab-team/crawlab?style=flat-square&logo=github" alt="Crawlab Stars"></a>
  <a href="https://www.capsolver.com/?utm_source=csdn&utm_medium=blog&utm_campaign=crawlab-capsolver"><img src="https://img.shields.io/badge/CapSolver-AI--Powered-blue?style=flat-square&logo=google-cloud" alt="CapSolver"></a>
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-green.svg?style=flat-square" alt="License"></a>
</p>

---

## 📖 简介 / Introduction

在分布式爬虫管理中，**Crawlab** 提供了强大的节点调度能力，而 **CapSolver** 则通过 AI 技术解决了最棘手的验证码（Captcha）问题。本项目旨在展示如何将两者完美结合，构建一个能够自动化绕过 reCAPTCHA、Cloudflare Turnstile 等挑战的企业级爬虫系统。

> [!TIP]
> **Crawlab 用户专属福利**：使用优惠码 **Crawlab** 充值 CapSolver，立享 **6%** 额外额度！ [立即注册](https://dashboard.capsolver.com/dashboard/overview/?utm_source=github&utm_medium=blog&utm_campaign=crawlab-capsolver)

---

## ✨ 核心特性 / Features

- 🌐 **分布式管理**：基于 Crawlab 的主从架构，轻松扩展爬虫节点。
- 🤖 **AI 驱动识别**：集成 CapSolver，支持 reCAPTCHA (v2/v3)、Cloudflare、AWS WAF 等。
- 🛠️ **多框架支持**：提供 Selenium、Scrapy、Puppeteer 的完整集成示例。
- 📊 **可视化监控**：通过 Crawlab UI 实时查看爬取状态与验证码解决率。

---

## 🚀 快速开始 / Quick Start

### 1. 部署 Crawlab
```bash
git clone https://github.com/crawlab-team/crawlab.git
cd crawlab
docker-compose up -d
```
访问 `http://localhost:8080` (默认: admin/admin)。

### 2. 获取 CapSolver API Key
前往 [CapSolver Dashboard](https://dashboard.capsolver.com/dashboard/overview/?utm_source=github&utm_medium=blog&utm_campaign=crawlab-capsolver) 注册并获取您的 `API_KEY`。

### 3. 安装依赖
```bash
pip install selenium requests scrapy
# 或者 Node.js
npm install puppeteer
```

---

## 💻 代码示例 / Code Examples

### 🐍 Python + Selenium (reCAPTCHA v2)
```python
import os
from selenium import webdriver
from capsolver_helper import solve_recaptcha # 假设封装好的逻辑

# 设置环境变量
os.environ['CAPSOLVER_API_KEY'] = 'YOUR_API_KEY'

driver = webdriver.Chrome()
driver.get("https://example.com/captcha")

# 自动识别并注入
token = solve_recaptcha(driver.current_url, site_key)
driver.execute_script(f"document.getElementById('g-recaptcha-response').value = '{token}';")
```

### 🕷️ Scrapy Middleware
```python
class CapSolverMiddleware:
    def process_response(self, request, response, spider):
        if "captcha" in response.text:
            # 调用 CapSolver API 逻辑
            return self.handle_captcha(response)
        return response
```

---

## 🛠️ 最佳实践 / Best Practices

1. **检测后再触发**：仅在页面出现验证码时调用 API，优化成本。
2. **错误重试**：实现指数退避算法，应对网络波动。
3. **安全管理**：使用 Crawlab 的环境变量存储 API Key，避免泄露。

---

## 🤝 贡献 / Contributing

欢迎提交 Issue 或 Pull Request 来完善本项目！请参阅 [CONTRIBUTING.md](./CONTRIBUTING.md)。

---

## 📄 许可证 / License

本项目采用 [MIT License](./LICENSE) 开源。

---

<p align="center">
  Made with ❤️ by the Crawlab & CapSolver Community
</p>
