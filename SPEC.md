# SFIA Skill Evaluator App Specification

## Project Overview

**Project Name:** SFIA Skill Evaluator  
**Type:** Web Application  
**Core Functionality:** A skills assessment tool that connects to users' social accounts (GitHub, Medium, etc.), scrapes publicly available content to analyze skills, and assigns proficiency levels based on the SFIA (Skills Framework for the Information Age) framework.  
**Target Users:** Professionals seeking to validate their skills through their public work portfolio, recruiters assessing candidate skills, and individuals planning career development.

---

## UI/UX Specification

### Layout Structure

**Page Sections:**
1. **Header** - Logo, navigation, user profile dropdown
2. **Hero Section** - Welcome message, quick stats, CTA to connect accounts
3. **Connected Accounts** - Grid of connected social platforms with status indicators
4. **Skill Evaluation Dashboard** - Main area showing skill proficiency levels
5. **Data Sources Panel** - Collapsible panel listing all sources used for evaluation
6. **Footer** - Links, copyright, privacy policy

**Grid/Flex Layout:**
- CSS Grid for main layout (sidebar + content)
- Flexbox for component alignment
- Card-based design for accounts and skills

**Responsive Breakpoints:**
- Mobile: < 768px (single column, stacked cards)
- Tablet: 768px - 1024px (2 column grid)
- Desktop: > 1024px (full layout with sidebar)

### Visual Design

**Color Palette:**
- Background: `#0D0D0D` (deep black)
- Surface: `#1A1A1A` (card backgrounds)
- Surface Elevated: `#252525` (hover states)
- Primary: `#00D9FF` (cyan accent)
- Secondary: `#FF3366` (pink accent)
- Tertiary: `#7B61FF` (purple accent)
- Success: `#00FF88` (green)
- Warning: `#FFB800` (amber)
- Error: `#FF4444` (red)
- Text Primary: `#FFFFFF`
- Text Secondary: `#888888`
- Border: `#333333`

**Typography:**
- Headings: "Outfit", sans-serif (weights: 600, 700)
- Body: "DM Sans", sans-serif (weights: 400, 500)
- Monospace: "JetBrains Mono" (for code/technical content)
- H1: 48px, H2: 32px, H3: 24px, H4: 18px
- Body: 16px, Small: 14px, Caption: 12px

**Spacing System:**
- Base unit: 8px
- xs: 4px, sm: 8px, md: 16px, lg: 24px, xl: 32px, 2xl: 48px

**Visual Effects:**
- Card shadows: `0 4px 24px rgba(0, 217, 255, 0.1)`
- Glow effects on primary elements: `0 0 20px rgba(0, 217, 255, 0.3)`
- Glass effect on panels: `backdrop-filter: blur(10px)`
- Borders: 1px solid with subtle gradient

### Components

**1. Account Connection Card**
- Platform icon and name
- Connection status (connected/disconnected/error)
- Last synced timestamp
- Connect/Disconnect button
- States: default, hover (glow), connected (green border), error (red border)

**2. Skill Proficiency Card**
- Skill name and code (e.g., "Machine Learning - MLNG")
- Proficiency level indicator (1-7 scale with visual bar)
- Confidence score percentage
- Expand to show evaluation details
- Color-coded by level (cyan for low, purple for mid, pink for high)

**3. Source Item**
- Platform favicon
- Source title (repo name, article title, etc.)
- URL link
- Relevance score
- Type indicator (code, article, project)

**4. Level Indicator**
- Visual progress bar showing 7 levels
- Current level highlighted
- Level names: Follow → Assist → Apply → Enable → Ensure & Advise → Initiate & Influence → Set Strategy

**5. Navigation Tabs**
- Dashboard, Skills, Sources, Settings
- Active indicator with glow effect

---

## Functionality Specification

### Core Features

**1. Social Account Connection**
- Support for connecting:
  - GitHub (via OAuth or token)
  - Medium (viaOAuth)
  - LinkedIn (via OAuth)
  - Personal Website/Blog (via URL)
- OAuth flow for secure authentication
- Manual token input option
- Connection status tracking

**2. Content Scraping & Data Collection**
- GitHub: Fetch public repositories, commit history, issues, PRs, profiles
- Medium: Fetch published articles, publications, drafts
- Website: Fetch available content, projects
- Rate limiting compliance
- Respect for platform APIs and terms

**3. Skill Evaluation Engine**
- Analyze collected content against SFIA skill definitions
- Key skills to evaluate:
  - Machine Learning (MLNG)
  - Data Science (DASC)
  - Software Engineering (SENG)
  - Data Management (DATM)
  - Artificial Intelligence (AINT)
  - Data Analysis (DTAN)
  - Programming (PROG)
  - Security & Privacy (SCPY)
  - Cloud Computing (CLDC)
  - Digital Mindset (DIGI)
- Level assignment (1-7) based on:
  - Complexity of projects/code
  - Frequency of relevant activities
  - Depth of involvement
  - Leadership indicators
  - Business impact

**4. Data Source Listing**
- Track all sources used for evaluation
- Show relevance score for each source
- Provide direct links to original content
- Export sources as citation list

### User Interactions and Flows

**Flow 1: Initial Setup**
1. User lands on dashboard (empty state)
2. Clicks "Connect Account"
3. Selects platform (GitHub, Medium, etc.)
4. Completes OAuth or enters token
5. System begins scraping (show progress)
6. Skills evaluated and displayed

**Flow 2: Viewing Skills**
1. User views dashboard with skill cards
2. Clicks on skill card to expand
3. Sees detailed evaluation
4. Can view source data for each skill

**Flow 3: Managing Connections**
1. User accesses connected accounts
2. Can disconnect any account
3. Can re-sync to refresh data

### Edge Cases
- No public content available → Show "insufficient data" message
- Rate limited by API → Queue and retry later
- OAuth token expired → Prompt re-authentication
- Platform not available → Show error, allow retry
- Conflicting evaluations → Show confidence score

---

## Technical Architecture

### Frontend
- Single HTML file with embedded CSS and JavaScript
- No build tools required
- Responsive design
- Dark theme with cyan/pink accents

### Data Handling
- Local storage for connected accounts (simulated)
- In-memory data processing
- JSON-based skill definitions

### API Integration
- GitHub REST API (public data)
- Medium RSS/API (public articles)
- Simulated OAuth flow for demo

---

## Acceptance Criteria

1. ✅ Application loads without errors
2. ✅ User can view SFIA framework info
3. ✅ User can "connect" GitHub account (simulated)
4. ✅ User can "connect" Medium account (simulated)
5. ✅ Skill evaluation displays with SFIA levels
6. ✅ All data sources are listed
7. ✅ Responsive on mobile/tablet/desktop
8. ✅ Visual design matches specification
9. ✅ Skills mapped to SFIA framework levels