<!-- .github/copilot-instructions.md - concise repo-specific guidance for AI coding agents -->

# Copilot instructions for contributors and AI agents

Purpose: give AI agents the minimal, actionable context to be productive in this Vite + React + TypeScript repo.

- Big picture:
  - This is a Vite + React + TypeScript single-page app (client-only). Entry: `src/main.tsx` -> `src/App.tsx`.
  - Routing is React Router (see `src/App.tsx`). Pages live under `src/pages/` (Index, Auth, Demo, Dashboard, Admin, NotFound).
  - UI primitives and shared components are under `src/components/ui/` (shadcn-style components). Landing page compositions are in `src/components/landing/`.
  - `@/*` TypeScript path alias maps to `./src/*` (see `tsconfig.json`). Use `@/` imports when editing.

- Where to look first (quick tour):
  - App bootstrap: `src/main.tsx` and `src/App.tsx` (routing + providers).
  - Pages: `src/pages/` — implement route-level features here.
  - Reusable UI: `src/components/ui/*` — small presentational components follow shadcn patterns.
  - Landing UI: `src/components/landing/*` — assembled sections like `Hero`, `Navbar`, `Footer`.
  - Hooks & utils: `src/hooks/` and `src/lib/utils.ts` for common helpers.

- Important integrations and runtime behavior:
  - React Query (`@tanstack/react-query`) is used globally via `QueryClientProvider` in `App.tsx`.
  - Notifications use two systems: a custom `Toaster` and `sonner` (see `src/components/ui/toaster.tsx` and `src/components/ui/sonner.tsx`). Keep both in mind when adding notifications.
  - Styling: Tailwind CSS configured (`tailwind.config.ts`) with `index.css` importing Tailwind layers.

- Build / dev / install commands (exact):
  - Install deps: `npm install` (also compatible with `bun install` if using Bun).
  - Dev server: `npm run dev` (runs `vite`).
  - Build: `npm run build` and `npm run build:dev` for development-mode build.
  - Preview production build: `npm run preview`.

- Project conventions and patterns:
  - Component naming: kebab/camel filenames under `ui/` (e.g., `button.tsx`, `toast.tsx`) export React components as defaults or named exports following existing files.
  - Small, focused UI primitives live in `components/ui` and should be composed into larger landing pieces in `components/landing`.
  - Keep visual logic in `ui/*` and page wiring in `pages/*`.
  - Use the `@/` alias for imports to avoid long relative paths.

- Editing examples (do this when modifying behavior):
  - To add a new route: add `src/pages/MyPage.tsx` and register `<Route path="/my" element={<MyPage/>} />` in `src/App.tsx`.
  - To add a reusable UI primitive: add `src/components/ui/my-component.tsx` and export it; update any consuming landing page.

- Linting & tests:
  - Lint: `npm run lint` (uses ESLint config in repo root).
  - There are no automated test scripts; do not invent test harnesses — propose them in PRs.

- PR and commit guidance for agents:
  - Keep changes small and focused to a single intent (UI, route, bugfix).
  - Update or add examples under `src/components/landing` when UI changes are made.
  - Prefer non-breaking edits. If you must change APIs (exports or component signatures), update all imports that use them.

- If in doubt:
  - Read `src/App.tsx` and the specific page under `src/pages/` to understand expected props/state.
  - Ask the human maintainer for design intent if the change affects global providers, routing, or query cache behavior.

-- End of file
