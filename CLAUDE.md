# nocnoc Developer Hub — Context for Claude

## What this project is

This is the **nocnoc Developer Hub** — a documentation portal that covers all the ways sellers can integrate with nocnoc. It is not just an API reference. It is a hub for multiple integration methods, with the REST API as the first available one.

The portal lives at `nocnoc.mintlify.app` and is built with Mintlify (MDX + docs.json), deployed automatically on every push to the `main` branch of this repo.

## Integration methods

| Integration | Status | Location |
|-------------|--------|----------|
| REST API | Live | `/api/` |
| Shopify | Coming soon | — |
| Goflow | Coming soon | — |
| SFTP | Coming soon | — |
| Sellercloud | Coming soon | — |

When a new integration is ready, it gets its own top-level folder (e.g. `/shopify/`) and a new tab in `docs.json`.

## Project structure

```
index.mdx                  ← Hub landing page (hero + integration cards)
docs.json                  ← Navigation, colors, logo, theme
logo/                      ← nocnoc SVG logos (light and dark)
images/                    ← 3D icon assets
favicon.svg                ← nocnoc icon

api/                       ← REST API integration
  introduction.mdx
  quickstart.mdx
  guides/
    sending-packages.mdx
  api-reference/
    overview.mdx
    responses.mdx
    products/
      list-products.mdx
      get-product.mdx
      create-product.mdx
      create-product-asin.mdx
      update-stock-price.mdx
    orders/
      list-orders.mdx
      cancel-order.mdx
    packages/
      create-son-package.mdx
      create-father-package.mdx
```

## Brand guidelines

### Colors
- **Mid Blue** `#0061FC` — primary, headers, CTAs, hero backgrounds
- **Deep Blue** `#010533` — dark backgrounds, secondary sections
- **Neutral Cream** `#F4F3EF` — light backgrounds (not currently applied per-page)
- **Bright Aqua** `#A4F9FF` — accents, highlights, eyebrow labels

### Typography
- **Poppins** — headlines and titles only
- **Manrope** — body text and supporting content

### Tone
- Direct and professional — not casual, not corporate
- Seller-first: explain business context before technical details
- Less is more — avoid unnecessary content, keep pages focused
- English only throughout the documentation

## Navigation structure (docs.json)

```
Home tab         → index.mdx (hub landing)
REST API tab     → Get started, Products, Orders, Packages, Reference
```

### REST API sidebar
```
Get started
  ├── Introduction
  └── Quick Start

Products
  ├── Get products
  ├── Get product by SKU
  ├── Create product
  ├── Create product by ASIN
  └── Update stock and price

Orders
  ├── List orders
  └── Cancel order

Packages
  ├── Sending packages (guide)
  ├── Create Son package
  └── Create Father package

Reference
  ├── Response codes
  └── Overview
```

## API details

- **Base URL:** `https://live.nocnocstore.com/api/v2`
- **Auth:** `X-Api-Key: YOUR_SELLER_KEY` header on every request
- **Format:** REST, JSON
- **Version:** v2
- **Environment:** Live only — no sandbox. All requests generate real orders.

## Content conventions

### Every API endpoint page must have:
1. `api:` in frontmatter with the full method + URL
2. All parameters with `<ParamField>` — include type, required flag, and description
3. A `## Returns` section explaining what the response contains
4. An `## Example request` with a curl snippet
5. A `<ResponseExample>` block with real JSON for each response code (200/201, 400, 401, 404 as applicable)

### Page frontmatter pattern
```mdx
---
title: "Endpoint name"
api: "METHOD https://live.nocnocstore.com/api/v2/path"
description: "One sentence describing what this endpoint does."
---
```

### Notes and warnings
- Use `<Note>` for helpful context (e.g. "use ASIN endpoint if you have an ASIN")
- Use `<Warning>` for important caveats (e.g. live environment, irreversible actions)

### What NOT to do
- Don't add unnecessary intro paragraphs — get to the content fast
- Don't repeat information already covered in Quick Start or Overview
- Don't use Spanish — everything is in English
- Don't add steps or guides inside endpoint pages — those belong in `/guides/`

## Landing page (index.mdx)

The hub landing has two sections:
1. **Hero** (blue `#0061FC`) — headline, description, two CTAs (Quick Start + View endpoints)
2. **Integration cards** (dark `#010533`) — one card per integration method. Active integrations link to their intro page. Coming soon integrations are visible but not clickable (no `href`, reduced opacity).

When adding a new integration, add a card to `index.mdx` and a new tab to `docs.json`.

## Deployment

Push to `main` → Mintlify auto-deploys to `nocnoc.mintlify.app`.
GitHub repo: `https://github.com/lucasbenmaor/mintlify`
