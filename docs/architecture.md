# Architecture

This project uses a layered web application architecture designed for a private production codebase and a public-facing case study.

## High-Level Flow

1. The user opens the website in the browser.
2. The frontend renders the storefront or dashboard experience.
3. User actions call the backend API over HTTPS.
4. The backend validates requests, applies application rules, and persists data in PostgreSQL.
5. Stripe handles payment processing where checkout is involved.
6. The app is deployed on a Linux VPS behind Nginx and Cloudflare.

## System Layers

### Frontend

The frontend is built with React, Vite, TypeScript, and Tailwind CSS. It is responsible for:

- Rendering the UI
- Handling navigation and client-side interactions
- Presenting products, dashboard views, and checkout steps
- Keeping the experience responsive across devices

### Backend API

FastAPI and Python provide the application API. This layer handles:

- Request validation
- Business workflow orchestration
- Checkout-related server actions
- Admin and content operations

### Database

PostgreSQL is used for durable storage. Typical data categories include:

- Product records
- Order records
- Operational application data

### Payments

Stripe is used for payment processing. Sensitive payment handling stays inside the payment provider and the backend integration layer.

### Infrastructure

The production environment uses:

- Linux VPS for application hosting
- Nginx for reverse proxying and request routing
- Cloudflare for TLS, caching, and edge protection

## Public Repository Boundary

This document deliberately stays at a high level. It does not expose route names, internal service names, database schema, or private workflow logic.
