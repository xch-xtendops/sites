# WFM & Data transformation — wave roadmap

Target operating model: a shared **center (CoE)** + a **federated delivery edge**, on a shared **capacity-tier** and **service-and-demand** layer, with DE feeding **XOOS** through a Gold-layer data contract.

**How to read this file**
- **Wave** = a phase of the transition.
- **Epic** (e.g. `W0-E1`) = a milestone. Assign tasks to the Epic it lives under.
- `- [ ]` = an assignable subtask. Append metadata as you go, e.g. `— owner: @name · effort: M · deps: W0-E4`.

**Staffing stance for this stage**
- **WFM:** no hiring, no downsizing — reskill and repurpose only *for this stage*. Mandate now spans **human + AI (blended) capacity planning** (see Decisions locked), so reskilling extends into AI-capacity modeling; specialized hires may follow in a later stage.
- **BI:** roughly flat headcount; sized by the workload model, not cut. Ad-hoc account demand and per-account product builds remain; what changes is routing (intake → satellite/pod).
- **Leadership:** **two CoE leads — 1 WFM CoE lead + 1 Data CoE lead.** The WFM lead is repurposed from the WFM bench; the **Data lead is a current DE** (one of the 10-person core, covering DE + Governance + BI).
- **DE:** the one function that grows. Firmed sizing and ramp in `W1-E2`.
- **Program:** **1 Project Manager — net-new hire** across the whole program: prioritization, deduplication, project-charter optimization, and BAU orchestration. Needed from Wave 0.

