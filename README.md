# 🤖 Sukisu Store Bot — Complete Setup Guide

Ek powerful Telegram bot — game keys, configs, aur digital products bechne ke liye.
FamPay auto payment, manual deposit, reseller system, aur bahut kuch.

---

## 📋 FEATURES

### 🛒 Customer Features
- ✅ Multi-category products (Android Root / Android Non-Root / iPhone)
- ✅ Instant key delivery (API se auto-fetch)
- ✅ Balance system (FamPay + Manual Deposit)
- ✅ FamPay auto payment (5 min mein detect)
- ✅ Manual deposit with admin verification
- ✅ Lucky Spin (daily reward — 1 ghante valid)
- ✅ Referral system (5% bonus on first purchase)
- ✅ Order history with keys
- ✅ Reseller system (custom discounted prices)
- ✅ Support tickets
- ✅ FAQ system
- ✅ Review system with reminders
- ✅ Selling proof channel
- ✅ Tutorial video
- ✅ Product notifications (Notify Me)

### 🔧 Admin Features
- ✅ Full admin panel
- ✅ Dashboard (today / weekly / lifetime stats)
- ✅ Analytics (top products, user growth, revenue)
- ✅ Product management (add / edit / delete / maintenance)
- ✅ Plan management (duration + price)
- ✅ Reseller price management per plan
- ✅ Deposit approval / rejection
- ✅ Support ticket management
- ✅ FAQ manager
- ✅ Review viewer
- ✅ Broadcast (text + photo + video + voice + audio + document)
- ✅ Targeted broadcast (All / Verified / Inactive / Resellers / Has Balance)
- ✅ Backup / Restore database
- ✅ CSV export (Users / Transactions / Deposits / Orders)
- ✅ Admin activity logs
- ✅ Bot maintenance mode
- ✅ Multi-admin support

### 🔒 Technical Features
- ✅ Rotating logs (10MB x 5 backups)
- ✅ HTML escape safety
- ✅ SQLite backup API (WAL-safe)
- ✅ Retry cap for API orders (3 attempts, then auto-refund)
- ✅ Balance locking (double-spend safe)
- ✅ Rate limiting
- ✅ Auto backup on crash
- ✅ Production ready

---

## 📦 REQUIREMENTS

- Python 3.8+
- Telegram Bot Token
- FamPay API access (optional, for auto payments)
- API provider for key delivery

---

## 🔧 STEP 1: INSTALL

```bash
pip install pyTelegramBotAPI requests
```

---

## ⚙️ STEP 2: CONFIG — FILE MEIN KYA KYA CHANGE KARNA HAI

File kholo: `sukisu_store_bot.py`

Sabse upar `# ============ CONFIG ============` section milega.
**Neeche diye gaye 11 values ko dhoondho aur `""` (empty string) mein apna value daalo.**

---

### 🔴 CHANGE #1 — `BOT_TOKEN`

**File mein ye line dhoondho:**
```python
BOT_TOKEN = ""
```

**Yahan apna bot token daalo.**

