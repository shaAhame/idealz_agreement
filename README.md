# iDealz Influencer Agreement System

A production-ready Flask app that:
- Serves a branded agreement form at your public URL
- Captures influencer details + drawn e-signature
- Emails a signed copy to both the influencer AND iDealz team
- Saves every submission to a CSV log
- Shows all records at /agreements

---

## Files

```
idealz-agreement/
├── app.py                  ← Flask backend (all logic)
├── templates/
│   ├── index.html          ← Agreement form (influencer-facing)
│   └── agreements.html     ← Admin records view
├── requirements.txt
├── Procfile
├── railway.json
└── .gitignore
```

---

## Deploy to Railway (step by step)

### 1. Get a Gmail App Password
1. Go to myaccount.google.com → Security
2. Enable 2-Step Verification if not already on
3. Search "App Passwords" → Create one for "Mail"
4. Copy the 16-character password (format: xxxx xxxx xxxx xxxx)

### 2. Push to GitHub
```bash
cd idealz-agreement
git init
git add .
git commit -m "iDealz agreement system"
# Create a new repo on github.com, then:
git remote add origin https://github.com/YOUR_USERNAME/idealz-agreement.git
git push -u origin main
```

### 3. Deploy on Railway
1. Go to railway.app → New Project → Deploy from GitHub repo
2. Select your repo
3. Railway auto-detects Python and deploys

### 4. Set environment variables in Railway
Go to your project → Variables → Add these:

| Variable       | Value                          |
|----------------|-------------------------------|
| IDEALZ_EMAIL   | agreements@idealz.lk          |
| GMAIL_SENDER   | your.gmail@gmail.com          |
| GMAIL_PASSWORD | xxxx xxxx xxxx xxxx           |
| SHOWROOM       | Liberty Plaza                 |

### 5. Get your public URL
Railway gives you a URL like: https://idealz-agreement-production.up.railway.app

Share THIS link with influencers. Done.

---

## URLs

| URL             | What it does                              |
|-----------------|------------------------------------------|
| /               | The influencer agreement form             |
| /agreements     | Internal view of all submitted records   |

---

## Local testing

```bash
pip install flask gunicorn
export GMAIL_SENDER="your@gmail.com"
export GMAIL_PASSWORD="xxxx xxxx xxxx xxxx"
export IDEALZ_EMAIL="you@idealz.lk"
export SHOWROOM="Liberty Plaza"
python app.py
# Open http://localhost:5000
```

---

## Multiple showrooms

Deploy the same repo 3 times on Railway, each with a different SHOWROOM variable:
- Liberty Plaza deployment → share its URL with Liberty Plaza influencers
- Marino deployment → share its URL with Marino influencers
- Prime deployment → share its URL with Prime influencers

Each deployment is free on Railway's Hobby plan.
