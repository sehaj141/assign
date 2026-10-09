# BrightChamps | Demo Attendance & Recovery Desk

**A browser-based operational prototype to identify demo no-show risk, prioritise lead recovery, and support attendance improvement.**

🔗 **Live Demo:**   https://assign-zeta-sage.vercel.app/

## Overview

The Demo Attendance & Recovery Desk is a lightweight operational tool built for the BrightChamps AI Forward Deployed Associate take-home assignment.

The objective is to translate lead funnel analysis into actionable sales operations. Rather than displaying metrics alone, the application helps identify scheduled demos that may require follow-up, inspect scheduling delays, and prepare rescheduling messages for missed demos.

The prototype runs directly in the browser and uses a single HTML file containing HTML, CSS, and JavaScript.

## The Business Problem

Analysis of the supplied case dataset identified demo attendance as a potential area for operational improvement.

| Metric                                                    | Historical observation |
| --------------------------------------------------------- | ---------------------: |
| Total inbound leads                                       |                  5,000 |
| Leads with scheduled demos                                |                  3,229 |
| Demos attended                                            |                  2,060 |
| Demos not attended                                        |                  1,169 |
| Overall demo show-up rate                                 |                 63.80% |
| Demos scheduled more than 48 hours after lead creation    |                  1,285 |
| Show-up rate for demos scheduled within 48 hours          |                 74.95% |
| Show-up rate for demos scheduled more than 48 hours later |                 46.93% |

The data shows that demos scheduled more than 48 hours after lead creation have a substantially lower observed show-up rate.

This motivates the hypothesis that reducing scheduling delays, improving confirmations, and enabling timely rescheduling could improve attendance.

These historical associations do not prove that scheduling delay alone causes no-shows. The proposed intervention requires validation through a measured pilot.

## Key Features

### 1. Dataset Upload

Upload the supplied CSV through the browser's file selector to populate the lead table from the dataset.

The current implementation processes the CSV locally in the browser; it does not require a separate Python server.

### 2. Demo Attendance Overview

The dashboard displays key operational indicators:

* Total scheduled demos in the loaded records.
* Demo show-up rate.
* Number of demos scheduled more than 48 hours after lead creation.
* An illustrative annualised revenue-uplift scenario.

### 3. Lead Filtering and Search

Inspect lead records using:

* Attendance status.
* Scheduling lag greater than 48 hours.
* Geography.
* Representative shift.
* Lead ID search.

These filters are intended to help the sales operations team focus on relevant records.

### 4. Scheduling-Lag Analysis

The application calculates the time between lead creation and demo scheduling:

`Scheduling lag = Demo scheduled timestamp − Lead created timestamp`

The result is expressed in hours and used to flag records with scheduling lag greater than 48 hours.

### 5. Recovery Message Preparation

For a selected lead, the application generates a draft WhatsApp-style rescheduling message containing the lead ID and parent timezone.

The user can copy the prepared message for review and further action.

**Important:** The prototype does not send WhatsApp messages, create actual rescheduling appointments, or write to a CRM. Its current recovery workflow prepares and copies a message; the success alert is a prototype interaction, not evidence of an external CRM update.

## How It Works

1. Open the live application.
2. Upload the BrightChamps case CSV using the dataset selector.
3. Filter the displayed records by attendance status, geography, representative shift, or scheduling lag.
4. Search for a specific lead using its ID.
5. Select the rescheduling action for a lead.
6. Review and copy the generated message.
7. Use the resulting lead-level insights to inform a follow-up or rescheduling workflow.

The initial page includes a small set of demonstration records so the interface can be explored before a dataset is loaded.

## Proposed Operational Intervention

The tool supports a proposed intervention with three components:

**Reduce scheduling delays:** Encourage eligible leads to book demos within 48 hours where suitable slots are available and parent preferences can be accommodated.

**Improve confirmations:** Introduce structured, timezone-aware reminders using existing operational tools.

**Recover missed demos:** Prioritise timely follow-up and rescheduling for leads who miss their scheduled sessions.

The prototype demonstrates selected parts of this workflow. Production messaging automation, scheduling integration, persistent action logging, and CRM synchronisation would require additional implementation.

## Financial Impact Framework

The assignment specifies the following assumptions:

* Revenue per converted customer: ₹60,000.
* Blended marketing cost per lead: ₹900.
* Observation period: approximately two months.

The financial opportunity is estimated using the expected conversion rate of recovered demo attendees:

`Expected incremental conversions = Recovered attendees × Historical conversion probability after joining`

`Estimated incremental revenue = Expected incremental conversions × ₹60,000`

The dashboard's ₹10.37M annualised figure represents the stated base-case revenue-uplift projection from the accompanying analysis. It is not realised revenue, guaranteed recoverable revenue, or profit.

The scenario depends on the number of attendees genuinely recovered and their subsequent conversion behaviour. All financial scenario assumptions should be reconciled with the accompanying decision memo and analysis.

## Measurement Plan

The primary metric is the demo show-up rate:

`Show-up rate = Attended scheduled demos / Total scheduled demos × 100`

The historical baseline is **63.80%**, based on 2,060 attended demos out of 3,229 scheduled demos.

The proposed pilot target is **68.50%**, subject to validation.

Supporting metrics include:

* No-show rate.
* Percentage of demos scheduled within 48 hours.
* Recovery and rescheduling rate.
* Attendance rate of recovered demos.
* Conversion rate after demo completion.
* Follow-up completion and operational adoption.

Where practical, evaluate the intervention using comparable treatment and control groups, with clearly defined cohort eligibility and enough time for outcomes to mature.

## Technology Stack

* **HTML5** — page structure.
* **CSS3** — styling, layout and responsive interface.
* **Vanilla JavaScript** — CSV processing, filtering, scheduling-lag calculations, modal interactions and message preparation.
* **File API** — browser-based CSV file reading.
* **Vercel** — deployment and hosting.

The prototype has no separate Python backend or database in its current implementation.

## Run Locally

No package installation or build step is required for the standalone HTML prototype.

1. Clone the repository:

   ```bash
   git clone <YOUR_GITHUB_REPOSITORY_URL>
   ```

2. Open the repository folder.

3. Open `index.html` in a modern web browser.

4. Upload the case CSV and explore the dashboard.

Alternatively, serve the file through a local static web server.

## Assumptions and Limitations

* The dashboard's initial lead list is demonstration data, not the complete dataset.
* The uploaded CSV is processed in the browser.
* The current CSV parser uses simple comma-separated field splitting; files containing quoted commas or embedded newlines may not be parsed correctly.
* The dashboard currently assumes the source CSV's column order matches the supplied assignment dataset.
* Uploaded data is not persisted to a database.
* The recovery-message action does not send messages or create a real CRM log.
* The displayed annualised revenue-uplift figure is a scenario estimate, not a measured outcome.
* Production use would require stronger CSV validation, robust parsing, persistent action logging, access controls, and appropriate integrations.

## AI Usage Disclosure

AI tools were used to assist with analysis, implementation, documentation, and review. The final submission should identify the tools actually used and distinguish AI-assisted work from functionality and calculations independently verified.

## Author

**Sehaj Preet Kaur**

Software Engineering | Data-Driven Problem Solving
