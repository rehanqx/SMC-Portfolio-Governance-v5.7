# 🏛️ Smart Money Concepts V5.7 — Portfolio & Exposure Engine

![Pine Script Version](https://img.shields.io/badge/Pine_Script-v6-blue?style=for-the-badge&logo=tradingview)
![TradingView](https://img.shields.io/badge/TradingView-Indicator-00897B?style=for-the-badge&logo=tradingview)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

An institutional-grade **Smart Money Concepts (SMC) Portfolio Governance & Exposure Engine** written in **Pine Script v6** for TradingView.

V5.7 acts as the apex macro risk controller for the entire SMC Suite. It manages portfolio-wide equity, enforces gross/net directional leverage boundaries, protects cash reserve buffers, and evaluates systemic drawdown risk to issue high-level capital allocation directives (`ALLOW_FULL_ALLOCATION`, `RESTRICT_SCALING`, `SUSPEND_NEW_ALLOCATIONS`).

---

## 🔥 Key Features

* **🏛️ Frozen 8-Module Portfolio Architecture:** Processed systematically through eight specialized internal sub-engines:
  `1. State ➔ 2. Exposure ➔ 3. Allocation ➔ 4. Risk ➔ 5. Diversification ➔ 6. Intelligence ➔ 7. Memory ➔ 8. API`
* **⚖️ Gross & Net Exposure Governance:**
  * **Gross Exposure Control:** Caps total portfolio leverage (`max_gross_exposure_pct`) across long and short positions.
  * **Net Directional Limit:** Prevents directional over-concentration (`max_net_exposure_pct`).
  * **Cash Reserve Buffer:** Reserves a minimum capital buffer (`reserve_capital_buffer`) for liquidity preservation.
* **🚨 Circuit Breaker & Lockout System:** Automatically shifts portfolio states into **LOCKED** or **WARNING** when max drawdown ceilings (`max_portfolio_dd_pct`) or leverage limits are breached.
* **📊 Master Portfolio Dashboard:** On-screen HUD displaying real-time portfolio scores (0–100), net/gross USD exposure, cash reserve availability, systemic risk ratings, and governance directives.
* **🔌 Open Output API:** Standardized variable exports (`export_PortfolioState`, `export_MasterPortfolioScore`, `export_GrossExposure`, `export_AvailableCapital`, `export_PortfolioRecommendation`) engineered specifically for **MetaTrader 5 (MT5) Expert Advisors** and **FIX Gateway Bridges**.

---

## 📊 Dashboard Overview

The built-in master portfolio HUD displays critical macro governance parameters:

| Metric | Description |
| :--- | :--- |
| **Portfolio State Status** | Operational state classification (*STABLE, WARNING, LOCKED*) |
| **Master Portfolio Score** | Aggregate index (0–100) and rating (*Optimal, High Efficiency, Standard*) |
| **Gross Portfolio Exposure**| Real-time combined long + short position value in USD ($) and percentage (%) |
| **Net Directional Exposure**| Real-time net directional bias value in USD ($) and percentage (%) |
| **Available Capital** | Unallocated cash available for new trade deployments |
| **Reserved Cash Buffer** | Guaranteed cash cushion set aside for capital preservation |
| **Systemic Risk Rating** | Macro risk evaluation (*LOW, MODERATE, HIGH, CRITICAL*) |
| **Governance Recommendation**| Directional directive (*ALLOW_FULL_ALLOCATION, RESTRICT_SCALING, SUSPEND*) |

---

## 🛠️ Configuration & Settings

### 1. Portfolio Governance Settings
* `Total Portfolio Equity ($)` *(Default: $100,000.00)*: Base portfolio capital value.
* `Max Portfolio Drawdown Limit (%)` *(Default: 10.0%)*: Maximum allowable portfolio equity drawdown before circuit-breaker lockout.
* `Max Gross Leverage Limit (%)` *(Default: 200.0%)*: Maximum gross position leverage ceiling.
* `Max Net Directional Limit (%)` *(Default: 50.0%)*: Maximum net directional exposure threshold.
* `Reserve Cash Buffer (%)` *(Default: 20.0%)*: Percentage of equity locked as emergency liquidity.

### 2. Visual & Display Standards
* Toggles for On-Chart Portfolio Status Labels and the Master Portfolio Dashboard.
* Color coding for portfolio states: **OPTIMAL** (Green), **WARNING** (Orange), and **LOCKED / CRITICAL** (Red).

---

## 💻 Installation & Usage

1. Open **[TradingView](https://www.tradingview.com)**.
2. Open the **Pine Editor** tab at the bottom of your workspace.
3. Create a new script, clear the default template, and paste the code from `SMC_Portfolio_Engine_v5_7.pine`.
4. Click **Save** and then select **Add to Chart**.

---

## ⚡ Real-Time Alerts Included

Includes native TradingView alert conditions for automated execution and webhooks:
* ⚠️ **Portfolio Warning:** Fires when net exposure or drawdown approaches policy thresholds.
* 🚨 **Portfolio Locked:** Fires immediately when drawdown limits or gross leverage ceilings are breached, halting all new allocations.



---

## 📜 License

This project is open-source and released under the [MIT License](LICENSE).
