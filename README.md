# CogniStream — Developer Flow-State & Cognitive Load Analytics

<p align="center">
  <img src="https://img.shields.io/badge/Project-CogniStream-6C63FF?style=for-the-badge" alt="Project"/>
  <img src="https://img.shields.io/badge/Domain-Developer%20Analytics-00A67E?style=for-the-badge" alt="Domain"/>
  <img src="https://img.shields.io/badge/Status-In%20Development-FFA500?style=for-the-badge" alt="Status"/>
  <img src="https://img.shields.io/badge/Analytics-Flow%20State%20%7C%20Cognitive%20Load-8B5CF6?style=for-the-badge" alt="Analytics"/>
</p>

> An analytics platform designed to measure developer flow, interruptions, and cognitive friction by transforming developer activity events into actionable engineering productivity insights.

## 📌 Overview

CogniStream is a developer analytics project focused on understanding **how developers work**, rather than measuring productivity through conventional metrics such as lines of code or tickets closed.

Traditional productivity metrics primarily measure output, but they often fail to capture the friction that developers experience during focused work. CogniStream addresses this gap by analyzing timestamped developer activity and interruption events from sources such as GitHub, Slack, Jira, and IDE activity.

The platform aims to identify:

- Developer focus and flow periods
- Uninterrupted coding sessions
- Context switching events
- Major interruption triggers
- Time lost due to interruptions
- Developer and team-level cognitive friction
- Patterns that can help improve engineering workflows

The project combines data engineering, analytics, and visualization into an end-to-end developer productivity analytics platform.

---

## 🎯 Problem Statement

Engineering productivity is often evaluated using metrics such as:

- Number of commits
- Number of tickets completed
- Lines of code written
- Task completion volume

While these metrics provide useful information about output, they do not explain **how efficiently developers are able to maintain focused work**.

Frequent Slack notifications, task switching, meetings, CI/CD alerts, and other interruptions can break concentration and reduce the amount of time available for deep work.

CogniStream focuses on measuring this hidden productivity cost through **Flow-State Analytics** and **Context-Switching Analysis**.

---

## 💡 Use Case

An Engineering Manager can use CogniStream to understand developer workflow beyond simple activity counts.

For example, instead of only seeing how many commits a team produced, the dashboard can highlight:

> **Context-Switching Tax**

and identify how interruptions affect developers' focused work.

This can help engineering teams understand:

- When developers experience the most interruptions
- Which event sources cause the most disruption
- How much focused work is lost
- Which periods provide the best conditions for deep work
- Where notification or workflow policies can be improved

---

## 🏗️ Project Architecture

```text
Developer Activity Sources
        │
        ├── GitHub
        ├── Jira
        ├── Slack
        └── VS Code / IDE Activity
                │
                ▼
        Apache Airflow
        Data Extraction &
        Workflow Orchestration
                │
                ▼
        Data Processing
        Python + Polars
                │
                ▼
        ClickHouse
        OLAP Event Storage
                │
                ▼
        Analytics Layer
        Flow-State & Friction Metrics
                │
                ▼
        API Layer
        FastAPI
                │
                ▼
        React + Tremor.js
        Analytics Dashboard
```

---

## 🛠️ Technology Stack

### Data Engineering

- **Apache Airflow** — Workflow orchestration and scheduled data extraction
- **ClickHouse** — OLAP database for high-volume timestamped event data

### Data Analytics

- **Python** — Data analysis and processing
- **Polars** — High-performance DataFrame processing
- **SQL** — Analytical querying and metric development

### Backend

- **FastAPI** — Lightweight API layer for serving aggregated analytics

### Visualization

- **React** — Frontend application
- **Tremor.js** — Analytics and dashboard components

### Data Sources

- GitHub
- Slack
- Jira
- VS Code / IDE Activity
- Mock developer activity APIs

---

## 📊 Data Analytics Scope

The Data Analytics component of CogniStream focuses on converting raw developer events into meaningful productivity and cognitive-flow metrics.

### 1. Data Cleaning & Preparation

Raw event data may contain inconsistent timestamps, duplicate records, missing values, different event structures, and multiple activity sources.

The analytics pipeline will focus on:

- Data validation
- Missing-value handling
- Duplicate detection
- Timestamp standardization
- Event-type standardization
- Source normalization
- Developer-level event consolidation

---

### 2. Developer Activity Analysis

Basic activity metrics will be developed to establish a baseline for understanding developer behavior.

Potential metrics include:

- Total events
- Total commits
- Active developers
- IDE activity hours
- Daily developer activity
- Activity by event source
- Activity by time period

---

### 3. Flow-State Analytics

CogniStream focuses on identifying periods where developers can maintain uninterrupted work.

A key analytical concept is the identification of:

**Uninterrupted Flow Blocks**

For example, a qualifying flow block may represent a sustained coding period of **90+ minutes without a Slack interruption**.

The analysis can include:

- Flow block start time
- Flow block end time
- Flow block duration
- Developer
- Number of flow blocks
- Average flow duration
- Longest flow session
- Daily and team-level flow trends

---

### 4. Interruption Analysis

Developer interruptions can be categorized and analyzed to determine their impact on focused work.

Potential interruption sources include:

- Slack notifications
- Messages
- CI/CD alerts
- Jira activity
- Meetings
- Other application or workflow events

The analysis will identify:

