# EduSync

**EduSync** is an adaptive learning platform with a web client, a REST API, and a machine learning service that powers personalised learning.

**Live demo:** [edusync-black.vercel.app](https://edusync-black.vercel.app)

## Features

- Adaptive learning experience backed by a dedicated ML service
- Secure authentication with JWT and hashed passwords
- Email notifications
- Real-time updates over WebSockets
- Responsive UI with charts and dashboards
- Mobile support via React Native (Expo)
- Automated testing: UI (Selenium, Appium), load, build and vulnerability tests
- CI/CD with GitHub Actions

> TODO: Replace or extend this list with the specific features your users see (e.g. courses, quizzes, progress tracking, roles).

## Architecture

```
┌──────────────┐     REST / WebSocket     ┌───────────────┐      HTTP       ┌──────────────┐
│ pdd-frontend │ ───────────────────────▶ │  pdd-backend  │ ──────────────▶ │  ml-service  │
│ React + Vite │                          │ Express (TS)  │                 │   FastAPI    │
└──────┬───────┘                          └───────┬───────┘                 └──────────────┘
       │                                          │
       └──────────────▶  Supabase  ◀──────────────┘
```

## Tech Stack

| Layer | Technologies |
|-------|--------------|
| Frontend | React 18, TanStack Start / Router / Query, Vite, Tailwind CSS 4, Radix UI, React Hook Form, Zod, Recharts, Expo / React Native |
| Backend | Node.js, Express, TypeScript, JWT, bcryptjs, Nodemailer, node-cache, ws, Axios |
| ML service | Python, FastAPI, Uvicorn, scikit-learn, pandas, NumPy, SciPy, joblib |
| Database / Auth | Supabase |
| Testing | Selenium, Appium, load tests, build tests, vulnerability tests |
| CI/CD / Hosting | GitHub Actions, Vercel |

## Project Structure

```
PDD-EDUSYNC/
├── pdd-frontend/          # Web client (React, TanStack, Vite)
├── pdd-backend/           # REST API (Express + TypeScript)
├── ml-service/            # ML microservice (FastAPI)
├── selenium-tests/        # Web UI end-to-end tests
├── appium-tests/          # Mobile UI tests
├── load-tests/            # Performance / load tests
├── build-tests/           # Build verification tests
├── vulnerability-tests/   # Security tests
└── .github/workflows/     # CI/CD pipelines
```

## Getting Started

### Prerequisites

- Node.js 20+
- Python 3.10+
- A [Supabase](https://supabase.com) project

### 1. Clone the repository

```bash
git clone https://github.com/tejaswireddy7/PDD-EDUSYNC.git
cd PDD-EDUSYNC
```

### 2. Backend

```bash
cd pdd-backend
npm install
cp .env.example .env     # then fill in your values
npm run dev              # development server
```

For production:

```bash
npm run build
npm start
```

### 3. ML service

```bash
cd ml-service
python -m venv venv
source venv/bin/activate          # Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

> TODO: Confirm the entry point (`main:app`) and port match your code.

### 4. Frontend

```bash
cd pdd-frontend
npm install
npm run dev
```

## Environment Variables

Create a `.env` file in each service that needs one. Never commit real secrets.

> TODO: Replace these with the exact variable names your code reads.

| Variable | Used by | Description |
|----------|---------|-------------|
| `SUPABASE_URL` | Frontend, Backend | Your Supabase project URL |
| `SUPABASE_KEY` | Frontend, Backend | Supabase API key |
| `JWT_SECRET` | Backend | Secret used to sign auth tokens |
| `ML_SERVICE_URL` | Backend | URL of the running ML service |
| `SMTP_*` | Backend | Email (Nodemailer) settings |

## Available Scripts

**Backend (`pdd-backend`)**

| Command | Description |
|---------|-------------|
| `npm run dev` | Start the dev server with ts-node |
| `npm run build` | Compile TypeScript to `dist/` |
| `npm start` | Run the compiled server |
| `npm run lint` | Lint the source with ESLint |
| `npm run format` | Format the source with Prettier |

**Frontend (`pdd-frontend`)**

| Command | Description |
|---------|-------------|
| `npm run dev` | Start the Vite dev server |
| `npm run build` | Create a production build |
| `npm run preview` | Preview the production build |
| `npm run lint` | Lint with ESLint |
| `npm run format` | Format with Prettier |

## Testing

The repository includes several test suites, each in its own folder:

- `selenium-tests/`: web UI end-to-end tests
- `appium-tests/`: mobile UI tests
- `load-tests/`: performance and load testing
- `build-tests/`: build verification
- `vulnerability-tests/`: security checks

> TODO: Add the command to run each suite (e.g. `npm test`, `pytest`, `k6 run ...`).

## CI/CD

GitHub Actions workflows in `.github/workflows/` automate checks on the repository. The frontend is deployed on Vercel.

> TODO: Briefly describe what each workflow does (build, test, deploy).

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push the branch: `git push origin feature/your-feature`
5. Open a pull request

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

> TODO: Add a `LICENSE` file to the repo if you don't have one.

## Author

**Tejaswi Reddy** ([@tejaswireddy7](https://github.com/tejaswireddy7))
