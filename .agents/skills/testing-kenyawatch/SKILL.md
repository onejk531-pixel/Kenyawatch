# Testing Kenyawatch App

## Prerequisites
- bun installed (`curl -fsSL https://bun.sh/install | bash`)
- Dependencies installed (`bun install`)
- `.env` file with `DATABASE_URL="file:./db/custom.db"`
- Prisma client generated (`bunx prisma generate && bunx prisma db push`)

## Devin Secrets Needed
- None required for basic testing (no auth configured)

## Starting the Dev Server
```bash
source ~/.bash_profile
bun run dev
```
Server runs on `http://localhost:3000`.

## Key Test Points

### 1. Landing Page (`/`)
- Should display a centered Z.ai logo (`/logo.svg`)
- Page title: "Z.ai Code Scaffold - AI-Powered Development"
- White/light background by default
- No console errors (React DevTools info and Fast Refresh messages are expected)

### 2. API Route (`/api`)
- `GET /api` should return JSON: `{"message":"Hello, world!"}`

### 3. Static Assets (`/logo.svg`)
- Should render the Z.ai logo SVG directly in the browser
- Should NOT return a 404

## Build & Lint Verification
```bash
bun run build    # Should compile successfully, generates standalone output
bun run lint     # Should pass (may show minor warnings, no errors)
```

## Notes
- The project uses Next.js 15 with App Router
- `next.config.ts` has `ignoreBuildErrors: true` and `ignoreDuringBuilds: true` — a clean build does not guarantee type correctness
- ESLint config has most rules relaxed
- No test suite exists yet — testing is manual/visual only
- Prisma uses SQLite with a `db/custom.db` file
- The app is currently a scaffold — domain-specific features (incident reporting) have not been built yet
