# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

SNR Builders Website is a professional website for a construction company built with plain HTML, CSS, and Vanilla JavaScript. The site showcases services, projects, team information, and enables client contact. Hosted on Cloudflare Pages with auto-deployment from GitHub.

## Tech Stack

**Frontend:**
- Plain HTML5 / CSS3 / Vanilla JavaScript (ES6+)
- No build tooling, no dependencies
- Responsive design for desktop, tablet, and mobile
- Modern accessibility standards (WCAG 2.1)
- Static site hosted on Cloudflare Pages

**Features:**
- Multiple pages (Home, About, Services, Gallery, Contact)
- Image gallery with lightbox/filtering
- Google Maps integration
- Contact form with validation
- WhatsApp redirect button
- SEO-friendly markup

## Project Structure

The website source lives in a separate GitHub repository (e.g., `SNR-Builders-Website/`).
Local Claude Code config stays in `.claude/` and is NOT committed to GitHub.

```
SNR-Builders-Website/  (GitHub repo)
├── index.html          ← Homepage
├── about.html          ← About SNR Builders
├── services.html       ← Services offered
├── gallery.html        ← Project gallery
├── contact.html        ← Contact form + map + WhatsApp
├── assets/
│   ├── images/         ← All project photos
│   └── icons/          ← Favicon, social icons
├── styles/
│   ├── main.css        ← Global styles and layout
│   └── components.css  ← Cards, gallery, form, navbar
├── scripts/
│   ├── gallery.js      ← Image gallery/lightbox
│   ├── contact.js      ← Form validation and submission
│   └── maps.js         ← Google Maps integration
├── README.md           ← Project documentation
└── .gitignore          ← Exclude system files
```

## Development Workflow

### No Build Step Needed
Edit `.html`, `.css`, and `.js` files directly. Open any `.html` file in a browser to preview locally.

### Local Development
```bash
# Option 1: Simple HTTP server (Python 3)
python -m http.server 8000

# Option 2: Using npx (no install needed)
npx http-server

# Option 3: VS Code Live Server extension
# Right-click index.html → Open with Live Server
```

Then visit `http://localhost:8000` (or the server's port).

### Git Workflow
```bash
# View status
git status

# Stage changes
git add .

# Commit (use GitHub MCP for this via Claude Code)
git commit -m "description"

# Push to GitHub (use GitHub MCP for this via Claude Code)
git push origin main
```

## Cloudflare Pages Deployment

1. Connect GitHub repo to Cloudflare Pages
2. Set **Build command:** (leave empty — no build needed)
3. Set **Output directory:** `/` (root folder)
4. Every push to `main` auto-deploys

No environment variables needed — this is a static site with no backend.

## Key Development Areas

**Homepage (index.html):**
- Hero section with company background
- Service overview cards
- Recent projects showcase
- Call-to-action (CTA) buttons
- Testimonials section

**Gallery (gallery.html):**
- Image grid with lightbox
- Project filtering (e.g., Residential, Commercial, Renovations)
- Before/after image comparisons
- Project details and metrics

**Services (services.html):**
- Service cards with descriptions
- Service benefits/features
- Pricing (if applicable)
- CTA to contact form

**Contact (contact.html):**
- Contact form with validation (name, email, message)
- Google Maps embed (office location)
- Contact information (phone, email, address)
- WhatsApp chat button

**About (about.html):**
- Company history and mission
- Team member profiles (optional)
- Why choose SNR Builders

## Styling Approach

- **Color Palette:** Professional construction industry colors (grays, blues, earth tones)
- **Typography:** Clear hierarchy, readable font sizes (16px+ body text)
- **Spacing:** Consistent margins and padding (use a grid: 8px, 16px, 24px, 32px, etc.)
- **Responsive:** Mobile-first CSS, test on 320px+ widths
- **No CSS framework:** Write custom CSS in `main.css` and `components.css`
- **Reusable components:** `.card`, `.btn`, `.section-title`, `.gallery-grid`, etc.

## Images & Assets

- **Format:** Use modern formats (WebP with JPG fallbacks) for photos
- **Optimization:** Compress images before adding to repo (max 150KB per image)
- **Lazy loading:** Use `loading="lazy"` on off-screen images
- **Alt text:** Every image must have meaningful alt text for accessibility

## Form Handling

The contact form can submit to:
1. **Formspree:** Free, no backend needed (formspree.io)
2. **Netlify Forms:** Free tier available
3. **Custom backend:** If SNR Builders has their own email service

Store the form endpoint in local config, NOT in the HTML/JS.

## SEO & Meta Information

- Unique `<title>` and `<meta name="description">` on every page
- Open Graph tags for social sharing (`og:title`, `og:image`, etc.)
- Structured data (JSON-LD) for Organization, LocalBusiness, and Service types
- Mobile viewport meta tag: `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
- Favicon and apple-touch-icon
- `robots.txt` and XML sitemap (optional but recommended)

## Code Quality Standards

- Semantic HTML5 (`<header>`, `<nav>`, `<main>`, `<footer>`, `<section>`, etc.)
- BEM naming for CSS classes (`.card`, `.card__title`, `.card--featured`)
- Vanilla JS: no jQuery or frameworks
- Comments only for non-obvious logic
- No inline styles (use CSS classes)
- Accessible form labels and ARIA attributes where needed
- Keyboard navigation support for all interactive elements

## Performance & Accessibility Checklist

- [ ] Lighthouse audit: 90+ on all metrics
- [ ] Mobile responsive: test on 320px, 768px, 1200px widths
- [ ] Form validation: real-time feedback for invalid inputs
- [ ] Images optimized and lazy-loaded
- [ ] Links have descriptive text (avoid "Click here")
- [ ] Color contrast: WCAG AA minimum (4.5:1 for body text)
- [ ] Focus indicators visible on all interactive elements
- [ ] No broken links or 404s
