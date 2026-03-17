# CompositeLab — ML Property Predictor

Composite material property prediction using GPR + GBM.  
**Carbon Fiber (20%) + Boron Nitride + Aluminium Oxide**

---
 
## Deploy on Railway (5 minutes)

### Step 1 — Push to GitHub
```bash
git init
git add .
git commit -m "CompositeLab"
git remote add origin https://github.com/YOUR_USERNAME/compositelab.git
git push -u origin main
```

### Step 2 — Create Railway project
1. Go to [railway.app](https://railway.app)
2. Sign up / log in (free)
3. Click **New Project → Deploy from GitHub repo**
4. Select your repo
5. Railway auto-detects Python and reads `railway.toml` ✅

### Step 3 — Add environment variable
In your Railway project dashboard:
1. Click your service → **Variables** tab
2. Add:
   - Key: `GROQ_API_KEY`
   - Value: `gsk_your_key_here`
3. Railway auto-redeploys ✅

### Step 4 — Get your URL
In the Railway dashboard → **Settings** tab → **Domains**  
Click **Generate Domain** → your app is live at:
```
https://compositelab-production-xxxx.up.railway.app
```

---

## Local Development
```bash
pip install -r requirements.txt
cp .env.example .env   # add your GROQ_API_KEY
python app.py
# visit http://localhost:5000
```

---

## Stack
- **Backend**: Flask + scikit-learn (GPR + GBM)
- **Frontend**: Vanilla JS + Chart.js
- **AI Chat**: Groq Llama 3.3 70B
- **Deploy**: Railway

## Notes
- Models train per session (Railway has ephemeral storage on free tier)
- Users upload Excel files each time to retrain
- `--timeout 120` in gunicorn handles the ~20s training time
- Free tier: 500 hours/month (enough for demos)
