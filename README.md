🗞️ AI Daily Newsletter Bot (n8n) – Built by Suyash ❤️
This project is a fully automated AI-powered newsletter generator using n8n, designed to deliver daily world news summaries in HTML email (via Gmail) and Discord (Markdown).
It integrates BBC RSS Feeds, NewsAPI, and Google Gemini for fact-checked summaries, with built-in normalization and error handling.

📌 Features
⏰ Daily Scheduled Trigger (8 AM IST)

📰 Combines trusted sources:

BBC RSS Feeds

NewsAPI (customizable topics)

🧠 AI-generated summaries via Google Gemini

📤 Delivers to Gmail (HTML) and Discord (Markdown)

🧹 Automatically:

Sorts by freshness

Normalizes & cleans text

Limits to top 20 headlines

❗ (Optional) Error notifications via Discord

🔁 Workflow Overview
Schedule Trigger (Daily 8 AM)
   ├── RSS Read (BBC News)
   └── HTTP Request (NewsAPI) 
        ↓
    Split Out (articles array from NewsAPI)
        ↓
    Merge (append BBC + NewsAPI)
        ↓
    Sort (by pubDate / publishedAt descending)
        ↓
    Normalize (lowercase formatting)
        ↓
    Limit (top 20 items)
        ↓
    Summarize (title + snippet)
        ↓
    AI Agent (Google Gemini)
        ├── Gmail Tool (HTML email)
        └── Discord Tool (Markdown)
⚙️ Setup Guide
1. 🔧 Requirements
n8n (self-hosted or desktop)

NewsAPI Key → newsapi.org

Google Gemini API Key

Gmail credentials (OAuth2)

Discord webhook URL

2. 🔑 Credentials & API Safety
✅ No API keys are hardcoded in the workflow file.

🔐 NewsAPI:

HTTP Request Node → Generic Auth → Header Auth (apiKey)

🔐 Google Gemini:

Language Model Node with API key in credentials

📧 Gmail:

Gmail Tool Node with OAuth2 credentials

💬 Discord:

Discord Tool Node with webhook credentials

🛡️ Keep your .json file private to protect keys

3. 📬 AI Agent Prompt (Built-in)
Generates two outputs every run:

✅ Gmail Output (HTML)
Valid HTML email with emojis, greeting, and exactly 12–15 factual headlines from the last 24 hours

✅ Discord Output (Markdown)
Clean, Discord-friendly markdown with bold headlines, emojis, and one-line summaries

🧪 Output Quality
✅ Real-time freshness (sorted by latest date)

✅ Lowercase normalization for clean comparisons

✅ Top 20 filtered before summarization

✅ Consistent AI formatting for Gmail & Discord

📂 Project Structure
bash
Copy
Edit
AI-Newsletter/
├── README.md                # This file
├── AI-Newsletter.json       # Main newsletter workflow
├── assets/                  # Screenshots and visuals
│   ├── workflow.png
│   ├── gmail-example.png
│   └── discord-example.png
<h2>📰 Today’s Top Headlines</h2>
<p>Hello! Here's a quick look at today’s most important global stories:</p>

<p>🌍 <b>UK Parliament Passes AI Regulation Bill</b>: New law mandates AI transparency for major tech firms.</p>
<p>🛰️ <b>ISRO Successfully Launches Gaganyaan Module</b>: Prepares for crewed space mission in 2026.</p>

<p>Thanks for reading!<br>Built by Suyash ❤️</p>
📰 **Today’s Top Headlines** – AI Bill, ISRO Launch, Global Markets

🌍 **UK Passes AI Regulation Bill**: New transparency rules for AI giants.

🛰️ **ISRO Launches Gaganyaan Module**: Major milestone toward crewed space mission.

---
*Built by Suyash ❤️*
🚨 Optional Error Handling
You can add nodes that:

❌ Send Discord alerts if NewsAPI fails (quota, invalid key, timeout)

❌ Send Discord alerts if Gemini AI Agent fails

💡 Future Upgrades
🔄 Slack or Telegram delivery

🌍 Multi-language summaries

📊 Engagement analytics

📰 Topic-based newsletters

👨‍💻 Author
Built by Suyash ❤
www.linkedin.com/in/suyashsinghgusain
https://github.com/suyash-codes
