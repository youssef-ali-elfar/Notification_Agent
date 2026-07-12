# AI Career Chatbot 💬

An AI-powered chatbot that represents you (based on your CV) and answers questions from visitors about your career, background, skills, and experience — built with **Streamlit** and **OpenRouter**, with **Pushover** notifications for lead capture.

## Features

- Chats as you, using your CV as context
- Automatically records visitor emails when they show interest in getting in touch
- Logs any question it couldn't answer, so you can improve the bot later
- Sends you a push notification (via Pushover) whenever a lead or unanswered question is recorded
- Deployable for free and shareable with anyone via a public link

## How It Works

1. The app loads your CV (PDF) and injects its text into the system prompt.
2. A visitor chats with the bot through a Streamlit chat interface.
3. The LLM (via OpenRouter) responds in character as you, using two tools when needed:
   - `record_user_details` — saves a visitor's email/name/notes when they want to connect
   - `record_unknown_question` — logs any question the bot couldn't confidently answer
4. Both tools trigger a push notification to your phone via Pushover.

## Requirements

- Python 3.9+
- An [OpenRouter](https://openrouter.ai/) API key
- A [Pushover](https://pushover.net/) account (user key + app token) for notifications

## Installation

```bash
# Clone the repository
git clone https://github.com/USERNAME/REPO_NAME.git
cd REPO_NAME

# Create and activate a virtual environment
python -m venv venv
venv\Scripts\Activate.ps1     # On Windows (PowerShell)
# source venv/bin/activate    # On macOS/Linux

# Install dependencies
pip install -r requirements.txt
```

## Setup

1. Place your CV as a PDF in the project folder, named exactly:
   ```
   Youssef_CV_Final.pdf
   ```
   (or update the filename in `main.py` to match your own file)

2. Create a `.env` file in the project root (see `.env.example`):

```
OPEN_ROUTER_KEY=your_openrouter_api_key_here
PUSHOVER_USER=your_pushover_user_key
PUSHOVER_TOKEN=your_pushover_app_token
```

> ⚠️ **Never commit your `.env` file.** It's already excluded via `.gitignore`.

## Usage

Run locally with:

```bash
streamlit run main.py
```

The app will open in your browser at `http://localhost:8501`.

## Deploying Publicly (Free)

You can deploy this app for free using **Streamlit Community Cloud**:

1. Push your project to GitHub (make sure `.env` is **not** included — only `.env.example`).
2. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
3. Select your repository and set `main.py` as the entry point.
4. In the app's **Settings → Secrets**, add your keys:
   ```toml
   OPEN_ROUTER_KEY = "your_key_here"
   PUSHOVER_USER = "your_pushover_user"
   PUSHOVER_TOKEN = "your_pushover_token"
   ```
5. Deploy — you'll get a public link like `https://your-app-name.streamlit.app` that anyone can use.

## Project Structure

```
.
├── main.py                    # Main Streamlit application
├── Youssef_CV_Final.pdf       # Your CV (used as chatbot context)
├── .env.example                # Example environment variables
├── .gitignore
├── requirements.txt
└── README.md
```

## Tech Stack

- [Streamlit](https://streamlit.io/) — chat UI
- [OpenRouter](https://openrouter.ai/) — LLM API access (OpenAI-compatible)
- [pypdf](https://pypi.org/project/pypdf/) — PDF text extraction
- [Pushover](https://pushover.net/) — push notifications

## License

This project is open source and available under the [MIT License](LICENSE).
