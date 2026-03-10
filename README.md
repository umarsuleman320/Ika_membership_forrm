# IKA Membership Application Form

**Ikhwatul Kiraam Association — Online Membership Form**

A fully branded, multi-step membership application form that:
- Collects all applicant data including passport photo and signature
- Generates a **beautifully designed PDF** in the browser (like a graphic designer made it)
- Emails the PDF to the **applicant** automatically
- Emails a copy to the **IKA admin** inbox
- Hosted free on **GitHub Pages**

---

## STEP 1 — Set Up EmailJS (Free)

EmailJS lets you send emails directly from the browser for free (200 emails/month on free plan).

1. Go to **https://www.emailjs.com** and create a free account
2. After logging in, click **"Add New Service"**
   - Choose **Gmail**
   - Connect your Gmail account: `ikhwatulkiraamassociation@gmail.com`
   - Give it a name: `IKA Gmail`
   - Copy the **Service ID** (looks like: `service_xxxxxxx`)

3. Click **"Email Templates"** → **"Create New Template"**

### Template 1 — For the Applicant (confirmation)
- Template Name: `IKA Applicant Confirmation`
- Subject: `Your IKA Membership Application — {{applicant_name}}`
- Body:
```
Assalamu Alaikum {{to_name}},

JazakAllahu Khairan for applying to join Ikhwatul Kiraam Association!

Your membership application has been received and is being reviewed by the Registrar.

Application Details:
- Name: {{applicant_name}}
- Branch: {{branch}}
- Membership Type: {{mem_type}}
- Submitted: {{submitted}}

Your application form (PDF) is attached to this email. Please keep it for your records.

We will contact you on {{phone}} regarding the next steps.

Yours in faith and brotherhood/sisterhood,
IKA Secretariat
Ikhwatul Kiraam Association
ikhwatulkiraamassociation@gmail.com | +234 707 578 0916
```
- Copy the **Template ID** (looks like: `template_xxxxxxx`)

### Template 2 — For Admin (copy of every submission)
- Template Name: `IKA Admin Copy`
- Subject: `[NEW APPLICATION] {{applicant_name}} — {{branch}} — {{mem_type}}`
- Body:
```
New membership application received.

Applicant: {{applicant_name}}
Branch: {{branch}}
Membership Type: {{mem_type}}
Phone: {{phone}}
Email: {{to_email}} (applicant's email, not this one)
Submitted: {{submitted}}

The full application PDF is attached.

— IKA Automated System
```
- Copy the **Template ID**

4. Go to **Account → API Keys** → copy your **Public Key**

---

## STEP 2 — Update index.html with your EmailJS keys

Open `index.html` and find these lines near the bottom (around line 560):

```javascript
const EMAILJS_SERVICE_ID  = 'YOUR_SERVICE_ID';
const EMAILJS_TEMPLATE_APPLICANT = 'YOUR_TEMPLATE_APPLICANT';
const EMAILJS_TEMPLATE_ADMIN     = 'YOUR_TEMPLATE_ADMIN';
const EMAILJS_PUBLIC_KEY  = 'YOUR_PUBLIC_KEY';
```

Replace each value with your actual keys from Step 1.

Example:
```javascript
const EMAILJS_SERVICE_ID  = 'service_abc1234';
const EMAILJS_TEMPLATE_APPLICANT = 'template_xyz5678';
const EMAILJS_TEMPLATE_ADMIN     = 'template_def9012';
const EMAILJS_PUBLIC_KEY  = 'AbCdEfGhIjKlMnOp';
```

---

## STEP 3 — Push to GitHub & Enable GitHub Pages

### Option A — Using GitHub Desktop (Easiest)
1. Download GitHub Desktop: https://desktop.github.com
2. Open it → File → New Repository
   - Name: `ika-membership`
   - Local path: choose a folder
3. Copy `index.html` and `README.md` into that folder
4. In GitHub Desktop → click **"Publish repository"** → uncheck "Keep private" → Publish
5. Go to your GitHub repo online: `https://github.com/umarsuleman320/ika-membership`
6. Click **Settings** → **Pages** (left sidebar)
7. Under "Source" → select **"Deploy from a branch"** → Branch: **main** → Folder: **/ (root)** → Save

Your form will be live at:
**https://umarsuleman320.github.io/ika-membership**

### Option B — Using Git Command Line
```bash
cd /path/to/ika-membership
git init
git add .
git commit -m "IKA Membership Form — initial"
git remote add origin https://github.com/umarsuleman320/ika-membership.git
git push -u origin main
```
Then enable Pages in Settings as above.

---

## STEP 4 — Test It

1. Open your live URL
2. Fill in the form with test data
3. Upload a test photo and signature
4. Submit — check that:
   - ✅ Loading screen appears
   - ✅ Success screen shows
   - ✅ Email arrives at the applicant's inbox (with PDF attached)
   - ✅ Email arrives at `ikhwatulkiraamassociation@gmail.com`

---

## What the PDF looks Like

The generated PDF includes:
- **IKA official header** (deep green + gold border, logo, Arabic name, motto)
- **Applicant's passport photograph** (top right)
- **Applicant's signature** (below photo)
- All 7 sections of data in a clean two-column table layout
- **Official footer** with page numbers and patron names
- Colour-coded section headings in IKA deep green

---

## Free Plan Limits

| Service | Free Limit |
|---------|-----------|
| EmailJS | 200 emails/month |
| GitHub Pages | Unlimited |
| jsPDF (PDF generation) | Unlimited (runs in browser) |

For higher volumes, upgrade EmailJS (~$9/month for 1,000 emails).

---

## Support

For technical issues contact the system builder or email:
**ikhwatulkiraamassociation@gmail.com**

_Ikhwatul Kiraam Association · Unity in Knowledge, Together in Faith and Action_
