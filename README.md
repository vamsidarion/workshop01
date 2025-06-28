Here is the **complete Markdown code** for your **"Getting Started with Ollama & Running Llama Models"** workshop — fully formatted, including all sections and the detailed **Windows WSL2 installation guide**.

You can copy and paste this into any `.md` file or Markdown editor (like VS Code, Obsidian, GitHub, etc.).

---

```markdown
# 🎓 Workshop: Getting Started with Ollama & Running Llama Models

## Presenters

### 👨‍💻 Muneer – Your Tech Guide  
I'm passionate about AI and open-source tools. I love breaking down complex topics into simple steps and helping others get hands-on with cutting-edge technology like **Ollama** and **Llama models**.

### 👩‍💻 Aishwarya – Making It Clear & Simple  
I focus on making technical concepts accessible to everyone. Whether it's explaining how models work or walking through installations, my goal is to make learning AI fun and easy — no jargon, just real results.

Together, we're here to guide you step by step through installing **Ollama**, running **Llama3**, and even setting up integrations — all in a way that’s beginner-friendly and engaging.

---

## 🧭 Table of Contents

1. [What is Ollama?](#1-what-is-ollama)  
2. [Why Use Ollama?](#2-why-use-ollama)  
3. [What You’ll Need Before Starting](#3-what-youll-need-before-starting)  
4. [How to Install Ollama](#4-how-to-install-ollama)  
5. [Running Llama Models](#5-running-llama-models)  
6. [Customizing Model Behavior](#6-customizing-model-behavior)  
7. [Understanding Responses](#7-understanding-responses)  
8. [Backing Up Outputs to Google Drive](#8-backing-up-outputs-to-google-drive)  
9. [Troubleshooting Common Issues](#9-troubleshooting-common-issues)  
10. [Want to Help Improve Ollama?](#10-want-to-help-improve-ollama)  
11. [License Info](#11-license-info)  
12. [Get in Touch](#12-get-in-touch)  
13. [Appendix: Ollama Installation Script (Advanced)](#13-appendix-ollama-installation-script-advanced)  

---

## 1. What is Ollama?

**Ollama** is an open-source tool that lets you run large language models like *Llama*, *Llama2*, and *Llama3* directly on your own computer — no internet required after downloading the model.

It’s fast, private, and perfect for developers, students, and AI enthusiasts who want to experiment with powerful models without relying on APIs or cloud services.

---

## 2. Why Use Ollama?

Here’s why Ollama makes life easier:

✅ Runs locally – No internet needed after download  
🔐 Private by default – Your data never leaves your device  
🚀 Fast and simple – Works great on Mac, Linux, and Windows (via WSL)  
🧠 Supports popular models – Like Llama3, one of the smartest open-source models out there  
🛠️ Easy to use – Just install and start chatting or coding  
🔄 Integrates well – With Python, Google Drive, and more  

Whether you want to chat, code, or build apps — Ollama can help.

---

## 3. What You’ll Need Before Starting

Before diving in, make sure you have:

- 💻 **Operating System**: macOS, Linux, or Windows (use WSL2)  
- 💾 **RAM**: At least 8GB (16GB+ recommended for smoother experience)  
- 🧰 **Basic Terminal Knowledge**  
- 🌐 **Internet Connection**: To download Ollama and models  

Once that’s ready, you’re all set!

---

## 4. How to Install Ollama

### For macOS:
Open Terminal and run:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

### For Linux:
Run these commands:

```bash
sudo apt update
sudo apt install -y ollama
```

### ✅ For Windows: Install via WSL2

> Follow these steps to install Ollama on **Windows using WSL2 (Windows Subsystem for Linux version 2)**.

#### Step 1: Enable WSL2

Open **PowerShell as Administrator** and run:

```powershell
# Enable WSL feature
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

# Enable Virtual Machine Platform
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

