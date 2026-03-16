# DLM-Dashboard-Retail-Focus-Dynamic-Load-Management-OCPP-1.6J

# ⚡ EV DLM Dashboard

A specialized, Real-Time Dynamic Load Management (DLM) dashboard designed specifically for retail environments with integrated EV charging (e.g., HPCL outlets). 

This dashboard visualizes power allocation natively under real-world constraints, proving that dynamic systems can balance vital retail operations, variable solar capabilities, and multi-protocol fast EV charging simultaneously.

## ✨ Key Features

*   **Real-Time DLM Processing:** Continuously calculates $P_{available} = P_{limit} + P_{solar} - P_{retail\_load} - P_{reserve}$.
*   **Retail Priority Mode (Power Boost):** Instantly safeguards retail operations by reserving load and proportionally throttling active EV charging sessions.
*   **HPCL Solar Integration constraint modeling:** Accurately reflects "Special Project" 65kWp capacities and maps expected solar contribution values against Retail vs. AC Slow vs. DC Fast charging needs.
*   **AI Dwell-Time Prioritization:** Features an intelligent PriorityController that detects "Quick-Stop" profiles, dynamically boosting power vectors for high SoC, short-stay users.
*   **Predictive Maintenance Anomaly Detection:** Real-time analysis of session telemetry via an integrated lightweight Autoencoder, alerting operators to unexpected voltage/current deviations.
*   **Client-Side "Zero-Backend" Execution:** Built as an entirely self-contained HTML/JS/CSS artifact utilizing React and Tailwind via CDN. No Node environments, no PIP installs, no Docker configurations required.

## 🛠️ Technology Stack

*   **Frontend Library:** React (via CDN)
*   **Styling:** Tailwind CSS (via CDN)
*   **Icons:** Unicode Native / Native CSS rendering
*   **Logic Processing:** Vanilla JavaScript (ES6) 

## 🚀 Getting Started (Local Development)

Because the entire application is bundled into zero-dependency files, getting started requires exactly zero setup.

1.  Clone this repository or download the ZIP.
2.  Open the `index.html` file natively in any modern web browser (Chrome, Safari, Firefox, Edge).
    - `Right Click index.html > Open With > Google Chrome`
3.  The simulation environment will immediately spring to life!

## 🎮 How to Use the Simulation

The dashboard contains an interactive `Controls` panel to simulate real-world operations at an EV charging site:

1.  **Toggle Solar Power (65kWp):** Simulate connecting the site's solar array. Watch the `Available Power` pool increase and observe the specific grid demand contributions below the toggle.
2.  **Enable Retail Priority:** Emulates a scenario where retail operations experience a sudden critical power need. The DLM formula immediately reserves 30kW for the site and throttles all charging EVs proportionally to avoid blowing the site fuses.
3.  **Simulate Grid Spike:** Triggers an immediate, random surge in baseline retail load, forcing the DLM to recalculate and pull power back from connected vehicles.
4.  **Connect/Disconnect Bays:** Click the `Connect` button on any Available charger to start a simulated session.
5.  **Inject Anomaly:** Triggers a massive spike in telemetry data (voltage/current jumps) on a specific charger. Watch the AI Autoencoder identify the deviation, spike the Anomaly Score, and trigger a `🔴 SYSTEM_ANOMALY` health warning. 
6.  **AI & Event Logs:** Scroll to the bottom to see real-time, pseudo-Postgres tables detailing every single load recalculation and AI decision made during the session.

## 🌐 Deployment (Netlify or GitHub Pages)

This project can be deployed anywhere plain HTML files are supported (which is everywhere). 

**Recommended: Netlify Free Tier**
1. Push this repository to GitHub.
2. Log into [Netlify](https://www.netlify.com/).
3. Click "Add new site" -> "Import an existing project".
4. Connect your GitHub account and select this repository.
5. Leave all build settings blank and click **Deploy Site**.

*No build process or server configurations are needed!*
