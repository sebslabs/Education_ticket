# EduPass — Seminar Ticketing (frontend demo)

A complete, frontend-only demonstration of a ticketing platform for G.C.E. A/L and O/L seminars in Sri Lanka: a public site, a student dashboard, an organiser dashboard and an admin dashboard.

> **Demo build.** There is no backend. Authentication, payments, QR verification and notifications are simulated in the browser, and every seminar, person and booking is fictional sample data stored in `localStorage`.

## Run it

```bash
npm install
npm run dev        # http://localhost:5173
npm run build      # type-check + production build into dist/
npm run preview    # serve dist/
npm test           # Vitest unit + integration tests
npm run lint       # oxlint
```

## Try the demo

- **Accounts:** open `/select-account` (or *Log in*) and pick **Student**, **Organiser** or **Admin**. Any password with 8+ characters works. Switch roles at any time from the dashboard top bar.
- **Book a ticket:** Explore → seminar → choose tickets → Cart → Checkout → pay with test card `4242 4242 4242 4242` (any future expiry, any CVC). You can choose whether the demo payment succeeds or is declined.
- **Check attendees in:** Organiser → QR check-in → *Simulate scan*, or type a ticket code from the student's *My tickets*.
- **Verification code:** the demo OTP is `246810`.
- **Reset:** Admin → Platform settings → *Reset demo data*.

## Project structure

```
src/
  components/        shared feature components (Navbar, SeminarCard, SeminarBrowser, …)
  components/ui/     design-system primitives (Button, Field, Dialog, DataTable, Charts, Tabs, …)
  contexts/          Data, Auth (simulated), Cart, Favourites, Toast, Theme providers
  data/mock/         fictional seed data + deterministic booking generator
  hooks/             useCatalog, usePersistentState, useTheme, …
  layouts/           Public, Auth and Dashboard layouts, route guard
  pages/public|auth|student|organiser|admin|shared
  styles/            Tailwind v4 theme tokens (light + dark)
  types/             shared TypeScript interfaces
  utils/             formatting, validation, search, analytics, CSV/ICS export
  test/              test setup and app-level integration tests
```

All screens read data through `DataContext` (`useData` / `useCatalog`). To connect a real backend, replace the provider's state and actions with API calls; the page components don't need to change shape.

## Deployment notes

The app uses clean URLs (`BrowserRouter`), so the host must serve `index.html` for unknown paths. `public/_redirects` (Netlify) and `vercel.json` (Vercel) are included. Configure an equivalent rewrite on other hosts.

See `EDUPASS_FRONTEND_COMPLETION_REPORT.md` for the full feature inventory, QA results and backend integration list.
"# Education_ticket" 
