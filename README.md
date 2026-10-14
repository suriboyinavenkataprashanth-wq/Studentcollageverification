# CollegeCompass AP 🎓🧭
> **Comprehensive, Modern B.Tech College Discovery & Comparison Platform for Andhra Pradesh, India**

CollegeCompass AP is a production-grade, responsive full-stack web application engineered to guide students completing Intermediate education (10+2 / MPC) and their families in choosing the right engineering college in Andhra Pradesh.

Unlike generic portals that publish unverified claims or obscure ancillary charges, CollegeCompass AP prioritizes **transparent evidence, realistic 4-year total costs, road-accurate travel distance, separated hostel vs private PG records, and honest placement metrics**.

---

## 🌟 Key Modules & Features

### 1. Interactive Homepage & Search
- **Hero Finder**: Search by college name, AP EAPCET code, branch specialization, home city, and annual tuition budget.
- **Popular Branches**: Direct exploration of CSE, AI/ML, Data Science, ECE, IT, EEE, Mech, and Civil cutoffs.
- **Featured Institutions**: AUCE Vizag, JNTUK Kakinada, VR Siddhartha Vijayawada, GVPCE Visakhapatnam, SVUCE Tirupati, RVR & JC Guntur, Vishnu Institute of Technology Bhimavaram, ANITS, and MITS.
- **EAPCET Counselling Roadmap**: 4-step guide explaining candidate registration, HLC certificate verification, web options prioritization, and seat allotment.
- **Verification Explainer & FAQs**: Transparent disclosure on counselling rounds, convenor vs management seats, and JVD eligibility.

### 2. Searchable, Multi-Filter College Directory (`/colleges`)
- Multi-dimensional filters: Engineering Branch, AP District (all 17 districts), Annual Tuition Budget slider, College Type (State University vs Private Autonomous vs Affiliated), NAAC Accreditation grade, and Verification Status.
- Grid and List view toggles, pagination, dynamic sorting (Relevance, Tuition Low-to-High, Rating, Estd Year).
- In-place bookmarking and one-click comparison tray selection.

### 3. Detailed College Profile Page (`/colleges/:id`)
- 9 Interactive Tabs:
  1. **Overview**: Established year, campus acreage, affiliation, contact details, official website link, and live road distance from candidate's home city.
  2. **Courses & Admissions**: Approved intake seats, annual tuition, and historical closing cutoff ranks across reservation categories (`OC_Boys`, `OC_Girls`, `BC_A`, `BC_B`, `SC`, `ST`, `EWS`).
  3. **Fees & 4-Year Outlay**: Interactive visual cost breakdown, annual vs total tuition, caution deposits, exam fees.
  4. **Hostels & PGs**: In-campus official hostels vs nearby private PG accommodation.
  5. **Internships**: Documented past student internships with company, role, stipend, and completion rates.
  6. **Placements**: Batch-wise median CTC, average CTC, peak offers, unique placed students vs total offers, top recruiters, and audited source citations.
  7. **Campus Life**: Laboratories, central library volumes, high-speed Wi-Fi fiber, sports grounds, technical festivals (e.g. STEPCONE, AFOSEC), accessibility, and anti-ragging squad compliance.
  8. **Student Reviews**: Star ratings across 6 dimensions (Teaching, Infrastructure, Hostel, Food, Campus Life, Support) with pros/cons and review submission modal.
  9. **Sources & Audit Trail**: Verifier, date, confidence score, and direct PDF/link references to official notifications.

### 4. Side-by-Side College Comparison Matrix (`/compare`)
- Compare up to 4 colleges simultaneously side-by-side.
- Compares tuition, 4-year total outlays, hostel charges, road distance, travel time, accreditations (NAAC, NBA, NIRF), median salary, highest CTC, and student feedback.
- Print-to-PDF ready layout with `@media print` stylesheet.

### 5. Transparent 4-Year Fee & Outlay Calculator (`/calculator`)
- Choose between **Convenor Quota (Category A)** and **Management Quota (Category B)**.
- Modify living mode: **College Hostel**, **Private PG**, **Day Scholar Bus**, or **Personal Commute**.
- Adjust laptop allowances, academic supplies, and meal expenses.
- Generates **Low (Frugal)**, **Typical (Expected)**, and **High (Conservative)** scenario projections.
- Built-in **Jagananna Vidya Deevena (JVD) Eligibility Checklist** with statutory disclaimer.

### 6. Home-to-College Road Distance & Routing Service
- Uses live **OpenStreetMap / OSRM Driving Engine** API for road distance and driving duration with a local geodesic AP-curvature (1.28x) offline fallback.
- Computes estimated monthly commute costs (APSRTC student bus pass vs personal fuel) vs campus hostel rent to guide the day-scholar vs hostel decision.
- Privacy-compliant: GPS and home locations remain client-side in the browser.

### 7. Separated Hostel & Private PG Finder (`/hostels`)
- Separates official campus hostels (managed by college chief warden) from private student PGs.
- Filter by Boys, Girls, Co-ed, rent ceiling, sharing configurations, and amenities.
- Uninspected sample listings are clearly watermarked with a prominent **DEMO DATA** badge.

