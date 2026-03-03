# ATLAS: THE BOOK v5.1 - THE GRIND

A simulation of financial advisory operations with behavioral friction, compliance state machines, and realistic business dynamics.

## 📊 Overview

This interactive simulation demonstrates the complex interplay between:
- **Time Allocation** (Prospecting, Closing, Servicing, COI Networking)
- **Book Optimization** (Required Servicing Baseline, Pareto Cuts)
- **Market Psychology** (VIX Volatility, Client Anxiety)
- **Human Capital** (Staff Satisfaction, Admin/Partner Hiring)
- **Compliance Dynamics** (Trust Scores, Alert Triggers)

## 🎯 Key Mechanics

### The Grind - Required Servicing
Your book now calculates a **Required Servicing Baseline** (~1 hour per $2M in AUM). If your servicing hours fall below this baseline:
- Anxiety spikes exponentially
- Churn risk increases dramatically
- Alerts trigger based on behavior, not just slider values

### COI Trap Dynamics
COI Networking builds dependency but creates revenue extortion risks:
- Dependency > 50% triggers extortion rates up to 50%
- Requires careful balancing of referral networks

### Generational Attrition
After ~8 quarters, books face natural attrition as client patriarchs pass:
- Multi-Gen planning (t_heirs) reduces liquidation risk
- Estate transfers can retain legacy assets

## 🎮 How to Play

1. **Open `index.html`** in your browser
2. **Allocate Time** across 5 categories (max 80 hrs/quarter)
3. **Execute Quarter** to simulate business operations
4. **Respond to Alerts** when behavioral friction triggers compliance warnings
5. **Manage Your Book** through promotions, hiring, and optimization

## 📈 Progression System

| Level | NNA Target | Payout Rate |
|-------|------------|-------------|
| 1     | $6M        | 40%         |
| 2     | $15M       | 42%         |
| 3     | $35M       | 45%         |
| ...   | ...        | ...         |
| 8+    | $400M      | 75%         |

## ⚠️ Game Over Conditions

- **Bankruptcy**: Cash reserves hit zero
- **Termination for Cause**: Trust score critically low + repeated violations

## 🔧 Technical Details

### State Machine Flow
1. `prepare_quarter()` - Market shock, alert evaluation
2. `resolve_alert(choice)` - Behavioral response to compliance warnings  
3. `finalize_quarter()` - Financial calculations, churn, progression

### Fixed Issues from v5.0
- ✅ NaN% CSS issue in level progress bar (added isNaN check)
- ✅ Baseline Required Servicing logic prevents mindless clicking
- ✅ Alert triggers based on behavior, not just slider values
- ✅ Proper temp variable initialization for state hygiene

## 📂 Repository Structure

```
atlas-book-v5.1/
├── index.html          # Main application file
├── README.md           # This documentation
└── .gitignore         # Git ignore rules
```

## 🚀 Testing the Simulation

### Quick Start
1. Clone or download `index.html`
2. Open in any modern browser (Chrome, Firefox, Edge)
3. No server required - pure client-side JavaScript

### Expected Behavior Flow
1. Start with 0 AUM and $25k cash
2. Allocate time to prospecting and closing
3. Watch anxiety build if you neglect servicing baseline
4. Handle alerts when behavioral friction triggers
5. Promote by hitting NNA milestones
6. Hire admin/partner for operational efficiency

## 🛠️ Development Notes

### State Variables
```javascript
state = {
  // Business Metrics
  aum_fee: 0, aum_ins: 0, pipeline: 0,
  
  // Time Allocation (hours)
  t_pros: 0, t_close: 0, t_serv: 0, 
  t_heirs: 0, t_coi: 0,
  
  // Compliance
  trust: 50, anxiety: 10, panic_churn_last_qtr: 0,
  
  // Operations
  has_admin: false, has_partner: false,
  staff_sat: 100, coi_dependency: 0,
};
```

### Mathematical Bounds
- Anxiety: 5-100 range (capped)
- Required Servicing: ~1hr per $2M AUM (adjusted by purge_factor)
- Churn: Base 0.5% + up to 16% panic churn at max anxiety
- Partner Multiplier: Diminishes as book scales (min 1.1x)

## 📄 License

This simulation is provided for educational purposes.
