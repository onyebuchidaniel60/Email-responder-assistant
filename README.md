# n8n Email Responder Assistant

This repository contains an **n8n workflow** that automates email management and intelligent response drafting using Google services and AI. It’s designed to help you automatically handle common email questions while alerting you about messages that require personal attention.

---

## 🚀 Features

- **Automated Gmail Trigger** — Detects new incoming messages.
- **AI-Powered Reply Generation** — Uses n8n Agent node connected to **Google Gemini** to understand the email and generate concise, contextually correct replies.
- **Google Docs Integration** — Drafts the email response in a connected Google Doc.
- **Smart Filtering** — Determines if the email is a common question; otherwise, flags it for manual review.
- **Google Sheets Logging** — Logs sender, email body, AI-generated reply, link to the message, and response status.
- **Slack Notifications** — Sends real-time updates about sent or pending replies.

---

## 🧩 Workflow Overview

### 1. **Gmail Trigger**
Monitors Gmail inbox for new “Important” emails.

### 2. **Get a Message**
Retrieves full email content and metadata, including sender and subject.

### 3. **Edit Fields**
Builds a Gmail link and prepares email data for the agent.

### 4. **AI Agent (LangChain)**
Processes the email through Google Gemini, generating a short and relevant reply (max two sentences).
- Uses a Google Docs tool to draft the reply.
- If not a “common question,” asks for manual handling.

### 5. **Conditional Branch**
Uses an **If node** to check if the AI’s output contains a Gmail link (meaning manual response required).

### 6. **Send Email / Slack Notification**
- If the email is handled automatically → Sends response via Gmail.
- Otherwise → Sends notification to Slack with link to the message.

### 7. **Google Sheets Update**
Appends the email record (sender, content, response, status, and link) into Google Sheets for tracking.

---

## 🧠 Tech Stack

- [n8n.io](https://n8n.io)
- Google Workspace APIs:
  - Gmail API
  - Google Docs API
  - Google Sheets API
- Slack API
- LangChain / Google Gemini (PaLM API)

---

## ⚙️ Setup Instructions

1. **Import the workflow**
   - Download the `.json` file from this repository.
   - Open your n8n editor → click **Import Workflow** → upload the file.

2. **Connect Credentials**
   - Gmail OAuth2  
   - Google Docs OAuth2  
   - Google Sheets OAuth2  
   - Slack OAuth2  
   - Google Gemini (PaLM) API key

3. **Update Resource IDs**
   - Replace Google Doc and Google Sheet IDs with your own.
   - Update Slack user/channel references.

4. **Activate the workflow**
   - Click execute the workflow to get workflow started

---

## 🪄 Example Use Case

When a client emails you asking a common question like:
> “Can you share your availability for next week?”

The workflow will:
- Detect the new email.
- Pass it through the AI agent.
- Draft a polite reply using information from the Google Doc.
- Send the reply automatically if appropriate.
- Log the interaction and notify you on Slack.

If it’s a more complex or personal message, it’ll skip sending and notify you to handle it manually.

---

## 🧰 Repository Contents

| File | Description |
|------|--------------|
| `email responder assistant.json` | n8n workflow file |

---

## 🧑‍💻 Author
Built by **Onyebuchi Nnamani** — automating intelligent email operations with n8n & AI.

---

## 📄 License
MIT License. Feel free to modify and adapt for your own workflows.
