# 🎤 VM Drop Audio Compliance Checker

Internal tool for voicemail drop compliance verification using OpenAI Whisper transcription and automated keyword detection.

## ⚡ Quick Start

1. **Visit the app**: https://ronakjindalghl.github.io/vm-drop-audio-checker/
2. **Upload an audio file** (MP3, MP4, WAV, M4A - max 25MB)  
3. **Wait for processing** (~1-2 minutes)
4. **Review results** for compliance violations

## 🔧 Features

- **Drag & drop file upload** with validation
- **OpenAI Whisper transcription** for high accuracy
- **Aggressive substring keyword matching** (catches all potential violations)
- **Real-time progress tracking** with visual indicators
- **Full transcription display** alongside violation details
- **Rate limiting** (10 transcriptions per hour)
- **Mobile responsive** design

## 🚦 Rate Limits

- **10 transcriptions per hour** (resets every hour)
- **25MB maximum file size**
- **15 minute processing timeout**

## 🛡️ Security & Privacy

- **Audio files are temporary** - deleted after processing
- **OpenAI API processing** - audio briefly sent to OpenAI for transcription
- **GitHub Actions logs** contain no sensitive data
- **API keys secured** in GitHub Secrets

## 📝 Keyword Detection

Uses **aggressive substring matching** to catch all potential violations:

- **"IRS"** matches in "first", "Kirstie", etc.
- **"Prize"** matches in "price", "surprised", etc.
- **"Package"** matches "packages", "packaging", etc.

**83 blocked keywords** including:
- Financial terms (loan, bank, cash)
- Scam indicators (IRS, social security)
- Prize/lottery terms (jackpot, sweepstakes)
- Company names (Amazon, PayPal)
- And more...

## 🚀 Setup Instructions

### 1. Repository Secrets

Add your OpenAI API key to GitHub repository secrets:
1. Go to repository Settings → Secrets and variables → Actions
2. Click "New repository secret"
3. Name: `OPENAI_API_KEY`
4. Value: Your OpenAI API key

### 2. Enable GitHub Pages

1. Go to repository Settings → Pages
2. Source: "Deploy from a branch"
3. Branch: `main`
4. Folder: `/ (root)`
5. Save

### 3. Enable GitHub Actions

GitHub Actions should be enabled by default. The workflow will trigger automatically when users upload files through the web interface.

## 💰 Cost Estimation

- **GitHub Actions**: Free (2000 minutes/month)
- **OpenAI Whisper**: ~$0.006/minute (~$3-5/month for typical usage)
- **GitHub Pages**: Free

**Total monthly cost**: ~$3-5

## 🐛 Troubleshooting

### Common Issues

1. **"Failed to start transcription"**
   - Check if OPENAI_API_KEY secret is set
   - Verify API key has Whisper access

2. **"Rate limit exceeded"**
   - Wait for next hour
   - Or manually reset `rate-limits.json`

3. **"Processing timeout"**
   - Try smaller audio files
   - Check GitHub Actions logs

4. **"File too large"**
   - Compress audio file
   - Max size: 25MB

### Checking Logs

1. Go to repository → Actions
2. Click on latest workflow run
3. Expand job steps to see detailed logs

---

**⚠️ Internal Use Only**: This application is designed for internal compliance checking. Do not share the URL publicly.
