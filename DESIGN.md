---
name: Rifqoi
description: A compact engineer's field notebook for SRE work and learning.
colors:
  primary: "#ffffff"
  neutral-bg: "#111111"
  graphite-surface: "#23262d"
  neutral-copy: "var(--color-gray-300)"
  neutral-muted: "var(--color-gray-400)"
  neutral-subtle: "var(--color-gray-500)"
  divider: "rgb(60,60,70)"
typography:
  display:
    fontFamily: "Nunito Variable, system-ui, sans-serif"
    fontSize: "1.875rem"
    fontWeight: 700
    lineHeight: 1.2
  title:
    fontFamily: "Nunito Variable, system-ui, sans-serif"
    fontSize: "1.25rem"
    fontWeight: 700
  body:
    fontFamily: "Nunito Variable, system-ui, sans-serif"
    fontSize: "1rem"
    fontWeight: 400
    lineHeight: 1.75
  label:
    fontFamily: "IBM Plex Mono, ui-monospace, monospace"
    fontSize: "1rem"
    fontWeight: 700
rounded:
  tight: "2px"
  prose: "8px"
spacing:
  sm: "8px"
  md: "16px"
  lg: "28px"
  xl: "32px"
  2xl: "48px"
components:
  navigation:
    typography: "{typography.label}"
    textColor: "{colors.primary}"
    padding: "0"
  project-summary:
    typography: "{typography.body}"
    textColor: "{colors.neutral-copy}"
    padding: "0"
---

# Design System: Rifqoi

## Overview

**Creative North Star: "A compact engineer's field notebook"**

The site pairs a near-black reading canvas with clear white headings, gray body copy, and a restrained graphite note in one isolated card utility. Nunito Variable carries most text; IBM Plex Mono marks navigation and article headings. The mood is understated, technical, and approachable, with a personal voice.

Internal pages use a narrow single column and let text carry the content. The homepage uses a compact two-column introduction on wider screens and stacks it on smaller screens. On internal routes, navigation sits beside the identity on wider screens and moves below it at smaller sizes. Motion is limited to subtle route fades and link color changes.

**Key Characteristics:**
- Dark, neutral canvas with a white and gray text hierarchy.
- Compact, text-led content with mono navigation cues.
- Active pages stay flat and unboxed.

## Colors

The active routes use a near-black base and a neutral gray scale; color is reserved for text emphasis and supplied identity marks.

### Primary
- **Soft White** (`{colors.primary}`): Headings, active navigation, emphasized links, and icons.

### Neutral
- **Near-Black Ink** (`{colors.neutral-bg}`): The page canvas.
- **Cool Graphite** (`{colors.graphite-surface}`): Background in the isolated `Card.astro` utility; current routes do not use this filled surface.
- **Reading Gray** (`{colors.neutral-copy}`): Body and project description copy.
- **Muted Gray** (`{colors.neutral-muted}`): Secondary identity text and inactive links.
- **Quiet Gray** (`{colors.neutral-subtle}`): Post dates and other lower-priority metadata.
- **Divider Gray** (`{colors.divider}`): Horizontal rules in article prose.

## Typography

**Display Font:** Nunito Variable (with system UI sans-serif fallback)
**Body Font:** Nunito Variable (with system UI sans-serif fallback)
**Label/Mono Font:** IBM Plex Mono (with the system monospace fallback)

**Character:** Rounded, readable sans-serif text keeps the personal writing approachable. The monospace face gives navigation and article headings a quiet technical cue.

### Hierarchy
- **Display** (700, 1.875rem / 30px, 1.2): Main page headings; the homepage scales to 2.25rem / 36px on wider screens.
- **Title** (700, 1.25rem / 20px): Project names and secondary headings.
- **Body** (400, 1rem / 16px, 1.625 on the homepage and 1.75 in article prose): Profile and project descriptions.
- **Label** (700, 1rem / 16px): Navigation in IBM Plex Mono; homepage destination labels use the same face at 1rem.

**The Two-Face Rule.** Keep Nunito Variable for reading and identity text; reserve IBM Plex Mono for navigation and article-heading cues.

## Layout

The shared shell centers content within a 700px maximum width. It uses 32px horizontal padding on small screens and 16px from the `md` breakpoint upward; top padding is 40px on small screens and 48px at `md`. The shared header stacks identity and navigation on smaller screens, then places them in one row at `md`. Internal pages use one column. The homepage uses a two-column introduction at `md`, a 65ch maximum text measure, and a compact rhythm between groups. Its content-sized layout places the footer directly after the introduction and destinations. Other pages retain their existing min-height layout, which keeps the footer at the bottom on short pages. Post rows use a fixed date column beside each title.

## Elevation & Depth

The active routes use no shadows or raised panels. Whitespace, type size, and a dashed footer divider establish hierarchy. The source also contains an isolated, currently unused card utility with a subtle inset outline; it does not define the active page surfaces.

**The Flat-Page Rule.** Keep current page content on the canvas; do not promote the unused card utility into a default container pattern.

## Shapes

The main page layout is square and unboxed. Rounded corners appear in article media and code blocks (8px); inline code uses a tighter corner. The footer uses a dashed top divider rather than a boxed boundary.

## Components

### Navigation
- **Style:** Text-only links in IBM Plex Mono, arranged in a compact horizontal row on wider screens and below the identity on smaller screens.
- **Home:** The logo marks the current page; the Projects and Posts routes are offered beside the introduction instead of duplicated in the header.
- **State:** The current route is white and announced with `aria-current`; inactive links use muted gray. Links have visible keyboard focus and a short color transition.

### Home Introduction
- **Style:** A first-person statement of interest in why systems fail and how to keep them running, followed by current Kubernetes and Nix interests, earlier data and machine-learning experience, a brief work detail at IOH, and the site's role as a learning log and English-writing practice. Employer and technology links are subdued and stay in the current tab.
- **Navigation:** “Start here” sits beside the introduction on wider screens and below it on narrow screens. Projects and Posts are unboxed links with short descriptions, ordered consistently with the shared navigation on other routes.
- **Spacing:** Copy forms a compact vertical group. The destination links follow directly in reading order; the homepage footer follows the content instead of being pushed to the viewport edge.

### Project Summaries
- **Style:** Unboxed text groups with a bold white project name, gray description, and an optional inline external link with a small link icon.
- **Spacing:** Entries are separated vertically; no card background or shadow is used on the Projects page.

### Post List
- **Style:** A compact two-column row, with a subdued date at left and the post title at right.
- **Behavior:** Post titles and dates use shared transition names when navigating into an article.

### Footer
- **Style:** Copyright at left and GitHub, LinkedIn, and email links at right, separated from the page by a dashed neutral divider.
- **State:** Links transition from gray to white on hover, expose visible keyboard focus, and use the current tab.

### Article Prose
- **Style:** Nunito body copy with justified paragraphs; mono headings; rounded code blocks and images; gray horizontal rules.

## Do's and Don'ts

### Do:
- **Do** keep content centered within the existing 700px maximum width.
- **Do** use the neutral gray scale for secondary text and white for clear emphasis.
- **Do** recommend straightforward implementations and preserve the site's simplicity.
- **Do** keep project summaries unboxed in the active Projects layout.

### Don't:
- **Don't** make raised shadows or filled cards the default page treatment; the active routes are flat.
- **Don't** treat company or technology logo colors as part of the site's neutral palette.
