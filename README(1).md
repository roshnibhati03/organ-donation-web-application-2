# Organ Donation Application (ODA)

A full-stack prototype for a secure, modern Organ Donation Application bridging donors and recipients with transparent matching.

## Features

- Modern responsive UI (React + Tailwind)
- Secure backend (Node.js/Express + MongoDB)
- Auth with JWT and salted password hashing
- PII encryption at-rest (AES-256-GCM)
- Patient and Donor registration with ABHA ID verification (mock)
- Donor organ opt-in, and waiting list visibility
- Patient organ request and priority scoring
- Transparent donor–patient matching logic
- FAQs, campaigns, resources
- Admin reports dashboard

## Tech Stack

- Frontend: React (Vite), Tailwind CSS
- Backend: Node.js, Express
- Database: MongoDB (Mongoose)
- Auth: JWT (httpOnly cookies), bcrypt
- Encryption: AES-256-GCM using Node crypto

## Monorepo Layout

```
/oda
  /backend
  /frontend
  /docs
```

## Quick Start

### Prerequisites

- Node.js >= 18
- MongoDB instance (local or Atlas)

### 1) Backend

```
cd backend
cp .env.example .env
# Edit .env with your values
npm install
npm run dev
```

Backend starts on http://localhost:4000

### 2) Frontend

```
cd ../frontend
npm install
npm run dev
```

Frontend runs on http://localhost:5173

## Environment Variables (Backend)

Copy `.env.example` to `.env` and set:

```
PORT=4000
MONGODB_URI=mongodb://127.0.0.1:27017/oda
JWT_SECRET=change_me
CRYPTO_SECRET=32_characters_min_key_change_me
COOKIE_SECURE=false
CORS_ORIGIN=http://localhost:5173
```

- `CRYPTO_SECRET` must be 32+ chars for AES-256.
- Set `COOKIE_SECURE=true` in production (HTTPS only).

## Docs

- See `docs/ARCHITECTURE.md` for system architecture, ER, and schema details.

## Security Notes

- Passwords hashed with bcrypt.
- PII fields (name, phone, address, abhaId) encrypted at-rest via AES-256-GCM.
- JWT in httpOnly, SameSite=Lax cookies to mitigate XSS.
- Basic validation and rate limiting scaffolded.

## Disclaimer

- ABHA ID verification is mocked for prototype purposes. Replace with a real integration in production.
