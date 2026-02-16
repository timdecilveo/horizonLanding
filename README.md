# HorizonOS Landing Page

A minimal, static landing page for HorizonOS — the operating system for modern service businesses.

## Tech Stack

- Plain HTML + CSS
- No frameworks or build tools
- Hosted on GitHub Pages

## Local Development

Open `index.html` in a browser, or run a simple local server:

```bash
# Python 3
python -m http.server 8000

# Node.js (npx)
npx serve .
```

Visit `http://localhost:8000`.

## Deploy to GitHub Pages

### 1. Push to GitHub

If you haven't already:

```bash
git init
git add .
git commit -m "Initial commit: HorizonOS landing page"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/horizonLanding.git
git push -u origin main
```

### 2. Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages** (in the left sidebar)
3. Under **Source**, select **Deploy from a branch**
4. Under **Branch**, choose `main` and `/ (root)`
5. Click **Save**

Your site will be live at `https://YOUR_USERNAME.github.io/horizonLanding/` within a few minutes.

## Optional: Connect Formspree

To receive form submissions via email without a backend:

1. Sign up at [Formspree](https://formspree.io)
2. Create a new form and copy your form endpoint (e.g. `https://formspree.io/f/xxxxx`)
3. Replace the form submit handler in `index.html` to validate, then submit via `fetch`:

```javascript
document.getElementById('contactForm').addEventListener('submit', async function(e) {
  e.preventDefault();
  // ... keep validation logic ...
  if (valid) {
    const formData = new FormData(this);
    await fetch('https://formspree.io/f/YOUR_FORM_ID', {
      method: 'POST',
      body: formData,
      headers: { 'Accept': 'application/json' }
    });
    successMessage.classList.add('visible');
    this.reset();
  }
});
```

This preserves the success message UX while sending data to Formspree.
