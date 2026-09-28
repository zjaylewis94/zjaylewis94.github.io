# The Archive (zjaylewis94.github.io)

The front door of Zach's library, served at https://zjaylewis94.github.io/.
It's a launcher, not an app: shelves of book spines. Each spine opens a live app
(`kind: "app"`, has a `url`) or points to a Claude project (`kind: "chat"`).
It has no data and no sync.

## The file
- `index.html` is the whole site: a single self-contained file, vanilla JS, no build step. Keep it that way.
- Shelves live in `DEFAULT_BOOKS` in `index.html`. Book fields: `title`, `kind`, `emblem`, `color` (hex), `url`, `h` (spine height px), `lean`.
- "Edit the shelves" saves an override in that browser's localStorage (`archive_books`). That override hides later changes to `DEFAULT_BOOKS` on that device.
- The page is public. Only titles and links go on it, never private content.

## The library (repos)
New repos use underscores (Zach's preference). Older ones keep their names.

| Book | Repo | Status (Sep 27, 2026) |
|---|---|---|
| The Archive (this) | `zjaylewis94.github.io` (public) | Front door |
| Subroutine (planner) | `SUBROUTINE` (public) | Live; its data syncs to the private `subroutine-data` repo |
| Workout Book | `hybrid-warrior` (public) | Live; opens on today's week from `CYCLE_START` |
| Teacher Book | `teacher_book` (public) | Empty (README only) |
| Head Coach Book | `headcoach_book` (public) | Empty |
| Sprints/Hurdle Coach | `sprint-hurdle_coach_book` (public) | Empty; rename to `sprint_hurdle_coach_book` suggested |
| Cook Book | `cook_book` (public) | Empty |
| Codex (Project Genesis) | `codex` (private) | **Codex 2.0 leads**; the original v35 is kept read-only in `reference/`. Pages stays off |
| Planner data | `subroutine-data` (private) | `subroutine_data.json`; per-book to-do lists planned at `books/<id>.json` |
| (retired) | `life-os` (private) | July attempt; don't build on it |

Not yet made: Ramination, Life Admin (private; `lifeadmin_book.html` is in Drive), Sketch Book, and **Steez Bank** (art ideas sorted by medium).

Shelves in Zach's notepad plan: **Educator** (Ramination?, Teacher, Head Coach, Sprints/Hurdle), **Life Admin** (Workout, Cook, Life Admin), **Art Studio** (Steez Bank, Sketch Book), **Genesis** (Codex). Side notes: a consistent theme across books, and a cover page for each.

## Reference material
Google Drive → `The Library/` holds one folder per shelf and one per book, plus a `START HERE` to-do doc. Read a book's folder before building it.
- Source art (PSDs, full-res PNGs) stays in Drive. GitHub rejects files over 100 MB; books get web-size exports only.
- Coaching material is grouped in Drive as `Educator/coaching_book/` (with `head_coach` and `sprint+hurdle_coach` inside), but there are two repos: `headcoach_book` and `sprint-hurdle_coach_book`.
- Before anything from Drive goes into a public repo, check it for student or athlete names.

## How we work
- One repo per book. The app shell is public; anything private (story text, student or athlete names) goes in the private data repo and loads with the user's token.
- Work on a branch and open a PR. The user merges from their phone. Don't push to `main`.
- Say "ready to merge" only when a PR is finished.
- Before opening a PR, check the page in headless Chromium (Playwright is installed) at 390px and 1280px wide, with no page errors.
