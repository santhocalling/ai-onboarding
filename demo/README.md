# AI-Powered Employee Onboarding – Demo

A clickable prototype built around the deck: **JOIN → LEARN → ENGAGE → CONFIRM**.
Its tagline is "Guided by AI. Decided by people."

## Run
Double-click `index.html`. It works offline and has no dependencies.

## Sign in
The demo opens on a login page. Each account only sees its own view; there is no role switch.

| Username | Password | View |
|---|---|---|
| `priya` | `demo` | Employee (Priya Sharma) |
| `daniel` | `demo` | Manager (Daniel Kim) |
| `anna` | `demo` | HR (Anna Müller) |

Or click one of the demo account cards under the form. Use **Sign out** (top right) to switch person. Progress is kept while the tab stays open, so actions in one view appear in the others. Reloading the page keeps you signed in but resets the demo data.

## 5-minute demo script
0. **Optional opener – HR configuration** (sign in as `anna`): in **Onboarding configuration**, change the probation period from 90 to **180 days**. The AI impact preview shows the moved review dates and the new check-in plan. Click **Save configuration**. Every view, the timeline and the assistant now use 180 days. Then sign out and sign in as `priya`.
1. **Problem (slide 2):** Onboarding information is spread across HR systems, email, documents and spreadsheets.
2. **JOIN:** Click **Generate with AI**. The checklist builds itself from the employee's role, department and location. Tick a few tasks and watch the KPIs and progress bars update. Use **Next: LEARN →** at the bottom to move through the stages.
3. **Assistant (right):** Click the suggested questions or type your own:
   - "What should I do next?" gives a live answer based on the current checklist.
   - "I need BIS access" creates a blocker routed to IT.
   - "How long is my probation?" answers from the HR configuration.
   - Unknown questions get escalated to HR.
4. **LEARN:** Complete the compliance items (the Compliance KPI reaches 100%) and show the matched contacts and documents.
5. **ENGAGE:** Fill in the check-in (mood, four 1–5 ratings, workload, three questions; it is pre-filled) and click **Analyze & submit**. The AI shows sentiment, engagement risk, ratings, themes with quoted evidence, routed blockers, suggested manager actions and a follow-up question. Written comments stay private unless Priya ticks "Share".
6. **Manager view** (**Sign out**, then sign in as `daniel`): Daniel sees his team and a "Needs your action" list. In ENGAGE he can add AI-suggested actions to his 1:1 agenda. In CONFIRM he clicks **Generate AI review**. The draft has a recommendation with confidence, live evidence, summary, strengths, development areas, risks and goals. **Everything is editable**: change the recommendation, rewrite text, add or remove points, add his own assessment. The tag changes from "AI draft" to "Edited by Daniel Kim". He then clicks **Approve & send to HR** or **Extend probation** (30/60/90 days).
7. **HR view** (sign in as `anna`): Anna sees the manager's final (edited) review read-only, all new hires, the escalated questions and the **HR sign-off** button. Sign-off rules follow the HR configuration.
8. **Back to Employee** (sign in as `priya`): Priya sees the final status ("probation confirmed" or the new review date). Tip: before the demo, ask the employee assistant "Can I work from abroad?". The question then shows up in HR's escalation inbox.
9. **Roadmap (slide 6):** Explain that this MVP covers the six core capabilities, and that document intelligence and AI agents come next.

### HR configuration options
| Setting | Options | Effect |
|---|---|---|
| Probation period | 60 / 90 / 120 / 180 days | Review dates, "Day X of N", timeline, pipeline status, assistant answers |
| Default extension | 30 / 60 / 90 days | Pre-selected when the manager extends |
| Manager reminder | 7 / 14 / 30 days before end | Marks other hires as "Review due soon" / "Review overdue" |
| Check-in cadence | Week 1 + 3 milestones, or every 30 days | Check-in timeline and AI follow-up question |
| Private comments | on / off | Whether employees can hide written check-in comments from the manager |
| HR sign-off required | on / off | Off: manager approval confirms probation directly |
| Block sign-off on incomplete compliance | on / off | HR sign-off button locked until mandatory training is 100% |
| Mandatory trainings | per training | Compliance % and "Mandatory" labels |

Each save shows an AI impact preview first, then creates a new policy version in the change history and notifies managers and new joiners (simulated).

### Who can do what
| | Employee | Manager | HR |
|---|---|---|---|
| Tick own tasks / compliance | ✔ | read-only | read-only |
| Submit feedback check-in | ✔ | sees AI summary (+ comments if shared) | sees AI summary |
| Resolve blockers | – | ✔ | ✔ |
| Generate & edit AI review, decide | sees status | ✔ | reads final review |
| Final sign-off | – | – | ✔ (if required by policy) |
| Answer escalated questions | – | – | ✔ |
| Change onboarding configuration | – | – | ✔ |

## Limitations
- The login is simulated (fixed demo accounts in the page). It is not real security; anyone who reads the file can see the accounts.
- All data is simulated. The AI responses use rules and keyword matching (`kb` and `themeRules` in `index.html`).
- "Real-time" means the UI reacts instantly with streaming chat, a live activity feed and animated KPIs. It is not connected to any backend.
- The design tokens come from the seeburger.com stylesheet: red `#e10a0a`/`#b90f0f`, orange accent `#ff5f1e`, cyan, the grey shades and the Source Sans font, with square corners. The font loads from Google Fonts and falls back to Segoe UI when offline. The SEEBURGER name is shown as plain text. No logo or images were copied.
- To use a real LLM, replace the `askAI()` function with a call to a backend (for example Azure OpenAI with your policy documents). Never put API keys in the browser.