# Restart your PC when prompted
```

#### Step 2: Install a Linux Distro

Go to the Microsoft Store or use this link:  
👉 [https://aka.ms/wslstore](https://aka.ms/wslstore)

Install **Ubuntu** or any preferred distro.

Launch it and complete setup (create username/password).

#### Step 3: Update Packages

Inside WSL terminal:

```bash
sudo apt update && sudo apt upgrade -y
```

#### Step 4: Install Ollama

You can either:

**Option A:** Install from repo

```bash
sudo apt install -y ollama
```

**Option B:** Use official install script

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

#### Step 5: Verify Installation

```bash
ollama --version
```

You should see something like:

```
ollama version 0.xx.x
```

#### Step 6: Test with Llama3 (Optional)

```bash
ollama pull llama3
ollama run llama3
```

Now you're running **Llama3 on Windows** using **WSL2**!

---

## 5. Running Llama Models

Let’s try running **Llama3**, one of the most advanced open-source models.

### Step 1: Download the model
```bash
ollama pull llama3
```

### Step 2: Start using it
```bash
ollama run llama3
```

Now you’re inside a chat interface. Try asking fun questions like:

- “Tell me a joke.”
- “Explain quantum physics in simple terms.”

You’ll get real-time responses — powered by AI right on your laptop!

---

## 6. Customizing Model Behavior

Want the model to be more creative or stick to facts?

You can adjust settings like:

- `temperature`: Higher = more creative, Lower = more factual  
- `max_tokens`: Controls how long the response should be  
- `top_p`, `frequency_penalty`: More advanced controls  

### Example in Python:
```python
import ollama

response = ollama.generate(
    model="llama3",
    prompt="Write a poem about cats.",
    temperature=0.8
)

print(response["response"])
```

This gives you control over how the model thinks and responds.

---

## 7. Understanding Responses

When you ask a question, Ollama generates a response based on what it learned during training.

Examples of things it can do:

- 📝 Answer questions  
- 💻 Generate code  
- 📚 Summarize text  
- ✍️ Write poems or stories  
- 📊 Explain complex topics  

But remember — it’s not always perfect. Sometimes it might guess wrong or even make up answers. Always double-check important info.

---

## 8. Backing Up Outputs to Google Drive

Wouldn’t it be nice if every response was saved automatically?

### Here’s how to back up your results to Google Drive:

1. Install `rclone` – a tool for syncing files to the cloud  
2. Set it up with your Google Drive account  
3. Create a folder to store outputs:
   ```bash
   mkdir ~/ollama_output
   ```

4. Save a response and sync it:
   ```bash
   ollama generate llama3 "Your question" > ~/ollama_output/response.txt
   rclone copy ~/ollama_output remote_drive:/ollama_backup
   ```

Now all your AI-generated ideas are safely stored online.

---

## 9. Troubleshooting Common Issues

| **PROBLEM**               | **SOLUTION**                                  |
|---------------------------|-----------------------------------------------|
| Can't download the model  | Check your internet connection                |
| Out of memory error       | Try smaller models like `llama3:8b`           |
| Command not found         | Reinstall Ollama or add it to PATH            |
| GPU not working           | Make sure CUDA drivers are installed          |

Still stuck? Ask us during Q&A or check the [Ollama GitHub](https://github.com/ollama/ollama).

---

## 10. Want to Help Improve Ollama?

Ollama is **open source**, so anyone can contribute!

You can:

- 🔍 Report bugs  
- 💡 Suggest new features  
- 📚 Improve documentation  
- 💻 Submit code changes  

Check out their [GitHub page](https://github.com/ollama/ollama) and join the community!

---

## 11. License Info

Ollama uses the **MIT License**, which means you can freely use, modify, and share it — even for commercial purposes.

Each model (like Llama3) may have its own license, so always read the fine print before sharing or reusing them.

---

## 12. Get in Touch

Have questions or feedback? Feel free to reach out:

📧 **Email**:
- Muneer: muneer@example.com  
- Aishwarya: aishwarya@example.com  

🧑‍💻 **LinkedIn**: Search for our names  
👨‍💻 **GitHub**: @muneerai / @aishwaryaml  

🔗 **Ollama Resources**:
- Website: [ollama.com](https://ollama.com)
- GitHub: [github.com/ollama/ollama](https://github.com/ollama/ollama)

---

## 13. Appendix: Ollama Installation Script (Advanced)

Below is the full content of the official Ollama installation script used when you run:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

This script handles everything from detecting your OS and architecture to installing the correct binaries, setting up systemd services, and configuring GPU support where available.

(Include the raw script content here as a code block or reference.)

---

🎉 **Final Words**

We hope this workshop gave you a solid foundation to start exploring **Ollama** and **Llama models**.

Remember:

🧠 AI isn’t just for experts  
💡 It’s for everyone who wants to learn, create, and innovate  

So go ahead — play around with Ollama, ask it anything, and maybe even build something amazing.

Thank you for joining us today — happy experimenting! 🚀
```

---

✅ **Ready to save as `workshop-ollama.md` and open in any Markdown viewer or editor.**

If you'd like:
- A downloadable `.md` file
- Converted to PDF or HTML
- The actual Ollama install script included in the appendix

Let me know and I'll provide it right away!
