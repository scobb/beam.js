# beam.js

Open-source tracking script for [Beam](https://beam.keylightdigital.dev), a privacy-first web analytics service from Keylight Digital LLC.

`beam.js` is the tiny client-side script that powers Beam pageview and custom event collection. The backend and dashboard are a hosted SaaS product; this repository contains only the browser tracking script so developers can inspect exactly what runs on their sites.

## What Beam tracks

- Page path
- Referrer URL
- Screen width
- Browser language
- Timezone
- Optional UTM tags: `utm_source`, `utm_medium`, `utm_campaign`
- Optional custom event name and JSON properties when you call `beam.track(...)`

## What Beam does not track

- Cookies
- `localStorage` or `sessionStorage`
- IP addresses in the script
- Persistent user identifiers
- Cross-site behavior
- Any ad-tech or fingerprinting data

## Setup

Add the script tag to your page `<head>`:

```html
<script defer src="https://beam.keylightdigital.dev/js/beam.js" data-site-id="YOUR_SITE_ID"></script>
```

Beam automatically sends a pageview on load.

### Custom events

```html
<script>
  window.beam.track('signup_started', { plan: 'pro' })
</script>
```

## Framework examples

### Plain HTML

```html
<!doctype html>
<html lang="en">
  <head>
    <script defer src="https://beam.keylightdigital.dev/js/beam.js" data-site-id="YOUR_SITE_ID"></script>
  </head>
</html>
```

### React

```jsx
export function App() {
  return (
    <>
      <script defer src="https://beam.keylightdigital.dev/js/beam.js" data-site-id="YOUR_SITE_ID"></script>
      <main>Your app</main>
    </>
  )
}
```

### Next.js

```tsx
import Script from 'next/script'

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="en">
      <body>
        <Script
          id="beam"
          strategy="afterInteractive"
          src="https://beam.keylightdigital.dev/js/beam.js"
          data-site-id="YOUR_SITE_ID"
        />
        {children}
      </body>
    </html>
  )
}
```

### WordPress

Paste this snippet into your theme header or a code-injection plugin:

```html
<script defer src="https://beam.keylightdigital.dev/js/beam.js" data-site-id="YOUR_SITE_ID"></script>
```

## Development notes

- Hosted product: https://beam.keylightdigital.dev
- Pricing: free tier available, Pro at $5/month
- Privacy model: cookie-free, no persistent identifiers, GDPR-friendly by design

## License

MIT
