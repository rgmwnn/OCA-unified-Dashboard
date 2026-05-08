# OCA Internal Performance Dashboard

A static internal analytics dashboard mockup for **Unified Channel Performance Reporting**, developed as part of the **RevoU x Telkom Indonesia Virtual Internship** project.

This dashboard is designed to help internal stakeholders monitor OCA’s multi-channel communication performance across **WhatsApp, SMS, Email, and Call/IVR** in one centralized view.

---

## Project Overview

OCA is a B2B omnichannel communication platform that helps companies send and manage customer communications through multiple channels, including WhatsApp, SMS, Email, and Call/IVR.

The main business problem addressed in this project is that each communication channel may be monitored separately, making it difficult to compare performance across channels, detect delivery issues, monitor billable activity, and identify user-level risks or opportunities.

This dashboard mockup provides a unified monitoring view to support regular decision-making for Management, Product, Operations, Campaign, and Account Management teams.

---

## Business Problem

OCA’s revenue depends on successful and billable message delivery. However, fragmented channel reporting can make it difficult to answer key business questions such as:

- Which channel generates the highest activity and billable value?
- Which channel is the most reliable or risky?
- When does message traffic peak?
- Which users are highly active, declining, or dependent on one channel?
- Where should Product, Operations, or Account Managers take action?

---

## Dashboard Objective

The objective of this dashboard is to provide a unified, always-updated internal monitoring tool that tracks:

- Channel activity
- Delivery effectiveness
- Charge and billable performance
- Time-based traffic patterns
- User behavior
- Risk and opportunity signals

The dashboard is designed as an action-oriented monitoring tool, not a one-time static report.

---

## Key Features

### 1. Executive Overview

Provides a high-level summary of cross-channel performance through KPI cards and executive insight notes.

Main KPIs include:

- Total Transactions
- Total Message Units
- Active Users
- Success Rate
- Charge Rate
- Billable Amount

---

### 2. Channel Performance

Compares WhatsApp, SMS, Email, and Call/IVR based on:

- Transaction share
- Billable amount
- Success rate
- Failed rate
- Pending rate
- RNA rate for Call/IVR

This section helps stakeholders evaluate channel performance beyond basic transaction volume.

---

### 3. Time Pattern Monitoring

Identifies traffic behavior across dates, days, and hours.

This section includes:

- Daily transaction trend
- Peak traffic by day and hour
- Campaign timing and operational load insights

---

### 4. User Monitoring

Tracks user-level behavior to identify:

- Top users
- High-value users
- Declining users
- Mono-channel dependency
- Upsell opportunity candidates

This section is intended to support Account Managers in prioritizing client follow-up.

---

### 5. Risk & Opportunity Center

Highlights operational and business risks through alert-style monitoring.

Example alerts include:

- Delivery Drop Alert
- High RNA Rate
- User Inactive 14 Days
- Mono-Channel Dependency
- Email Processed Spike

Each alert includes severity, status, suggested action, and responsible owner.

---

## Selected Metrics

| Metric Area | Metrics |
|---|---|
| Activity | Total Transactions, Total Message Units, Active Users, Active Days |
| Delivery Effectiveness | Success Rate, Failed Rate, Pending Rate, RNA Rate |
| Monetization | Charged Transactions, Charge Rate, Billable Amount, Billable Amount Share |
| User Behavior | Top Users, Main Channel Share, Mono-Channel Dependency, Declining User Signal |
| Time Pattern | Daily Trend, Hourly Trend, Peak Day/Hour |
| Risk & Opportunity | Delivery Drop Alert, Inactive User Alert, Upsell Opportunity Signal |

---

## Important Metric Notes

### Transaction Count vs Message Units

For SMS, one transaction can contain multiple SMS parts. Therefore, the dashboard separates:

- **Total Transactions** = number of transaction records
- **Total Message Units** = actual message volume, using `SUM(total_sms)` for SMS

This avoids underestimating SMS activity.

### Raw Amount vs Billable Amount

Raw transaction amount should not be directly treated as revenue because some non-charged records may still contain price values.

The dashboard prioritizes:

```sql
Billable Amount = SUM(transaction_amount WHERE charge = TRUE)