> **Net-new permanent headcount = 8 Data Engineer hires + 2 for the XOScore pod (net new) + 1 PM.** The core DE team lands at **10** (today's 2 DEs are part of it — one becomes the Data CoE lead — plus 8 new hires). WFM, BI, and Governance are repurpose/reskill. Bronze build is contractors (temporary). Total engineers: **12** (10 core + 2 pod).

---

## Glossary — one vocabulary for the whole plan

- **XO** — the provider company. Sells **XOOS** (platform) and **Services** (WFaaS, DaaS, the data supply — where this plan lives).
- **XOOS** — the AI platform tenants consume. Its own database/frontend/backend are a separate architecture; our edge with it is the Gold-layer data contract.
- **Tenant** — a company that consumes XOOS (XO BPO first; future clients identical). The **hard data-isolation boundary**. Commercial synonym: "client."
- **Account** — a brand/logo a tenant delivers service for (Sonrava, Morgan & Morgan…). The **org federation unit** (one WF POC per account or account-cluster) and a **soft** partition within a tenant. Synonyms: logo, program.
- **Customer** — the end consumer an account serves.

Reads as: *XO provides XOOS to tenants; each tenant runs multiple accounts; each account serves many customers.*

**Two boundaries — do not conflate them:**
- **Data isolation = per tenant** (hard walls; cross-tenant blending needs consent). Within a tenant, accounts share infra and can blend freely.
- **Org federation = per account** (WF POCs and embedded RTA/scheduling sit at the account level).

**Scaling economics:** pipeline work scales with **accounts × sources**; platform + isolation work scales with **tenants**. Cost per account therefore falls as a tenant's account count grows, and onboarding tenant #2 is cheaper per account than tenant #1 (platform already exists; each new tenant only adds a fresh isolation setup).

## Timeframe

- **Start: Mon 27 Jul 2026. Full structure in place: ~Sep 2027 (14 months) — compressed from 18.** Investment is **staged wave by wave** (no ceiling, funded as the need arises). The compression is achieved by front-loading value and running the MVP lane in parallel; the tradeoff is a tight external-ready date (Feb 2027), the highest-risk milestone.
- **WFM skill assumption:** team is treated as already skilled for human + AI (blended) models, so the blended flip is gated only by real AI volume, not by reskilling.

**Committed milestones**
1. XOOS analytics MVP — Warby Parker · **Sep 2026**
2. First WFM CoE iteration · **Nov 2026**
3. XOOS analytics — external-consumption-ready · **Feb 2027**
4. WFMaaS (blended AI + human) enabled · **Feb 2027**
5. Full XOOS onboarding engine · **Jun 2027**
6. Full Data Governance + Data Engineering structure ready · **Sep 2027**

## This is a cadence, not a fixed-end project

The 14-month roadmap stands up a **capability**, not a one-off deliverable. Once the machine exists, WFM + Data run as a permanent **analyze → decide → implement** loop that keeps the data and operational-reporting infrastructure and processes tuned and orchestrated as accounts, KPIs, and the AI mix change. The build sets up the loop; the loop never stops. (This is what the Project Manager below keeps orchestrated.)

---

## Wave 0 — Foundations
*Build the machine and pick tenant zero before touching delivery.*

### W0-E1 — Operating model signed off
Milestone: target org, roles, and reporting lines approved.
- [ ] Draft target org chart for WFM and Data (center + edge + service layer)
- [ ] Document the matrix: operational (solid) line to account CX POC; functional line to CoE (requests, trains, develops, replaces staff)
- [ ] Write the WF POC role definition (level, mandate, operational-to-CX / functional-to-CoE)
- [ ] Define the three capacity-tier rules (dedicated-external / dedicated-internal-critical / shared-flex)
- [ ] Socialize and get sign-off from leadership + account stakeholders

### W0-E2 — CoE leads named
Milestone: the three centers have owners.
- [ ] Assign the WFM CoE lead (Forecasting + Planning)
- [ ] Assign the Data CoE lead (DE + Governance + BI)
- [ ] Both repurposed from the existing bench (Director / Managers / Data Analysis Leads) — not recruited
- [ ] Hire the program Project Manager — net-new (prioritization, dedup, charter, BAU orchestration)
- [ ] Confirm area head (Director) and demand/capacity-management owner (candidate: current Assoc Manager)

### W0-E3 — Tenant zero confirmed
Milestone: legacy BPO set as the proving ground.
- [ ] Confirm legacy BPO as tenant zero and get exec buy-in
- [ ] Select 2–3 anchor accounts for the Wave 1 pilot (candidates: Sonrava, Morgan & Morgan, Conde Nast)
- [ ] Define pilot success criteria and exit gate to Wave 2

### W0-E4 — Workload & intake model built  *(unblocks BI and DE sizing)*
Milestone: a demand-intake + throughput model that produces headcount numbers.
- [ ] Inventory current demand: ad-hoc requests + standard-product implementations per account
- [ ] Define intake, triage, and prioritization process (who routes what, and how)
- [ ] Define throughput assumptions (capacity per analyst/DE by task type)
- [ ] Produce the BI sizing output (validate the "roughly flat" assumption against real demand)
- [ ] Feed the DE inputs (tenants × accounts × sources, templating %, SLA tiers, timeframe) into the DE ramp

### W0-E5 — Baselines & KPI dictionary v0
Milestone: a measurable starting line.
- [ ] Baseline current forecast accuracy per account
- [ ] Baseline current data SLAs / freshness / incident volume
- [ ] Draft KPI / metric dictionary v0 (definitions to be governed later)

### W0-E6 — DE hiring opened
Milestone: platform reqs live.
- [ ] Write hiring specs for platform-weighted senior DEs
- [ ] Open ~2–3 senior reqs (platform core first — see `W1-E2`)
- [ ] Define reskill tracks (BI analyst → analytics engineering; WFM analyst → forecasting → blended human+AI capacity modeling)

---

## Wave 1 — Prove it on anchors
*WFM unbundle + DE platform build on tenant zero (XO BPO) and the anchor accounts.*

> **Parallel lane:** `W1-E5` (MVP end-to-end prototype) kicks off at wave start and runs *alongside* the platform build. It's the reference vertical slice everything else — templates, the semantic layer, XOOS entities — is modeled on. Accept slightly higher early peak headcount here to de-risk everything downstream.

### W1-E1 — Planning CoE operational on anchors
Milestone: forecasting runs centrally for 2–3 anchors.
- [ ] Extract forecasting from embedded analysts on anchor accounts
- [ ] Reskill selected WFM analysts on forecasting methods and tooling
- [ ] Stand up the central forecasting workflow and cadence
- [ ] Define the central-forecast → local-schedule handoff and who owns accuracy
- [ ] Design the forecasting model/data to extend to blended human+AI later (don't build a human-only system you'll rip out)
- [ ] Compare anchor forecast accuracy vs. the W0 baseline

### W1-E2 — DE platform foundation live  *(DE sizing lives here)*
Milestone: multitenant foundation running for tenant zero.
- [ ] Onboard platform hires
- [ ] Build the medallion foundation (bronze → silver → gold) + tenant isolation
- [ ] Set up orchestration, CI/CD, and baseline monitoring
- [ ] Migrate tenant-zero pipelines onto the platform
- [ ] Templatize the pipeline pattern to make later account (and tenant) onboarding cheap

**DE sizing (firmed from known inputs)**

Inputs: 1 tenant today (XO BPO), ~15 accounts, ~5 sources/account ≈ **~75 source→bronze integrations**; bronze bespoke, silver→gold ~55% templated; SLA P0/P1/P2 (business-hours); footprint LATAM + PH ≈ follow-the-sun; ~18-month build.

Four lanes:
- **Platform core** — foundation, isolation, orchestration, security. Fixed, front-loaded: **~2** to establish and run. Scales with *tenants*, not accounts.
- **Pipeline engineering** — source → bronze → silver per account. Scales with *accounts × sources*. Bronze is bespoke = the labor hump. Steady-state maintenance ~1 DE per 4–6 accounts → **~3–4** for 15 accounts; more during the build (or contractors — see below).
- **Analytics engineering / Gold** — silver → gold, XOOS contract, BI marts, KPI customization. Scales with data products/entities: **~1–2** start → **~3**, held down by the semantic layer (`W1-E6`).
- **Reliability / DataOps** — monitoring, on-call, incident. **~2** by Wave 3, split across regions (follow-the-sun is a real cost driver from your footprint), zero before then.

**Ramp:** 2 today → **~5** in W1 → **~8** by W2 → **10** at external-ready. **8 new hires**; today's 2 DEs are part of the 10 (one becomes the Data CoE lead). The XOScore pod's **2 are net new**, on top.
**Immediate defensible ask:** **+2–3 senior, platform-weighted, now** (your 2 DEs can't hold BAU *and* build the foundation; seniors set the patterns that make every later hire productive — hire pipeline-juniors first and they'll build one-offs you rip out).
**Bronze hump (contractor-covered — decided):** the ~75 bespoke bronze builds are roughly a **2-FTE-year one-time hump** in W1–W2, staffed with **contractors** rather than permanent heads so you don't over-staff for a build that ends.

### W1-E3 — First Gold entities to XOOS
Milestone: the data contract is real, not theoretical.
- [ ] Agree the first Gold entities with the XOOS team (operational metrics + WFM planning)
- [ ] Staff the XOOS Gold-entity design inside DE (not a standalone team)
- [ ] Version the contract (schema, freshness, ownership) — anticipate future mix/economics entities for XOOS caps #4/#5
- [ ] Ship the first entities and validate consumption in XOOS

### W1-E4 — WF POC model piloted
Milestone: the federated edge tested on anchors.
- [ ] Stand up WF POCs on anchor accounts
- [ ] Reorganize anchor RTA/scheduling under the POCs and the tier model
- [ ] Capture lessons + adjust the POC role before wider rollout

### W1-E5 — MVP end-to-end prototype (2 accounts)  *(parallel to the platform build, from wave kickoff)*
Milestone: one complete vertical slice — source → bronze → silver → gold → XOOS contract, plus central forecasting and a BI product — working for 2 representative accounts, as the reference everything else is modeled on.
- [ ] MVP accounts: Warby Parker + Morgan & Morgan (both confirmed)
- [ ] Build the full data path end to end for both: source → bronze → silver → gold
- [ ] Wire the Gold slice to the XOOS data contract and validate consumption
- [ ] Run central forecasting end to end for the 2 accounts (feeds `W1-E1`)
- [ ] Ship one BI product on the slice (proves the BI consumption path)
- [ ] Harvest the slice into reusable templates + patterns (feeds `W1-E2` templatization)
- [ ] Prove the KPI / semantic layer on the slice (feeds `W1-E6`)

### W1-E6 — Governed semantic / metrics layer  *(KPI customization; DE + DG jointly)*
Milestone: per-tenant / per-account KPI customization delivered as *configuration on a shared model*, not bespoke pipelines — the "robust, ongoing, guaranteed" property.
- [ ] Design the semantic / metrics layer (definitions live in the KPI dictionary; customization = config)
- [ ] Define the DE ↔ DG ownership split (DG owns definitions; DE owns the layer architecture)
- [ ] Implement on the MVP slice (`W1-E5`) and validate customization for both accounts
- [ ] Set the pattern that keeps analytics-engineering headcount flat as KPIs proliferate

---

## Wave 2 — Scale & govern
*Roll the model to all internal accounts, stand up governance, convert BI.*

### W2-E1 — Federation rolled to all internal accounts
Milestone: POC + tier model everywhere internally.
- [ ] Roll WF POCs and capacity tiers to remaining accounts
- [ ] Move remaining accounts' forecasting to the Planning CoE
- [ ] Retire the old embedded-forecasting arrangement
- [ ] Track RTA load as AI QA / better forecasting land; redeploy freed capacity to reskilling

### W2-E2 — Governance live
Milestone: KPI/MDM/DQ v1 + ownership model in force.
- [ ] Charter the governance function and its remit
- [ ] Publish KPI / metric dictionary v1
- [ ] Stand up Master Data Management (v1 scope)
- [ ] Define and roll out Data Quality rules + monitoring
- [ ] Publish the ownership model: DG CoE owns definitions + enforcement; domain/satellite owns data ownership, stewardship, and updates

### W2-E3 — BI as satellite + CoE
Milestone: BI runs on the intake model.
- [ ] Form the BI satellite pool + on-demand pods from existing analysts
- [ ] Stand up the BI CoE (capability building, recruitment/selection/development, product-design standards)
- [ ] Launch intake + prioritization for account requests and standard-product builds
- [ ] Re-validate BI sizing against live demand from `W0-E4`

### W2-E4 — DE covers all internal accounts
Milestone: pipelines for every internal account.
- [ ] Onboard remaining account pipelines using the templated pattern
- [ ] Grow analytics engineering for the expanding Gold-entity set
- [ ] Expand monitoring/alerting coverage across accounts

### W2-E5 — Blended human + AI capacity planning  *(the mandate expansion; powers XOOS caps #4/#5)*
Milestone: the Planning CoE forecasts and optimizes the human/AI mix, not just human demand — and ships that intelligence to XOOS.
- [ ] Flip from human-first to blended once an account has real AI volume (define the trigger/threshold)
- [ ] Forecast AI-absorbable share by contact type, complexity, and risk
- [ ] Plan the human workforce on the *residual* demand; adjust skill mix toward complex/escalated work
- [ ] Model mix economics (cost per contact: AI vs. human vs. blended) and optimize for cost/quality/SLA
- [ ] Plan AI capacity + the human overflow/safety net (low-confidence and failure fallback)
- [ ] Plan the automation glide path per account (moving-target human forecast during ramp)
- [ ] Ship blended-planning + economics Gold entities to XOOS (caps #4 roadmap, #5 classic-vs-AI)
- [ ] Produce the mix cost-savings/performance analysis that lets the client + solutioning team decide (WFM plans/justifies; it does not decide the mix)

---

## Wave 3 — External-ready
*Commercial-grade hardening for WFaaS + data products + paying tenants.*

### W3-E1 — Multitenancy & security certified
Milestone: a sellable security bar.
- [ ] Harden tenant isolation, access controls, and audit logging
- [ ] Pursue certifications as the market requires (SOC 2 / ISO / data residency)
- [ ] Confirm client-consent model for any shared/cross-tenant modeling

### W3-E2 — Service management live
Milestone: SLA-backed delivery.
- [ ] Stand up service-delivery management (SLA tracking, incident ownership, QBRs)
- [ ] Add reliability / DataOps capacity + on-call
- [ ] Define SLA tiers and escalation / breach-authorization rules

### W3-E3 — Commercial packaging ready
Milestone: WFaaS and data products are offerable.
- [ ] Define WFaaS offering, tiers, and onboarding
- [ ] Define data-product offering, tiers, and onboarding
- [ ] Clarify who owns commercial packaging/selling (your mandate vs. product/sales)

### W3-E4 — External fence funded
Milestone: the ring-fence is real, not a slide.
- [ ] Formalize ring-fenced external capacity
- [ ] Implement the funding model (external funded by external revenue; internal demand costed via chargeback)
- [ ] Finalize and version the Gold-layer data contract + docs

---

## Decisions locked
- **Reporting lines (matrix):** WF POCs + RTA/scheduling report **operationally (solid line) to the account's CX POC**. The **CoE holds the functional line** — it requests/approves the staff, trains, develops, and replaces them. Account owns day-to-day direction; CoE owns the talent lifecycle and professional standards.
- **XOOS data staff: inside DE.** The people designing the Gold-layer entities XOOS consumes sit within DE, not as a standalone team — they ride the shared platform and keep the Gold layer consistent.
- **Governance model: central standards + federated ownership.** The **DG CoE owns metric/KPI definitions and enforcement**; **data ownership, stewardship, and updates live with the domain area / satellite**.
- **Timeframe: 18 months** to external-ready — confirmed.
- **Bronze build: contractor-covered**, not permanent headcount (~2 FTE-year one-time hump).
- **MVP accounts:** Warby Parker (firm) + Morgan & Morgan (tentative).
- **Dedicate-vs-share (scheduling/RTA):** no global rule — decided per account at onboarding, as part of defining that account's setup.
- **WFM mandate: BOTH — human + AI (blended) capacity planning.** WFM owns *planning and quantifying* the human/AI mix (the cost-savings/performance case); the **decision sits with the client + solutioning team**, since AI agents are a service sale. Phased: human-first through W0–W2, blended from `W2-E5`. This makes the WFM CoE the engine behind XOOS caps #4 (agentify roadmap) and #5 (classic vs. AI analytics).
- **Funding: investment, not a revenue line.** Value accrues through XOOS sales; no direct revenue target for this team. Staged wave by wave. Commercial packaging/selling of WFaaS + data products is **out of scope** for this team.
- **MVP accounts:** Warby Parker + Morgan & Morgan — both confirmed.

## Still open / noted dependencies
- [ ] **No centralized WFM platform today** — may need to buy or build. Out of scope for this plan, but a hard dependency for WFM delivery at scale; flag to whoever owns tooling budget.

---
---

# ═ Parallel track — XOScore ═

*A separate side project, run simultaneously with the main plan. Kept as its own simulation: its own timeline and resources, with defined integration points where it can ride the main build rather than duplicate it.*

**What it is:** an objective experience score (XOScore) computed by evaluating interactions **one by one, non-aggregated**, over any interaction source. Two decoupled layers — **Measurement** (AI rates each interaction: score + confidence + evidence + rationale; reusable across brands) and **Aggregation** (dimension scores → composite XOScore, **configurable per brand**, calibrated over time). Early phases are measurement/calibration-heavy (data science + CX SME); DE effort concentrates in the backbone.

**Start:** month **+3 (~Oct 2026)**. Run by a **separate pod** (finding efficiencies via the shared platform/infra, but not folded into the core DE ramp). Runs standalone first, integrating with the main build wherever the timeline allows, then **open-ended** — after P4 it continues in its own analyze → decide → implement cadence, on **milestones tracked separately** from the XOOS / WFM / BI / DE timeline.

## XOScore simulation — timeline & DE

| Phase | Goal | DE deliverable | Dedicated DEs | Milestone (anchored) |
|---|---|---|---|---|
| P0 | Measurement design & gold set | Canonical interaction schema; sample extraction | 0–1 (light) | — |
| P1 | Standalone MVP (score one-by-one, vs. gold set) | 2–3 source adapters; versioned score store | 1 | Validated scores · **~Mar 2027** |
| P2 | Aggregation & brand config | Config/weight store; outcome-data joins for calibration | 1 | Brand-configurable · **~May 2027** |
| P3 | DE backbone (productionize) | Batch + streaming ingestion, connectors, orchestration, observability/drift, re-scoring, cost governance | 2 | Production backbone · **~Aug 2027** |
| P4 | Lifecycle integration | Join-ready keys; lifecycle data pipelines | 2 | Full lifecycle · **~Dec 2027** |

- **Dedicated DE ramp: 1 → 1 → 2 → 2 (strict peak 2).** If platform/backend + MLOps are filed under DE, standalone peak is 3–4 — **avoided by integration** (see below).
- P3 can run ~50% in parallel with P1–P2; P4 depends on external lifecycle data.

## Integration points — enrich the score (and XOOS)
- [ ] **Shared interaction ingestion** — reuse the main build's bronze/silver pipelines instead of building new source adapters.
- [ ] **Join-ready keys via MDM/governance** — align customer / interaction / agent / brand / timestamp to the main semantic layer *before* any join exists.
- [ ] **Outcome signal for calibration** — CSAT / NPS / churn / resolution from the Gold layer, so P2 weights are *learned*, not hand-tuned (faster).
- [ ] **XOScore → XOOS** — the per-interaction/per-brand score becomes a Gold entity feeding XOOS experience analytics (caps #1 monitor, #5 classic-vs-AI).

## Running both simultaneously
- **Separate pod, shared platform:** 2 dedicated DEs as a distinct team — not added to the core DE ramp — reusing the platform, orchestration, and drift monitoring the main build stands up.
- **Complementary by design:** XOScore is DE-light exactly while the main platform is still being built; its DE-heavy backbone (P3) lands *after* the platform is ready to host it — so no contention.
- **Combined DE footprint:** core 10 + XOScore pod 2 (net new) = **12 total** (mid–late 2027).
- **Integration leverage:** because the pod rides our platform, it needs only its **2 DEs** — not the standalone 3–4.
- **Open-ended:** P4 is not a finish line. After lifecycle integration, XOScore continues in its own cadence loop, with its own milestone track separate from the general timeline.
- **Extends past the main plan** into 2027 and beyond, with P4 gated on external lifecycle data.

## XOScore-specific risks & rules
- **Data access is the main schedule driver** (sources, quality, approval lead time) — not the engineering.
- Treat interaction data as **PII from P1**, not a P3 afterthought.
- **Version every scored record** with `rubric_version`, `model_version`, `prompt_version`.
- Plan a **re-scoring strategy** for rubric changes (scores aren't comparable across rubric versions).