**Kahan se milega:** Telegram pe [@BotFather](https://t.me/BotFather) → `/newbot` → token copy karo

**Example:**
```python
BOT_TOKEN = "1234567890:ABCdefGHIjklMNOpqrsTUVwxyz"
```

**Format:** `1234567890:ABCdefGHIjklMNOpqrsTUVwxyz`

---

### 🔴 CHANGE #2 — `ADMIN_USER_ID`

**File mein ye line dhoondho:**
```python
ADMIN_USER_ID = 0  # Apna Telegram user ID yaha daalo (@userinfobot se lo)
```

**Yahan apna Telegram user ID daalo (0 ki jagah).**

**Kahan se milega:** [@userinfobot](https://t.me/userinfobot) pe `/start` → ID milega

**Example:**
```python
ADMIN_USER_ID = 123456789  # Apna Telegram user ID yaha daalo (@userinfobot se lo)
```

⚠️ **Yeh ID hi main admin hogi.** Yeh admin ko remove nahi kar sakte.

---

### 🔴 CHANGE #3 — `SUCCESS_IMG`

**File mein ye line dhoondho:**
```python
SUCCESS_IMG = ""  # Success image ka file_id (@RawDataBot se lo)
```

**Yahan apni success image ka file_id daalo.**

**Kahan se milega:** [@RawDataBot](https://t.me/RawDataBot) pe apni image bhejo → `file_id` copy karo

**Example:**
```python
SUCCESS_IMG = "AgACAgUAAxkBAA..."  # Success image ka file_id (@RawDataBot se lo)
```

⚠️ **Empty chhoda toh text message aayega, image nahi.**

---

### 🔴 CHANGE #4 — `FAMPAY_UPI_ID`

**File mein ye line dhoondho:**
```python
FAMPAY_UPI_ID = ""  # Apna UPI ID yaha daalo (e.g. yourname@paytm)
```

**Yahan apna UPI ID daalo jisme payment aayega.**

**Example:**
```python
FAMPAY_UPI_ID = "yourname@paytm"  # Apna UPI ID yaha daalo (e.g. yourname@paytm)
```

**Format:** `yourname@paytm` ya `9876543210@ybl`

---

### 🔴 CHANGE #5 — `DB_PATH`

**File mein ye line dhoondho:**
```python
DB_PATH = "sukisu.db"  # Database file ka naam (change kar sakte ho)
```

**Change karne ki zaroorat NAHI.** Default `sukisu.db` rakh do.

**Agar change karna hai:**
```python
DB_PATH = "mybot.db"  # Database file ka naam (change kar sakte ho)
```

---

### 🔴 CHANGE #6 — `API_URL`

**File mein ye line dhoondho:**
```python
API_URL = ""  # Apna API endpoint yaha daalo
```

**Yahan apne API provider ka endpoint daalo.**

**Example:**
```python
API_URL = "https://api.example.com/buy"  # Apna API endpoint yaha daalo
```

⚠️ **Empty chhoda toh purchase kaam nahi karega.**

---

### 🔴 CHANGE #7 — `API_KEY`

**File mein ye line dhoondho:**
```python
API_KEY = ""  # Apna API key yaha daalo
```

**Yahan apne API provider ki key daalo.**

**Example:**
```python
API_KEY = "sk_live_xxxxxxxxxxxxx"  # Apna API key yaha daalo
```

---

### 🔴 CHANGE #8 — `MASTER_KEY`

**File mein ye line dhoondho:**
```python
MASTER_KEY = ""  # Apna master key yaha daalo
```

**Yahan apne API provider ki master key daalo.**

**Example:**
```python
MASTER_KEY = "master_xxxxxxxxxxxxx"  # Apna master key yaha daalo
```

---

### 🔴 CHANGE #9 — `FAMPAY_VERIFY_URL`

**File mein ye line dhoondho:**
```python
FAMPAY_VERIFY_URL = ""  # Apna verify URL yaha daalo
```

**Yahan apna FamPay verify URL daalo.**

**Example:**
```python
FAMPAY_VERIFY_URL = "https://yourdomain.com/verify.php"  # Apna verify URL yaha daalo
```

---

### 🔴 CHANGE #10 — `FAMPAY_QR_URL`

**File mein ye line dhoondho:**
```python
FAMPAY_QR_URL = ""  # Apna QR URL yaha daalo
```

**Yahan apna FamPay QR URL daalo.**

**Example:**
```python
FAMPAY_QR_URL = "https://yourdomain.com/qr.php"  # Apna QR URL yaha daalo
```

---

### 🔴 CHANGE #11 — `FAMPAY_API_KEY`

**File mein ye line dhoondho:**
```python
FAMPAY_API_KEY = ""  # Apna FamPay API key yaha daalo
```

**Yahan apna FamPay API key daalo.**

**Example:**
```python
FAMPAY_API_KEY = "fampay_xxxxxxxxxxxxx"  # Apna FamPay API key yaha daalo
```

---

## ⚙️ STEP 3: DB DEFAULTS — FILE MEIN KYA CHANGE KARNA HAI

Ab `init_db()` function ke andar settings table section mein jao.

**Dhoondho:**
```python
support_name_1 TEXT DEFAULT 'Support',
support_url TEXT DEFAULT '',
manual_upi TEXT DEFAULT '')
```

**Yeh already generic hai.** Change karne ki zaroorat NAHI.

⚠️ **Agar tu chaahta hai ki default support name kuch aur ho, toh change kar:**
```python
support_name_1 TEXT DEFAULT 'YOUR SUPPORT NAME',
support_url TEXT DEFAULT 'https://t.me/yourchannel',
manual_upi TEXT DEFAULT 'yourupi@paytm')
```

---

## ⚙️ STEP 4: MIGRATIONS — FILE MEIN KYA CHANGE KARNA HAI

`migrations` list ke andar ye lines dhoondho:

```python
"ALTER TABLE settings ADD COLUMN support_name_1 TEXT DEFAULT 'Support'",
"ALTER TABLE settings ADD COLUMN support_url TEXT DEFAULT ''",
"ALTER TABLE settings ADD COLUMN manual_upi TEXT DEFAULT ''",
```

**Yeh already generic hai.** Change karne ki zaroorat NAHI.

⚠️ **Agar DB defaults change kiye (Step 3 mein), toh yahan bhi same change karo.**

---

## ⚙️ STEP 5: WELCOME TEXT — FILE MEIN KYA CHANGE KARNA HAI

`get_welcome_text()` function ke andar ye line dhoondho:

```python
🏪 <b>STORE</b> 🏪
```

**Yahan apna store name daalo.**

**Example:**
```python
🏪 <b>MY GAMING STORE</b> 🏪
```

**Aur ye line bhi:**
```python
username = user["username"] if user and user["username"] else "User"
```

**Change karne ki zaroorat NAHI.** `"User"` already generic hai.

---

## ⚙️ STEP 6: SUPPORT MENU — FILE MEIN KYA CHANGE KARNA HAI

Ab 2 functions mein same change karna hai.

### 6.1 — `show_support_menu()` function

**Dhoondho:**
```python
def show_support_menu(call):
    name1 = get_setting("support_name_1", "Support")
    support_url = get_setting("support_url", "https://t.me/")
```

**Yahan apna default support name aur URL daalo.**

**Example:**
```python
def show_support_menu(call):
    name1 = get_setting("support_name_1", "My Support")
    support_url = get_setting("support_url", "https://t.me/mysupport")
```

### 6.2 — `show_support_contacts_menu()` function

**Dhoondho:**
```python
def show_support_contacts_menu(call):
    text = "💬 <b>SUPPORT CONTACTS</b>\n\n"
    markup = InlineKeyboardMarkup(row_width=1)
    name1 = get_setting("support_name_1", "Support")
    support_url = get_setting("support_url", "https://t.me/")
```

**Yahan bhi same change karo (jo 6.1 mein kiya).**

**Example:**
```python
def show_support_contacts_menu(call):
    text = "💬 <b>SUPPORT CONTACTS</b>\n\n"
    markup = InlineKeyboardMarkup(row_width=1)
    name1 = get_setting("support_name_1", "My Support")
    support_url = get_setting("support_url", "https://t.me/mysupport")
```

---

## ⚙️ STEP 7: MANUAL DEPOSIT — FILE MEIN KYA CHANGE KARNA HAI

`show_manual_deposit()` function ke andar ye line dhoondho:

```python
manual_upi = get_setting("manual_upi", "")
```

**Change karne ki zaroorat NAHI.** Empty already generic hai.

⚠️ **Agar default UPI chahiye toh:**
```python
manual_upi = get_setting("manual_upi", "yourupi@paytm")
```

---

## ⚙️ STEP 8: SELLING PROOF — FILE MEIN KYA CHANGE KARNA HAI

`show_selling_proof()` function ke andar:

```python
link = get_setting("selling_proof_link", "https://t.me/")
```

**Change karne ki zaroorat NAHI.** Generic hai.

---

## 🚀 STEP 9: RUN

```bash
python sukisu_store_bot.py
```

**Agar sab theek hai toh ye print hoga:**
```
🚀 Bot running...
```

**Aur ye files ban jaayengi:**
- `bot.log` — general logs
- `api_errors.log` — API errors
- `api_success.log` — API success
- `sukisu.db` — database
- `backups/` — emergency backups folder

---

## 🎯 STEP 10: BOT SETUP (Telegram pe)

### 10.1 — Bot Start Karo
1. Apne bot ko Telegram pe open karo
2. `/start` bhejo
3. Phone number verify karo (Share My Number button)
4. Main menu khul jaayega

### 10.2 — Admin Panel Kholo
Main menu mein **🔧 Admin** button dikhega. Usse click karo.

---

## 🔧 STEP 11: ADMIN PANEL SETUP

### 💰 Payments Section

| Button | Kya Karna Hai |
|--------|---------------|
| 📱 QR Code | Apna QR code upload karo (image bhejo) |
| 🔗 Manual UPI | Apna manual UPI ID set karo |
| 💳 Min Deposit | Minimum deposit amount (default ₹500) |
| 💸 Res Fee | Reseller activation fee (default ₹399) |
| 💳 Reseller Min Balance | Reseller ke liye minimum balance (default ₹2000) |

### 💬 Support Section

| Button | Kya Karna Hai |
|--------|---------------|
| 🎫 Tickets | User tickets dekh sakte ho |
| 💬 Contacts | Support name + URL set karo |
| 📸 Selling Proof Link | Apna proof channel link |
| ❓ FAQ Manager | FAQ add / edit / remove |

### 📦 Products Section

**Naya product add karne ke liye:**

1. **➕ Add Product** → Category choose karo:
   - 🤖 Root (Android Root users)
   - 📱 Non-Root (Android Non-Root users)
   - 🍎 iPhone (iPhone users)

2. Product name(s) bhejo (ek line mein ek naam, multiple ho toh multiple lines)

3. Ab har product pe click karo aur set karo:
   - **🔗 Set API PID** — API provider se product ID
   - **📅 Add Plan** — Duration + Price
     - Format: `1 Day 70` ya `7 Days 261` ya `1 Day 70 50` (last optional reseller price)
   - **📝 Add Features** — Product features (multi-line)
   - **📺 Add Demo Video** — Demo video link
   - **📥 Download Files Link** — Channel link jahan files hain
   - **✏️ Edit Name** — Product ka naam change
   - **🔧 Toggle Maintenance** — Product maintenance ON/OFF
   - **🗑️ Delete Product** — Product delete

### 👥 Users Section

| Button | Kya Karna Hai |
|--------|---------------|
| 💰 Add Balance | User ko balance add karo (format: `user_id amount`) |
| 🚫 Ban User | User ID bhejo ban karne ke liye |
| ✅ Unban User | User ID bhejo unban karne ke liye |
| 👑 Admins | Naye admin add / remove karo |
| 📸 Reviews | User reviews dekho |

### ⚙️ Settings Section

| Button | Kya Karna Hai |
|--------|---------------|
| 🔧 Maintenance | Bot maintenance ON/OFF |
| 💾 Backup | Database backup download |
| 📂 Restore | Database restore (backup file bhejo) |
| 📁 Export CSV | Users / Transactions / Deposits / Orders |
| 📝 Admin Logs | Admin activity logs |

### 📢 Broadcast Section

| Button | Kya Karna Hai |
|--------|---------------|
| 📢 All Users | Sab users ko message |
| ✅ Verified | Sirf verified users ko |
| 👥 Inactive | 7 din se inactive users ko |
| 🤝 Resellers | Sirf resellers ko |
| 💰 Has Balance | Jinke paas balance hai |
| 📸 Media Broadcast | Image / Video / Voice / Audio / Document |

**Media broadcast ke liye:**
1. 📸 Media Broadcast pe click karo
2. Ab koi bhi media bhejo (image/video/voice/audio/document)
3. Bot sab users ko broadcast karega
4. Caption ke saath bhi bhej sakte ho

---

## 📋 ADMIN PANEL BUTTONS — QUICK REFERENCE

```
👑 Dashboard    → Stats, revenue, orders
📊 Analytics    → Today / Weekly / Top products
📦 Products     → Add / Manage / Maintenance
💰 Payments     → Deposits, QR, UPI, fees
👥 Users        → Balance, Ban, Admins
💬 Support      → Tickets, Contacts, FAQ
⚙️ Settings     → Maintenance, Backup, Restore, CSV
📢 Broadcast    → All / Verified / Inactive / Resellers / Media
```

---

## 🔑 USER FLOW (kaise user purchase karega)

1. `/start` → Phone verify
2. **💰 Add Balance** → FamPay ya Manual Deposit
3. **🔑 Shop Key** → Device type choose
4. Product choose → Duration choose
5. **✅ Confirm** → Balance deduct → Key mile
6. Key copy karo → Game mein use karo
7. ⭐ Review do

---

## 🤝 RESELLER SYSTEM

### Reseller Kaise Bane?
1. Minimum **Reseller Min Balance** (default ₹2000) deposit karo
2. **🤝 Become Reseller** → **✅ JOIN NOW**
3. Activation fee (default ₹399) deduct hoga
4. Reseller ban jaoge — ab sab products discounted price pe milenge

### Reseller Benefits
- Sab products discounted price pe
- Custom margin — jitna chaaho profit
- Special reseller tag
- Unlimited earning

### Reseller Price Set Karna (Admin)
1. Admin → 📦 Products → 💰 Reseller
2. Category choose karo
3. Product choose karo
4. Plan choose karo
5. Reseller price set karo

---

## 🎁 REFERRAL SYSTEM

### Kaise Kaam Karta Hai
1. User **🎁 Referral** pe click kare
2. Apna unique link copy kare
3. Friends ko share kare
4. Jab friend pehli purchase kare → **5% bonus** (max ₹100) mile

---

## 🎮 LUCKY SPIN

- Har **24 ghante** mein 1 free spin
- Reward: **₹1 - ₹3** cash
- ⏰ **1 ghante** ke andar use karna hoga
- Purchase pe automatically discount milega
- Expire hone se pehle warning milegi
- **Sirf regular users ke liye** (resellers nahi kar sakte)

---

## 🆘 TROUBLESHOOTING

### Bot start nahi ho raha?
```bash
# Token check karo
# Python version check karo
python --version

# Requirements dobara install karo
pip install --upgrade pyTelegramBotAPI requests
```

### Payment detect nahi ho raha?
- `FAMPAY_API_KEY` verify karo
- `FAMPAY_VERIFY_URL` verify karo
- `api_errors.log` dekho

### Purchase fail ho raha hai?
- `API_URL`, `API_KEY`, `MASTER_KEY` check karo
- Product ka `API PID` set hai ya nahi check karo
- `api_errors.log` dekho

### DB lock error?
- `busy_timeout=30000` set hai, thoda wait karo
- WAL files (`-wal`, `-shm`) delete **mat** karo

### Broadcast slow?
- `BROADCAST_DELAY` badha do (0.05 → 0.1 ya 0.2)
- Telegram rate limit: 30 msg/sec

### Koi aur error?
- `bot.log` dekho
- `api_errors.log` dekho

---

## 📄 LOGS

| File | Kya Hai | Rotation |
|------|---------|----------|
| `bot.log` | General logs | 10MB x 5 |
| `api_errors.log` | API errors | 5MB x 3 |
| `api_success.log` | API success | 5MB x 3 |

**Logs auto-rotate hote hain — disk full nahi hoga.**

---

## 💾 BACKUP & RESTORE

### Manual Backup
Admin → ⚙️ Settings → 💾 Backup

### Auto Backup
- Crash pe automatic backup
- `backups/` folder mein save hota hai
- Admins ko Telegram pe bhi bhejta hai

### Restore
Admin → ⚙️ Settings → 📂 Restore → `.db` file bhejo

⚠️ **Restore se pehle automatic backup ban jaata hai.**

---

## 📊 CSV EXPORT

Admin → ⚙️ Settings → 📁 Export CSV

| Type | Kya Export Hoga |
|------|-----------------|
| 👥 Users | Sab users ka data |
| 💰 Transactions | Sab transactions |
| 📱 Deposits | Manual deposits |
| 📦 Orders | API orders |

---

## 🔧 MAINTENANCE MODE

Admin → ⚙️ Settings → 🔧 Maintenance

**ON karne pe:**
- Sab users ko notification jaayegi
- Users kuch bhi purchase nahi kar payenge
- `check_maintenance` button se check kar sakte hain

**OFF karne pe:**
- Sab users ko wapas welcome message
- Sab kuch normal

---

## 📋 FORMATS — QUICK GUIDE

### Add Plan Format
```
1 Hour 10
3 Hours 20
1 Day 70
7 Days 261
30 Days 700
```

**With reseller price:**
```
1 Day 70 50
7 Days 261 200
```

### Add Balance Format (Admin)
```
123456789 500
```
(Yeh user `123456789` ko ₹500 add karega)

### Add Admin Format
```
123456789
```

### Add Support Contact Format
```
Name | UserID
```

### Add FAQ Format
```
Question | Answer
```

### Ban / Unban Format
```
123456789
```

---

## ⚠️ IMPORTANT NOTES

### ✅ Kya Karna
- Apna `BOT_TOKEN` daalo
- Apna `ADMIN_USER_ID` daalo
- Apna `FAMPAY_UPI_ID` daalo
- Apne API keys daalo
- Admin panel se QR upload karo
- Admin panel se UPI set karo
- Admin panel se support name/URL set karo
- Admin panel se products add karo
- Regular backup lo

### ❌ Kya NAHI Karna
- Kisi aur ka token use mat karo
- Kisi aur ka UPI use mat karo
- Kisi aur ka API key use mat karo
- Config values public repo pe upload mat karo
- WAL files (`-wal`, `-shm`) delete mat karo
- Database file manually edit mat karo (bot band hone pe karo)

---

## 📄 LICENSE

[Apna license yahan likho]

---

## 🆘 SUPPORT

Agar koi issue aaye toh:
1. Logs check karo (`bot.log`, `api_errors.log`)
2. Admin panel se settings verify karo
3. [Apna support contact yahan likho]

---

## 📌 VERSION

**Version:** 1.0.0
**Last Updated:** [Date]
**Status:** Production Ready

---

## 🎯 QUICK START CHECKLIST

```
[ ] Python install kiya
[ ] pyTelegramBotAPI + requests install kiye
[ ] BOT_TOKEN daala
[ ] ADMIN_USER_ID daala
[ ] SUCCESS_IMG daala (optional)
[ ] FAMPAY_UPI_ID daala
[ ] API_URL daala
[ ] API_KEY daala
[ ] MASTER_KEY daala
[ ] FAMPAY_VERIFY_URL daala
[ ] FAMPAY_QR_URL daala
[ ] FAMPAY_API_KEY daala
[ ] Bot run kiya
[ ] /start bheja
[ ] Phone verify kiya
[ ] Admin panel khola
[ ] QR upload kiya
[ ] Manual UPI set kiya
[ ] Support name + URL set kiya
[ ] Products add kiye
[ ] API PID set kiye
[ ] Plans add kiye
[ ] Test purchase kiya
[ ] Backup liya
```

---

**🎉 Bot ready hai! Happy selling!**