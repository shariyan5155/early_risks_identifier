 # 🎓 Early Academic Risk Triage System (PS-02)

> **Built for Build vs Break 2026 (BvB 2026)**  
> *Track: PS-02 — Education / Student Success*

A client-side, multi-signal early warning engine designed to identify gradual student disengagement weeks before mid-term evaluations or debarment lists occur. Rather than relying on rigid snapshot thresholds or black-box classifiers, this platform synthesizes classroom attendance velocity with assignment timelines using an explainable, 4-layer evaluation matrix.

---

## 📌 Problem Context

In educational institutions, attendance tracking, coursework submissions, and academic logs reside in disconnected silos. By the time an overall attendance average drops below the institutional 75% cutoff or a student appears on a debarment list, it is usually too late for remedial recovery.

### The Challenge
- **Siloed Data:** Independent attendance portals and LMS assignment logs obscure combined patterns.
- **The Snapshot Trap:** Static filters penalize students who suffer temporary illness (acute blips) the same as students who are systematically disengaging.
- **Black-Box Opacity:** Standard ML models output arbitrary risk scores without explainable root causes.

---

## 💡 The Solution: 4-Layer Risk Matrix

Instead of computing `Attendance + Overdue Assignments = Risk`, the system evaluates student trajectories across four distinct layers:

1. **Layer 1 — Current Status:** Baseline snapshot monitoring cumulative regular attendance, practical lab ratios, and overdue deliverables.
2. **Layer 2 — Rolling Velocity ($\Delta v$):** Calculates the rate-of-change over rolling 14-day evaluation windows, catching downward drift (e.g., dropping from 90% to 70%) long before hard minimum cutoffs are breached.
3. **Layer 3 — Temporal Persistence:** Distinguishes acute 3-day medical absences (damped as *Transient Fluctuations*) from sustained multi-week disengagement.
4. **Layer 4 — Cross-Coupling:** Detects when attendance decline correlates directly with missing theory assignments, escalating the student to *Immediate Outreach*.

---

## 🛠️ System Architecture & Workflow

The project is built as a zero-dependency, client-side web application that operates locally via shared browser storage.

Built-in Hackathon Resilience
Zero-Dependency Resilience: Client-side storage ensures no downtime from venue Wi-Fi drops during live presentations.

False-Alarm Damping: Built-in persistence filters isolate single-week drops to prevent overreaction to brief medical leaves.

Client-Side Sanitization: Input guards prevent edge-case zero-division errors or timestamp manipulation past term limits.
