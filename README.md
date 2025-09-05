# Smart Supply Chain: A Deep-Dive Analysis into Delivery Bottlenecks

### Executive Summary
This project performs a comprehensive root cause analysis on a smart supply chain dataset to investigate a critical business problem: **an overall late delivery rate exceeding 54%**. The analysis transitions from a high-level overview to a granular investigation, revealing that the primary issue is not regional logistics but a **flawed, static scheduling system** that creates unrealistic delivery promises.

Key findings show that each shipping mode fails in a unique, symptomatic way—from the systematically broken "First Class" service to the highly inconsistent "Second Class" service. The project concludes with a multi-phased action plan focused on immediate fixes, rebuilding the core scheduling logic with a predictive model, and establishing long-term monitoring.

---

### 📈 Problem Statement
The company is facing a critical operational challenge with over half of its deliveries failing to meet their scheduled arrival dates. This high rate of failure directly impacts customer satisfaction, increases customer service costs, and damages brand reputation. This project aims to:
1.  Identify the primary drivers of shipping delays.
2.  Quantify the impact of different factors (e.g., shipping mode, destination, internal processes).
3.  Provide data-driven, actionable recommendations to reduce the late delivery rate and improve operational efficiency.

---

### 💾 Dataset
This project utilizes the "Smart Supply Chain" dataset, which contains over 180,000 order records with 50+ features detailing customer, order, product, and logistics information.

* **Source:** [DataCo Smart Supply Chain For Big Data Analysis](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis?select=DataCoSupplyChainDataset.csv)

---

### 🛠️ Tools & Technologies
* **Language:** Python
* **Core Library:** Apache Spark (PySpark) for big data processing and analysis.
* **Libraries:** Pandas for data inspection.

---

### 🔬 Analysis Workflow
The analysis followed a structured, hypothesis-driven approach, moving from a broad scope to specific, targeted investigations.

1.  **Initial Health Check:** The analysis began by calculating the overall late delivery rate, revealing a staggering **54.8%** of orders were late.

2.  **Geographical vs. Systemic Analysis:** An initial hypothesis that delays were caused by specific geographical markets was tested. The analysis showed that all `Market`s performed almost identically poorly, disproving the hypothesis and suggesting a **systemic, global issue**.

2.  **Internal Process Analysis:** A new metric, `days_on_warehouse`, was engineered to measure internal fulfillment time. This revealed a **hidden internal bottleneck**, with warehouse processing times varying unpredictably from 2 to 6 days.

4.  **Deep-Dive into Shipping Modes:** The investigation then pivoted to `Shipping Mode` as the potential root cause, which proved to be the primary driver of inconsistencies. Each mode was analyzed as a separate case:
    * **"First Class":** Uncovered a **systematically broken** process where a 1-day promise consistently met a 2-day reality, causing a ~95% late rate for all fulfilled orders.
    * **"Second Class":** Revealed **extreme inconsistency**, where a rigid 2-day promise failed to account for a widely variable actual delivery time of 2-6 days.
    * **"Same Day":** Identified as a **high-stakes gamble**, operating at maximum capacity with a nearly 50/50 success rate due to an extreme 0-day promise.
    * **"Standard Class":** Paradoxically found to be the **most reliable** service, indicating its scheduling promise was the most realistic.

---

### 💡 Key Findings & Insights
* The primary bottleneck is a **flawed and static scheduling algorithm** that does not account for real-world variables.
* **Premium services are ironically the most unreliable.** "First Class" is virtually guaranteed to be late, and "Same Day" is a coin flip.
* The system's failure is often **by design**, with hard-coded, unrealistic promises (e.g., promising 1-day delivery when the process always takes 2 days).
* **Internal warehouse inefficiency** is a major, previously hidden contributor to overall delivery delays.

---

### 🚀 Recommendations & Roadmap

1.  **Immediate Tactical Fixes:**
    * **"First Class" Service:** Immediately adjust the delivery promise from 1 to 2 days to match actual performance and eliminate the systemic failure rate.
    * **"Same Day" Service:** Implement a strict order cut-off time to convert the service from a 50/50 gamble into a reliable premium option.

2.  **Core Strategic Project: Predictive Scheduling Engine:**
    * **Transition from Static to Dynamic:** Decommission the current ineffective, static "one-size-fits-all" scheduling system.
    * **Build a Predictive Model:** Develop and deploy a machine learning model that generates accurate, dynamic delivery promises for each order based on key drivers (e.g., geographical destination, product category, internal warehouse delays).

3.  **Continuous Improvement Initiatives:**
    * **Warehouse Optimization:** Launch a project to standardize and reduce the high variability in internal fulfillment times (`days_on_warehouse`).
    * **Proactive Monitoring:** Deploy a live performance dashboard to track all shipping KPIs, enabling proactive bottleneck management and ensuring long-term operational excellence.
