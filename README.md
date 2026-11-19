# ZenBill / Atrilium — Internal Customer Service MVP

**Live tool:** [https://sarahw6.github.io/zenbill-mvp-tool](https://sarahw6.github.io/zenbill-mvp-tool)

A standalone browser tool for the ZenBill/Atrilium team to use with customers during calls or demos. No login, no server, no install — open the link and go.

---

## What's inside (8 tabs)

| Tab | Purpose |
|-----|---------|
| **1. Bill Intake** | Enter patient info, bill amounts, insurance status, income for FPL check |
| **2. Error Detector** | 12 billing error types with legal rights + savings estimates |
| **3. Dispute Pathway** | Auto-recommends PPDR, No Surprises Act, insurance appeal, charity care, etc. |
| **4. Letter Generator** | 7 complete dispute letters (auto-fills from intake) — copy & send |
| **5. Savings Calculator** | Gross savings, ZenBill fee (20% capped at $1,000), net patient savings + GFE vs. final |
| **6. Case Library (26)** | 15 KFF investigative cases + 11 actual patient bills analyzed with dispute notes |
| **7. GFE / Price Lookup** | 1,653 CPT codes with 2026 Medicare rates, state GPCI-adjusted, hospital charge ranges |
| **8. AI & OCR Guide** | Build roadmap: OCR tools, AI components, data sources, HIPAA requirements, cost per bill |

---

## Data sources embedded

- **CMS 2026 National Physician Fee Schedule** (Oct. release, 1,653 active CPT codes)
- **2026 Geographic Practice Cost Indices (GPCI)** — all 52 states/territories
- **CMS DHS Code List Addendums** 2021–2026 (Stark Law designated health services)
- **15 KFF / ProPublica / investigative journalism** medical billing cases
- **11 actual patient bills** analyzed for billing errors (NYU Langone, Bozeman Health/Nicole Rolet, Yuma Regional Medicare, Froedtert, Erlanger, VCU, Jackson Purchase/Thana McGary, CHLA, Allina, BCBS-TN)
- **MEPS 2024 Hospital Inpatient Survey** structure reference
- **Business model:** 20% of savings, capped at $1,000 per case

---

## How to edit

1. **Clone this repo:**
   ```bash
   git clone https://github.com/sarahw6/zenbill-mvp-tool.git
   cd zenbill-mvp-tool
   ```

2. **Open `index.html`** in any text editor (VS Code recommended)

3. **Key sections to edit** (search by comment):
   - `// DATA` → `const CASES` array — add new cases here
   - `const ERRORS` array — add new billing error types
   - `const CPT_RATES` — Medicare rate data (update quarterly)
   - `const STATE_GPCI` — geographic adjustment factors
   - Letter templates → search `function buildLetter()`
   - Dispute pathways → search `function renderPathways()`
   - Charity care FPL logic → search `function checkFPL()`

4. **Add a new case to the library:**
   ```javascript
   {
     id: "YOUR-ID",
     provider: "Hospital Name (City, State)",
     billed: 5000,
     insurer_paid: 3000,
     balance: 2000,
     service: "Description of services",
     issue_category: "Duplicate charges",  // matches existing categories
     dispute_step: "Step-by-step dispute guidance...",
     title: "Short descriptive title",
     emergency: "Yes",  // "Yes", "No", or "Unknown"
     bill_type: "Hospital ED bill"
   }
   ```

5. **Push and deploy:**
   ```bash
   git add index.html
   git commit -m "Add new case / update letter template / etc."
   git push origin main
   ```
   GitHub Pages auto-deploys on push — live in ~1 minute.

---

## Cofounder access

To give team members edit access:
1. Go to **Settings → Collaborators** on this repo
2. Add GitHub usernames for Munam, Carissa, and other cofounders
3. They can edit directly on GitHub (click the pencil icon on `index.html`) or clone locally

---

## Important notices

- **Legal:** This tool provides billing information and dispute support, not legal advice.
- **HIPAA:** Only use billing information voluntarily shared by patients. Do not store PHI in this tool.
- **CPT codes:** Descriptions are from CMS public fee schedule files. Full CPT code descriptions are copyright AMA — do not redistribute commercially without AMA license.
- **Actual bill cases:** Bills from real patients in the Case Library were voluntarily shared for training purposes. Treat as confidential.

---

## Update schedule

| Data | Source | Update frequency |
|------|--------|-----------------|
| CMS PFS RVU (Medicare rates) | cms.gov/medicare/physician-fee-schedule | Quarterly (Jan, Apr, Jul, Oct) |
| GPCI factors | Same CMS release | Annually |
| DHS Code List | cms.gov/medicare/referrals | Annually (Nov/Dec) |
| FPL thresholds | HHS aspe.hhs.gov | Annually (Feb) |

---

*ZenBill / Atrilium — Internal tool. Not for public distribution.*