- Number of interruptions
- Interruption frequency
- Interruption source
- Time of interruption
- Developer affected
- Average time between interruptions

---

### 5. Context-Switching Analysis

Context switching occurs when developers move away from their current focused activity and begin interacting with another task, tool, or event.

CogniStream will analyze:

- Context switches per developer
- Context switches per day
- Context switches per hour
- Most frequent interruption sources
- High-friction time periods
- Developer-level switching patterns
- Team-level switching patterns

---

## 📈 Key Analytics Metrics

The project will focus on specialized analytics rather than only conventional productivity metrics.

| Metric | Description |
|---|---|
| **Total Activity** | Overall developer activity recorded across event sources |
| **Focus Time** | Estimated time spent in focused development activity |
| **Flow Blocks** | Sustained uninterrupted development sessions |
| **Average Flow Duration** | Average duration of identified flow sessions |
| **Interruption Rate** | Frequency of interruptions during development activity |
| **Context Switches** | Number of detected transitions between activities |
| **Context-Switching Tax** | Estimated productivity cost associated with interruptions and context switching |
| **Flow Score** | Derived measure representing the quality of developer focus |
| **Top Interruption Trigger** | Event source responsible for the highest number of interruptions |

> **Note:** Metric definitions and formulas will be finalized based on the available dataset and validated project requirements.

---

## 🔍 Planned Analytical Questions

CogniStream will help answer questions such as:

1. How much time do developers spend in focused work?
2. How frequently are developers interrupted?
3. What are the major sources of interruptions?
4. Which time periods experience the highest context switching?
5. How many uninterrupted 90+ minute flow sessions occur?
6. Which developers or teams experience the highest interruption rates?
7. How does interruption frequency affect focus time?
8. What are the primary causes of developer friction?
9. Which periods provide the best conditions for deep work?
10. How can engineering teams reduce unnecessary context switching?

---

## 📊 Dashboard Objectives

The final analytics interface is intended to provide an executive-friendly view of developer workflow and cognitive friction.

Planned dashboard areas include:

### Executive Overview

- Active developers
- Total activity
- Total focus hours
- Average flow duration
- Context-switching tax
- Overall flow score

### Flow-State Analysis

- Flow time trends
- Flow block distribution
- Longest flow sessions
- Developer flow comparison

### Interruption Analysis

- Interruptions by source
- Interruptions over time
- Top interruption triggers
- Interruption frequency

### Context-Switching Analysis

- Context switches by developer
- Context-switching trends
- High-friction periods
- Context-switching tax analysis

### Developer / Team Analysis

- Developer-level metrics
- Team-level comparisons
- Focus vs. interruption patterns
- Productivity friction indicators

---

## 👨‍💻 Data Analytics Contribution

The Data Analytics workstream focuses on transforming raw developer activity events into meaningful business and engineering insights.

### Primary Responsibilities

- Data profiling and exploratory analysis
- Data cleaning and validation
- Event standardization
- Developer activity analysis
- Flow-State detection
- Uninterrupted Flow Block analysis
- Interruption analysis
- Context-switching analysis
- KPI and metric development
- Dashboard-ready data preparation
- Analytical documentation
- Business insights and recommendations

---

## 📁 Proposed Analytics Structure

```text
analytics/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_data_profiling.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_exploratory_analysis.ipynb
│   ├── 04_flow_state_analysis.ipynb
│   └── 05_context_switching_analysis.ipynb
│
├── src/
│   ├── cleaning/
│   ├── analytics/
│   └── metrics/
│
├── sql/
│   ├── activity_metrics.sql
│   ├── flow_state.sql
│   └── context_switching.sql
│
└── docs/
    ├── data_dictionary.md
    ├── metric_definitions.md
    └── analytical_insights.md
```

---

## 📌 Expected Outcomes

The completed CogniStream platform is expected to provide:

- A unified analytical view of developer activity
- Reliable event-level data processing
- Flow-State identification
- Uninterrupted work-session analysis
- Context-switching measurement
- Identification of major interruption triggers
- Developer and team-level friction analytics
- Dashboard-ready productivity metrics
- Actionable insights for improving developer experience

---

## 🚀 Future Enhancements

Potential future enhancements include:

- Real-time developer activity monitoring
- Machine-learning-based interruption prediction
- Personalized developer flow recommendations
- Automated anomaly detection
- Notification optimization recommendations
- Advanced team benchmarking
- Historical trend analysis
- Automated alerts for abnormal context-switching patterns

---

## 📚 Project Documentation

Project documentation will be maintained throughout development and will include:

- Data dictionary
- Data-cleaning methodology
- KPI definitions
- Flow-State methodology
- Context-Switching Tax methodology
- SQL queries
- Analytical findings
- Dashboard documentation
- Final business recommendations

---

## 👥 Project Team

**Project:** CogniStream — Developer Flow-State & Cognitive Load Analytics

**Domain:** Engineering Operations / HR-Tech

**Focus Areas:**

- Data Engineering
- Data Analytics
- Developer Productivity
- Cognitive Flow Analytics
- Business Intelligence
- Data Visualization

---

## ⭐ Project Vision

CogniStream aims to move developer productivity analytics beyond **"How much did a developer produce?"** toward a more meaningful question:

> **"How effectively can developers maintain focused work?"**

By analyzing activity patterns, interruptions, and context switching, CogniStream provides a data-driven approach to understanding developer experience and improving engineering workflows.
