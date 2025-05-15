#  Debt Manager Assistant – AI-Powered n8n Workflow

This project is an AI-powered debt management assistant built using n8n, integrated with Google Sheets, Supabase (vector database), and OpenRouter/Gemini LLMs. It enables smart debt tracking, answering natural language queries, and sending reminders based on live debtor data.

---

## Features

- **Natural Language Interface**: Ask questions like "Who owes more than ₹10,000?" or "Who do I need to follow up with soon?"
- **Google Sheets Integration**: Stores debtor data (name, phone, amount, product, due date)
- **Supabase Vector Store**: Enables semantic search and contextual understanding
- **LLM Chat Model**: Powered by OpenRouter or Google Gemini
- **AI Agent Node**: Interprets and routes requests based on intent
- **Webhook Trigger**: Easily connect to front-end apps, forms, or chat interfaces

---

## Folder Structure

```bash
├── n8n-workflow.json     # Exported n8n workflow with all nodes
├── supabase.json         # Supabase vector store configuration and metadata
├── README.md             # This file
└── /docs
    └── system_prompt.md  # AI Agent system instructions
```

---

##  How It Works

1. **Webhook Trigger** receives a message or query.
2. **AI Agent** parses the intent.
   - If it's a data query → routes to Google Sheets or Supabase.
   - If it's a natural language question → sends to Supabase vector search.
3. **LLM Model** (OpenRouter or Gemini) handles chat responses.
4. **Vector Store Search** answers complex or vague queries.
5. **Webhook Response** returns data or answer to the user.

---

##  Required Fields in Google Sheet

Your Google Sheet should include the following headers:

- `Name`
- `Phone`
- `Product`
- `Amount`
- `Due Date`

---

##  Environment Variables (via n8n Credentials)

- Google Sheets OAuth2
- Supabase URL & API Key
- OpenRouter or Gemini API Key

---

## System Prompt (for AI Agent)

Stored in `/docs/system_prompt.md`. It defines the assistant’s behavior, tone, and logic routing rules (webhook vs Supabase).

---

## 🧪 Test Instructions

Use n8n’s “Test Workflow” feature to try:

- POST /webhook URL with sample body:
```json
{
  "text": "Who owes more than ₹5000?"
}
```

---

##  Notes

- In Production mode: Connect the last node (e.g., Respond to Webhook) back to SplitInBatches if looping is used.
- You may export embeddings from Sheets → Supabase using Gemini Embeddings node.

---

##  Deployment

You can deploy this on n8n Cloud, local n8n desktop, or Docker. For a public-facing bot, connect the Webhook to a chatbot UI like Telegram, WhatsApp, or a custom frontend.

---

##  Questions?

Open an issue or ping your assistant inside the bot — Alexis is always ready 😄

