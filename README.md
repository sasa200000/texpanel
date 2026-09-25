# TEXPANEL

پنل مدیریت پروکسی مبتنی بر **Cloudflare Workers** — سبک، سریع و کاملاً رایگان.
بدون نیاز به سرور، بدون نیاز به root؛ فقط یک حساب Cloudflare.

---

## ✨ امکانات

- 🌐 **چند پروتکل**: VLESS / VMess / Trojan / socks (همه روی یک Worker)
- 📡 **اشتراک‌ساز جاافتاده**: لینک سابسکریپشن + تبدیل با بک‌اند دلخواه (subconverter)
- 🎯 **IPهای منتخب**: منبع IP سفارشی یا استخراج‌شده از بهترین IPهای عمومی
- 📊 **نمودار مصرف زنده**: نمودار آنی و animated مصرف Worker به‌صورت realtime
- 🤖 **ربات تلگرام**: مدیریت کامل پنل از داخل تلگرام (وضعیت، ریستارت، آمار)
- 🔐 **ورود ایمن**: رمز عبور هش‌شده + توکن جلسه + محافظت در برابر کشف نشست
- 🛡️ **ضد هک**: هدرهای امنیتی سخت‌گیرانه (CSP / X-Frame-Options / CORP)، مسدودسازی درخواست‌های مخرب، اعتبارسنجی نشست
- 🎨 **تم نئون**: صورتی / زرد فسفری / سبز فسفری / سیاه، حالت روشن و تاریک
- 🌍 **دوزبانه**: فارسی و انگلیسی در همه‌جا
- ☁️ **ذخیره‌سازی**: Cloudflare D1 + KV (رایگان)
- 🔧 **آپدیت از داخل پنل**: بدون نیاز به دستکاری کد

---

## 🚀 راه‌اندازی

1. وارد [Cloudflare Dashboard](https://dash.cloudflare.com) شوید.
2. یک **D1 Database** و یک **KV Namespace** بسازید.
3. فایل `wrangler.toml` را باز کنید و این‌ها را پر کنید:
   - `account_id`
   - نام و آیدی D1 (`[[d1_databases]]`)
   - نام و آیدی KV (`[[kv_namespaces]]`)
4. اعتبارنامه‌ها را در متغیرهای محیطی Worker تنظیم کنید:
   - `PASSWORD` — رمز ورود به پنل
   - `TG_BOT_TOKEN` — توکن ربات تلگرام (اختیاری)
   - `TG_CHAT_ID` — آیدی عددی شما (اختیاری)
5. دیپلوی:
   ```bash
   npx wrangler deploy
   ```
6. آدرس Worker را باز کنید، رمز را وارد کنید و تمام.

---

## 🔒 امنیت

TEXPANEL به‌صورت پیش‌فرض این‌ها را فعال می‌کند:

| هدر | مقدار |
|---|---|
| `Content-Security-Policy` | `default-src 'self'` + فقط فونت گوگل |
| `X-Frame-Options` | `DENY` |
| `X-Content-Type-Options` | `nosniff` |
| `X-XSS-Protection` | `1; mode=block` |
| `Cross-Origin-Opener-Policy` | `same-origin` |
| `Cross-Origin-Resource-Policy` | `same-origin` |

به‌علاوهٔ نشست‌های کوتاه، توکن CSRF در فرم‌ها و مسدودسازی IPهای مشکوک.

---

## 📜 لایسنس

MIT — استفاده آزاد. کپی‌رایت © 2026 TEXPANEL.

## 📸 اسکرین‌شات‌ها / Screenshots

| فایل | توضیح |
|---|---|
| [docs/login.png](docs/login.png) | صفحهٔ ورود (رمز عبور) |
| [docs/01-overview.png](docs/01-overview.png) | نمای کلی + لینک‌های اتصال |
| [docs/02-user-management.png](docs/02-user-management.png) | مدیریت کاربران (افزودن/حذف/ریست/کپی لینک) |
| [docs/03-ip-scanner.png](docs/03-ip-scanner.png) | اسکنر IP تمیز یک‌کلیکی |
| [docs/04-usage-chart.png](docs/04-usage-chart.png) | نمودار زندهٔ مصرف (canvas) |
| [docs/05-custom-ip-list.png](docs/05-custom-ip-list.png) | لیست IP دلخواه |
| [docs/06-telegram-bot.png](docs/06-telegram-bot.png) | تنظیمات ربات تلگرام |
| [docs/07-logs.png](docs/07-logs.png) | لاگ‌های اخیر |
