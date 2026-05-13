
# Qply Widget Snippets

Official embed examples for **[Qply](https://qply.io)** — the AI-powered live chat widget for Shopify, WordPress, Webflow, and any website.

> 🚀 New here? **[Get started with Qply free →](https://qply.io)**

---

## Table of contents

- [Plain HTML / any website](#plain-html--any-website)
- [Qply for Shopify](#qply-for-shopify)
- [Qply for WordPress](#qply-for-wordpress)
- [Qply for Webflow](#qply-for-webflow)
- [Qply with React](#qply-with-react)
- [Qply with Next.js](#qply-with-nextjs)
- [Qply with Vue](#qply-with-vue)

---

## Plain HTML / any website

Paste this snippet before the closing `</body>` tag on any page where you want the **[Qply chat widget](https://qply.io)** to appear:

```html
<!-- Qply Live Chat Widget -->
<script>
  (function(w,d,s,o){
    w.QplyConfig = { siteKey: 'YOUR_SITE_KEY' };
    var j = d.createElement(s); j.async = true; j.src = 'https://qply.io/widget.js';
    var f = d.getElementsByTagName(s)[0]; f.parentNode.insertBefore(j, f);
  })(window, document, 'script');
</script>
```

Replace `YOUR_SITE_KEY` with the key from your [Qply dashboard](https://qply.io/dashboard).

---

## Qply for Shopify

1. In your Shopify admin, go to **Online Store → Themes → Edit code**
2. Open `layout/theme.liquid`
3. Paste the snippet above just before `</body>`
4. Save

The Qply widget will now appear on every page of your store.

📘 [Full Shopify guide on Qply.io →](https://qply.io/docs/shopify)

---

## Qply for WordPress

**Option A — using a code-snippets plugin:**

Install [Code Snippets](https://wordpress.org/plugins/code-snippets/) (or similar) and add the Qply snippet as a footer snippet.

**Option B — adding to your theme directly:**

In `wp-content/themes/your-theme/footer.php`, paste the Qply snippet before `</body>`:

```php
<?php // Qply Live Chat Widget ?>
<script>
  (function(w,d,s){
    w.QplyConfig = { siteKey: 'YOUR_SITE_KEY' };
    var j = d.createElement(s); j.async = true; j.src = 'https://qply.io/widget.js';
    var f = d.getElementsByTagName(s)[0]; f.parentNode.insertBefore(j, f);
  })(window, document, 'script');
</script>
```

📘 [Full WordPress guide on Qply.io →](https://qply.io/docs/wordpress)

---

## Qply for Webflow

1. In your Webflow project settings, go to **Custom Code**
2. Paste the Qply snippet into the **Footer Code** field
3. Publish your site

📘 [Full Webflow guide on Qply.io →](https://qply.io/docs/webflow)

---

## Qply with React

```jsx
import { useEffect } from 'react';

export function QplyWidget({ siteKey }) {
  useEffect(() => {
    window.QplyConfig = { siteKey };
    const script = document.createElement('script');
    script.src = 'https://qply.io/widget.js';
    script.async = true;
    document.body.appendChild(script);
    return () => { document.body.removeChild(script); };
  }, [siteKey]);
  return null;
}

// Usage:
// <QplyWidget siteKey="YOUR_SITE_KEY" />
```

---

## Qply with Next.js

In `app/layout.tsx` (App Router):

```tsx
import Script from 'next/script';

export default function RootLayout({ children }) {
  return (
    <html>
      <body>
        {children}
        <Script id="qply-widget" strategy="afterInteractive">
          {`
            window.QplyConfig = { siteKey: 'YOUR_SITE_KEY' };
            (function(d,s){
              var j = d.createElement(s); j.async = true; j.src = 'https://qply.io/widget.js';
              d.body.appendChild(j);
            })(document, 'script');
          `}
        </Script>
      </body>
    </html>
  );
}
```

---

## Qply with Vue

```vue
<script setup>
import { onMounted, onUnmounted } from 'vue';

const props = defineProps({ siteKey: String });

let script = null;
onMounted(() => {
  window.QplyConfig = { siteKey: props.siteKey };
  script = document.createElement('script');
  script.src = 'https://qply.io/widget.js';
  script.async = true;
  document.body.appendChild(script);
});
onUnmounted(() => { if (script) document.body.removeChild(script); });
</script>
```

---

## About Qply

**[Qply](https://qply.io)** is an AI live chat platform built for small businesses. We help Shopify, WordPress, and Webflow stores convert more visitors with AI replies, real-time messaging, and a mobile-friendly agent dashboard — all for a fraction of the cost of enterprise chat tools.

- 🌐 [qply.io](https://qply.io)
- 📘 [Documentation](https://qply.io/docs)
- 🐦 [X / Twitter](https://x.com/qplyio)
- 💼 [LinkedIn](https://www.linkedin.com/company/qply/)
- 💬 [Support](https://qply.io/contact)

## License

MIT — feel free to adapt these snippets for your own integrations. 
