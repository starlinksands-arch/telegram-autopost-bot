# Telegram Auto-Post Bot 🤖

A bot that automatically posts your message + photo to **ANY group** where it's added as admin. No setup needed per group - just add the bot and it starts posting!

## What It Does

✅ Auto-posts message + photo to every group it's added to  
✅ Starts automatically when added as admin  
✅ Posts at regular intervals (default: every 60 seconds)  
✅ Works in unlimited groups simultaneously  
✅ Easy to update message and photo anytime  

---

## Quick Setup (5 Minutes)

### Step 1: Create Bot with BotFather

1. Open Telegram
2. Search for **@BotFather** and tap Start
3. Send `/newbot`
4. Choose bot name (e.g., "My Auto Post Bot")
5. Choose username ending in "bot" (e.g., "myautopost_bot")
6. **Copy your token** - looks like: `123456:ABCDEfghIjklMn...`

### Step 2: Setup Your Computer

1. **Install Python 3.8+** from [python.org](https://www.python.org)

2. **Download this project** or clone it:
   ```bash
   git clone https://github.com/starlinksands-arch/telegram-autopost-bot.git
   cd telegram-autopost-bot
   ```

3. **Install Python packages:**
   ```bash
   pip install -r requirements.txt
   ```

### Step 3: Configure the Bot

1. **Create `.env` file** in the project folder with:
   ```
   BOT_TOKEN=123456:ABCDEfghIjklMn...
   POST_INTERVAL=60
   ```
   
   Replace `123456:ABCDEfghIjklMn...` with your actual token from BotFather

2. **Add your message** - Edit `post_message.txt`:
   ```
   🚀 Check this out!
   
   Your message here
   ```

3. **Add your photo** - Place image file in `images/` folder:
   ```
   images/post.jpg
   ```
   Edit `photo_path.txt` to point to it:
   ```
   ./images/post.jpg
   ```

### Step 4: Run the Bot

```bash
python bot.py
```

You should see:
```
✓ Scheduler started - Posts every 60 seconds
Bot is running. Press Ctrl+C to stop...
```

### Step 5: Add to Your Groups

1. Open your Telegram group
2. Search for your bot username (e.g., @myautopost_bot)
3. Click to add to group
4. Make it **ADMIN** (long-press bot → "Make Administrator")
5. **Bot automatically starts posting!** ✓

That's it! No commands needed. It posts automatically.

---

## File Structure

```
telegram-autopost-bot/
├── bot.py                 ← Main bot script
├── .env                   ← Your config (BOT_TOKEN, interval)
├── post_message.txt       ← What message to send
├── photo_path.txt         ← Path to your photo
├── images/                ← Folder with your photos
│   └── post.jpg          ← Your photo file
├── requirements.txt       ← Python packages needed
└── README.md             ← This file
```

---

## How to Update Posts

### Change the Message

Edit `post_message.txt`:
```
New message here!
With emojis 🎉
And formatting
```

### Change the Photo

1. Place new photo in `images/` folder
2. Edit `photo_path.txt`:
   ```
   ./images/new_photo.jpg
   ```

**Changes take effect immediately** - bot reloads content each time it posts!

---

## Formatting

You can use HTML formatting in `post_message.txt`:

```
<b>Bold text</b>
<i>Italic text</i>
<code>Code block</code>
<a href="https://google.com">Click here</a>
```

---

## Settings

In `.env` file:

```
BOT_TOKEN=your_token_here        # Your bot token from BotFather
POST_INTERVAL=60                 # Seconds between posts (60=1min)
```

### Intervals:
- `30` = every 30 seconds
- `60` = every 1 minute  
- `300` = every 5 minutes
- `3600` = every 1 hour

---

## Commands (Optional)

If you send these in a group:

- `/start` - Force start posting in that group
- `/stop` - Stop posting in that group

But bot starts automatically when added, so you don't need these!

---

## Troubleshooting

### Bot doesn't post
- ❌ Check `BOT_TOKEN` is correct in `.env`
- ❌ Make sure bot is **ADMIN** in the group
- ❌ Check `post_message.txt` is not empty
- ❌ Check internet connection

### Photo doesn't show
- ❌ Photo file path is wrong in `photo_path.txt`
- ❌ Photo file doesn't exist - check `images/` folder
- ❌ Photo format not supported (use JPG or PNG)

### Terminal shows error
- ❌ Python 3.8+ installed? (`python --version`)
- ❌ Packages installed? (`pip install -r requirements.txt`)
- ❌ `.env` file exists and has `BOT_TOKEN`?

---

## Keep Bot Running 24/7

### Option 1: On Linux/VPS (Recommended)

Use `screen` or `tmux`:
```bash
screen -S telegrambot
python bot.py
# Press Ctrl+A then D to detach
# Later: screen -r telegrambot to reattach
```

### Option 2: Docker

1. Create `Dockerfile`:
```dockerfile
FROM python:3.9
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python", "bot.py"]
```

2. Build and run:
```bash
docker build -t telegram-bot .
docker run -d --env-file .env --name telegram-bot telegram-bot
```

### Option 3: Windows (Task Scheduler)

Create a batch file and schedule it to run at startup.

---

## Support

Having issues? Check:
1. Bot token is correct (from BotFather)
2. Bot is admin in the group
3. Python 3.8+ installed
4. Packages installed: `pip install -r requirements.txt`

---

**Enjoy your auto-posting bot! 🚀**