### 8. Smart Personalized Recommendation Engine (`/recommendations`)
- Transparent multi-criteria scoring algorithm balancing AP EAPCET rank, reservation category, budget limits, preferred branches, preferred districts, and user priority sliders (Placements, Affordability, Proximity, Campus Life).
- Itemizes admission probability per branch (High Chance, Moderate Chance, Competitive Reach) and explicitly enumerates **Why Recommended (Pros)** and **Trade-offs to Consider**.

### 9. Role-Based Admin Verification Dashboard (`/admin`)
- Switch instantly between **Student**, **Admin**, and **Guest** modes via the top navigation bar.
- Manage colleges master records (create, update, delete with duplicate ID protection).
- Review moderation queue (approve, flag, reject student feedback).
- Manage citizen-reported data inaccuracy tickets.
- Stale data audit tracker (ensuring periodic revision within 180 days).
- Single-click CSV master export and backup tool.

---

## 🛠️ Tech Stack & Architecture

- **Frontend**: React 19, TypeScript, Tailwind CSS v4, Vite 8, Lucide React icons.
- **State Management**: React Context (`AuthContext`, `StudentProfileContext`, `FavoritesContext`, `ComparisonContext`) with browser `localStorage` persistence.
- **Routing**: React Router DOM (v7).
- **Backend / Database**: Supabase PostgreSQL with Row Level Security (RLS) policies (`supabase/migrations/20261014_init_college_compass.sql`).
- **Routing API**: Open Source Routing Machine (OSRM) driving API with offline AP geodesic fallback.
- **Testing**: Node.js & `tsx` unit test runner (`npm test`) validating fee calculations, scholarship eligibility, admission suitability logic, and recommendation ordering.

---

## 🚀 Getting Started

### Prerequisites
- Node.js (v18 or higher recommended; developed on Node v24 LTS)
- npm (v9 or higher)

### Installation

1. Clone or navigate to the repository directory:
   ```bash
   cd c:\Users\surib\Downloads\project1
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. (Optional) Configure environment variables:
   Copy `.env.example` to `.env.local`:
   ```bash
   copy .env.example .env.local
   ```
   > **Note**: If Supabase credentials are not provided, the application automatically runs in full interactive **Demo Mode** with realistic Andhra Pradesh college datasets and persistent local storage.

4. Start the development server:
   ```bash
   npm run dev
   ```
   Open your browser at `http://localhost:5173`.

---

## 🧪 Running Unit Tests

The test suite validates fee calculation engines, scholarship rules, cutoff evaluation, and recommendation scoring:

```bash
npm test
```

Expected output:
```
==================================================
 CollegeCompass AP: Running Engineering Unit Tests
==================================================

✅ PASS: FeeCalculator: AUCE Convenor Quota annual tuition is ₹35,000
✅ PASS: FeeCalculator: AUCE 4-Year tuition is exactly ₹1,40,000
✅ PASS: FeeCalculator: Total 4-year outlay accounts for hostel, mess, and exam fees
✅ PASS: FeeCalculator: Scenario range generates valid low < high estimates
✅ PASS: JVD Scholarship: Income ₹1,80,000 (<= ₹2.5L) is eligible
✅ PASS: JVD Scholarship: Income ₹3,50,000 (> ₹2.5L) is not eligible
✅ PASS: Suitability: Rank 1,000 vs Cutoff 2,000 gives "High Chance"
✅ PASS: Suitability: Rank 2,050 vs Cutoff 2,000 gives "Moderate Chance"
✅ PASS: Suitability: Rank 5,000 vs Cutoff 2,000 gives "Needs Quota / Low Chance"
✅ PASS: RecommendationEngine: Successfully generates non-empty college matches
✅ PASS: RecommendationEngine: Matches are correctly sorted descending by matchScore
✅ PASS: RecommendationEngine: Generates transparent pros explaining why college matched
✅ PASS: DistanceService: Commute cost estimator calculates realistic monthly bus and fuel expenses

--------------------------------------------------
 Summary: 13 Passed, 0 Failed
--------------------------------------------------
✨ All CollegeCompass AP unit tests passed successfully!
```

---

## 🗄️ Database Setup (Supabase)

To link a live PostgreSQL database:
1. Create a project at [supabase.com](https://supabase.com).
2. Open the SQL Editor in your Supabase dashboard.
3. Paste and run the schema migration found in:
   `supabase/migrations/20261014_init_college_compass.sql`
4. Copy your project's URL and anon public key into `.env.local`:
   ```env
   VITE_SUPABASE_URL=https://xyzcompany.supabase.co
   VITE_SUPABASE_ANON_KEY=eyJhbGciOi...
   ```

---

## 🚢 Production Build & Deployment

To compile the optimized production bundle:
```bash
npm run build
```

To preview the production build locally:
```bash
npm run preview
```

### Deploying to Vercel or Netlify
- Build command: `npm run build`
- Output directory: `dist`
- Framework preset: `Vite`
- Single Page App (SPA) redirect rule:
  - For Vercel: included in standard Vite deployment.
  - For Netlify: add a `_redirects` file in `public/` containing `/* /index.html 200`.

---

## ⚖️ Statutory & Product Principles

1. **Accuracy Over Hype**: We never rank a college based on commercial sponsorships or unverified self-proclaimed claims.
2. **Privacy Protection**: We do not require account registration or mobile numbers for searches.
3. **Transparent Outlays**: Every college card and detail tab reflects both the single-year tuition and full 4-year expected living expenses.
