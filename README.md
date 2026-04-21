# SAP-Production-Planning-Project
# SAP PP – Production Order Management Simulator

> **A browser-based, faithful simulation of the SAP ECC / S/4HANA Production Planning (PP) module, covering the end-to-end lifecycle of Production Order Management.**

---

##  Project Overview

This project is a comprehensive study and interactive simulator of the **SAP Production Planning (SAP PP)** module, focused on Production Order Management. It was developed as a project submission by **Atul Aaditya (Roll No: 2305369)** and demonstrates — both through documentation and a live HTML simulator — how production orders are created, modified, confirmed, and closed within the SAP ERP ecosystem.

| Field | Details |
|---|---|
| **Module** | SAP Production Planning (SAP PP) |
| **Topic** | Production Order Management |
| **Transaction Codes** | CO01, MD16, CO02, CO15 |
| **Submitted by** | Atul Aaditya |
| **Roll No** | 2305369 |
| **Document Type** | Project Report + Interactive HTML Simulator |

---

##  Problem Statement

In manufacturing organizations, manual tracking and execution of production activities often result in:

- Inability to monitor the full lifecycle of a production order (creation → closure)
- No automated triggering of goods movements during production confirmation
- Lack of synchronization between Bill of Materials (BOM), Routing data, and shop floor execution
- Completed orders polluting MRP, leading to unnecessary procurement signals
- Difficulty in accurate production cost settlement and variance analysis

**SAP PP** addresses these challenges with a centralized, automated framework for managing production orders.

---

##  Features

### Simulator (HTML Frontend)
The `SAP_PP_Simulator.html` file is a single-file, zero-dependency interactive web application that faithfully replicates the look and feel of SAP ECC / R3 GUI. It includes:

- **Authentic SAP GUI aesthetic** — title bar, menu bar, toolbar, transaction code input, status bar
- **Transaction navigation** — enter T-codes directly (CO01, MD16, CO02, CO15, COOIS) or use the menu
- **CO01 – Create Production Order** — multi-step form with material search, BOM/Routing auto-population, quantity & scheduling, and order release
- **MD16 – Display Planned Orders** — filter by MRP controller, list planned orders, convert to production orders
- **CO02 – Change Production Order** — modify quantity, dates, components; apply Technical Completion (TECO)
- **CO15 – Confirm Production Order** — enter yield quantity, review automatic Goods Issue (MT 261) and Goods Receipt (MT 101), post confirmation
- **COOIS – Order List** — view all created orders with status tracking
- **In-browser state management** — all order data persists within the session
- **Status bar feedback** — real-time system messages mirroring SAP behavior

### Documentation (Project Report)
The accompanying `.docx` project report covers:

- Introduction to SAP PP and the role of Production Orders
- Relationship between Planned Orders and Production Orders
- Master data integration: BOM, Routing, Material Master
- Step-by-step procedures with screenshots for all four transaction codes
- Unique architectural points of SAP PP
- Future improvement roadmap

---

##  Transaction Codes Covered

| T-Code | Name | Purpose |
|---|---|---|
| **CO01** | Create Production Order | Manually create and release a production order; BOM and Routing are auto-copied |
| **MD16** | Display / Convert Planned Orders | Convert MRP-generated Planned Orders into executable Production Orders |
| **CO02** | Change Production Order | Modify order quantities, dates, components; apply TECO status |
| **CO15** | Confirm Production Order | Record production completion; auto-post Goods Issue (MT 261) and Goods Receipt (MT 101) |
| **COOIS** | Production Order Information System | View and filter all production orders by status |

---

##  Tech Stack

| Component | Technology | Purpose |
|---|---|---|
| **ERP Platform** | SAP ERP (ECC / S/4HANA) | Core enterprise resource planning system |
| **Module** | SAP PP (Production Planning) | Production scheduling and order management |
| **Frontend Simulator** | HTML5 + CSS3 + Vanilla JavaScript | Browser-based SAP GUI replica (single file, no dependencies) |
| **Planning Engine** | MRP (Material Requirements Planning) | Automatic demand and supply planning |
| **Master Data** | BOM, Routing, Material Master | Foundation data for order creation and costing |
| **Cost Management** | SAP CO (Controlling) | Cost settlement and variance analysis |

---

##  Getting Started

### Running the Simulator

No installation or build step is required.

1. Download `SAP_PP_Simulator.html`
2. Open the file in any modern web browser (Chrome, Firefox, Edge, Safari)
3. The simulator loads instantly — no internet connection required after download

### Navigating the Simulator

- **Via T-Code field**: Type a transaction code (e.g., `CO01`) in the command field at the top and press Enter
- **Via Menu**: Use the menu bar (System → Transactions) to navigate between screens
- **Via Home Dashboard**: Click any transaction tile on the home screen

### Typical Workflow

```
1. CO01  →  Create a Production Order (enter material, plant, quantity → release)
2. MD16  →  Convert MRP Planned Orders to Production Orders (optional path)
3. CO02  →  Modify the Production Order if needed (update quantity, dates)
4. CO15  →  Confirm Production (post Goods Issue + Goods Receipt simultaneously)
5. CO02  →  Apply TECO (Technical Completion) to close the order
6. COOIS →  Review all orders and their statuses
```

---

##  Production Order Lifecycle

```
MRP Run
  └─► Planned Order (MD16)
         └─► Production Order Created (CO01 / MD16 conversion)
                └─► Released → Shop Floor Execution
                       └─► Confirmed (CO15)
                              ├── Goods Issue (MT 261) — components consumed
                              └── Goods Receipt (MT 101) — finished goods posted
                                     └─► TECO Applied (CO02)
                                            ├── Removed from MRP
                                            ├── Reservations deleted
                                            └── CO Variance Analysis enabled
```

---

##  File Structure

```
├── SAP_PP_Simulator.html       # Standalone interactive simulator (open in browser)
└── SAP_PP_Project_Report.docx  # Full project documentation with screenshots
```

---

##  Key Concepts

- **Bill of Materials (BOM)**: Automatically pulled into the production order on creation; defines all components required
- **Routing**: Specifies the sequence of operations and work centers; auto-copied from master data
- **Backflushing**: Components flagged in the Material Master are automatically issued during CO15 confirmation — no manual Goods Issue required
- **TECO (Technical Completion)**: Final status of a production order; blocks further goods movements, removes the order from MRP, and releases component reservations
- **Movement Type 261**: Goods Issue — raw materials consumed from stock
- **Movement Type 101**: Goods Receipt — finished goods posted to unrestricted stock

---

##  Future Improvements

- **SAP S/4HANA Migration** — Fiori UX, simplified data models, predictive MRP (pMRP)
- **IoT Integration** — Machine-triggered automatic order confirmations via sensor signals
- **ML-based Demand Forecasting** — SAP IBP integration for improved planned order accuracy
- **Digital Scheduling Board** — Drag-and-drop visual production scheduling with real-time capacity
- **Automated Exception Handling** — Workflow alerts for failed goods movements during CO15
- **Sustainability Tracking** — Energy, carbon footprint, and waste data per production batch
- **SAP Analytics Cloud Dashboards** — Real-time KPIs: OEE, scrap rates, order cycle times

---

##  Author

**PARTH PATEL**
Roll No: 2305062
SAP PP – Production Order Management Report

---
