# EmailJS Setup Instructions for Contact Form

Your contact form has been updated to use **EmailJS** - a free email service that sends emails directly from your website without needing a backend server.

## ✅ What Was Changed

1. **Removed** old PHP form submission
2. **Removed** Google reCAPTCHA (can be added back if needed)
3. **Added** EmailJS SDK integration
4. **Updated** form field names to work with EmailJS
5. **Added** loading spinner and better user feedback

## 📧 EmailJS Setup Steps (FREE - 200 emails/month)

### Step 1: Create EmailJS Account

1. Go to [https://www.emailjs.com/](https://www.emailjs.com/)
2. Click **"Sign Up"** (completely free)
3. Sign up with your Google account or email

### Step 2: Add Email Service

1. After logging in, go to **"Email Services"** in the dashboard
2. Click **"Add New Service"**
3. Choose your email provider:
   - **Gmail** (recommended for personal)
   - **Outlook/Office365**
   - Or any other supported service
4. Click **"Connect Account"** and authorize EmailJS
5. **Copy the Service ID** (you'll need this later)

### Step 3: Create Email Template

1. Go to **"Email Templates"** in the dashboard
2. Click **"Create New Template"**
3. Use this template content:

**Subject:**
```
New Contact Form Submission: {{subject}}
```

**Content:**
```
You have received a new message from your website contact form.

From: {{from_name}}
Email: {{reply_to}}
Phone: {{phone}}
Subject: {{subject}}

Message:
{{message}}

---
This email was sent from the Nebula Consultancy Services contact form.
```

4. **Important:** In the settings, set the **"To Email"** to your email address: `support@consult-nebula.com`
5. Click **"Save"**
6. **Copy the Template ID** (you'll need this)

### Step 4: Get Your Public Key

1. Go to **"Account"** → **"General"** in the EmailJS dashboard
2. Find your **"Public Key"** (also called User ID)
3. **Copy it** (it looks like: `user_xxxxxxxxxxxxx` or similar)

### Step 5: Update Your Website Code

Open `contact.html` and find these three lines (around line 348-365):

```javascript
emailjs.init('YOUR_PUBLIC_KEY'); // Replace this
```

```javascript
const serviceID = 'YOUR_SERVICE_ID'; // Replace this
const templateID = 'YOUR_TEMPLATE_ID'; // Replace this
```

Replace them with your actual values:

```javascript
emailjs.init('user_xxxxxxxxxxxxx'); // Your public key from Step 4
```

```javascript
const serviceID = 'service_xxxxxxx'; // Your service ID from Step 2
const templateID = 'template_xxxxxxx'; // Your template ID from Step 3
```

### Step 6: Test Your Form

1. Save the `contact.html` file
2. Upload it to your server
3. Go to your contact page
4. Fill out the form and submit
5. You should receive an email at `support@consult-nebula.com`

## 🎯 Template Field Names

The form uses these field names (already configured):
- `from_name` - Visitor's name
- `reply_to` - Visitor's email
- `phone` - Visitor's phone
- `subject` - Subject selection
- `message` - Message content

## 🔧 Customization Options

### Change the "To" Email Address

In the EmailJS template settings, update the "To Email" field.

### Add Auto-Reply to Visitors

In your EmailJS template, you can enable "Auto Reply" to send a confirmation email back to the visitor.

### Add reCAPTCHA Back (Optional)

If you want to add spam protection back, you can integrate EmailJS with Google reCAPTCHA v3.

## 💰 Pricing

- **Free Plan**: 200 emails/month (perfect for most small businesses)
- **Personal Plan**: $7/month - 1,000 emails
- **Business Plan**: $15/month - 10,000 emails

## 🆘 Troubleshooting

### Form submits but no email received

1. Check your EmailJS dashboard → "Email Service" → Make sure it's connected
2. Check spam folder
3. Verify the "To Email" in your template matches your email
4. Check EmailJS logs in dashboard for errors

### "Failed to send" error

1. Verify all three IDs are correct (Public Key, Service ID, Template ID)
2. Check browser console for detailed error messages
3. Make sure your EmailJS service is still connected

### Quota exceeded

You've hit the 200 emails/month limit on the free plan. Either:
- Upgrade to a paid plan
- Wait until next month for quota reset

## 📱 Features

✅ No backend/server required
✅ Works from static HTML
✅ Real-time delivery
✅ Spam protection (EmailJS has built-in protection)
✅ Delivery tracking in dashboard
✅ Auto-reply support
✅ Custom templates
✅ Multiple email services

## 🔗 Useful Links

- EmailJS Dashboard: https://dashboard.emailjs.com/
- EmailJS Documentation: https://www.emailjs.com/docs/
- Support: https://www.emailjs.com/docs/faq/

## ⚠️ Important Notes

1. Keep your Public Key and Service ID safe (don't share publicly)
2. Monitor your monthly usage in the EmailJS dashboard
3. EmailJS quota resets on the 1st of each month
4. Emails typically arrive within seconds

---

**Need Help?** 
- EmailJS Support: support@emailjs.com
- Documentation: https://www.emailjs.com/docs/

Good luck! 🚀
