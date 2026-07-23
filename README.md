# 🔍 Detecting Fake Influencers Using Multi-Layer Social Media Analysis

## 📌 Executive Summary & Project Overview
In the era of digital marketing, influencer partnerships have become a primary channel for brand promotion and customer acquisition. However, the rise of **fake influencers**—accounts utilizing bots, purchased followers, and automated engagement scripts—poses a major financial threat to businesses. Relying solely on surface-level metrics like follower counts often leads to wasted marketing budgets on unearned reach.

This project introduces a **Multi-Layer Social Media Analytics Framework** to detect fake influencer accounts across **Instagram** and **X (formerly Twitter)**. By systematically investigating user behavior across four distinct analytical layers (Text, Action, Network, and Hyperlink) and evaluating their integrated correlations, this study proves that single-dimensional metrics are insufficient for detection, and demonstrates the necessity of a holistic, multi-layered data framework.

---

## 👥 Project Team 
* **Course:** CCDS-431 Social Web Analytics
* **Team Members:**
  * **Ghala Alward** | 
  * **Rimas Albahkali** 
  * **Milf Alnaqeeb** 
  * **Rimas Almuntashiri** 

---

## 🎯 Business Problem & Research Question

### The Business Challenge
Selecting influencers solely based on follower count creates significant risk:
1. **Financial Loss:** Marketing budgets are allocated to accounts with non-existent or passive reach.
2. **Skewed ROI:** Campaign performance metrics become inflated by bot interactions.
3. **Brand Reputation:** Partnering with accounts spreading spam or suspicious links harms brand trust.

### Research Question
> *"How can businesses effectively detect fake influencers by applying a multi-layer social media analysis framework?"*

---

## 📊 Dataset Description & Preprocessing

The primary dataset was sourced from Kaggle and curated specifically for influencer behavior analysis across social platforms.

* **Total Cleaned Records:** 1,773 accounts (845 for X, 928 for Instagram)
* **Total Features:** 27 behavioral, textual, network, and engagement attributes.
* **Feature Enrichment:** Custom features were engineered, including `sentiment_score`, `sentiment_label`, and filtered text patterns for Natural Language Processing (NLP).
* **Data Hygiene:** Handled missing values, deduplicated entries, and formatted numeric features using Python (`Pandas`).

---

## 🛠️ Multi-Layer Analytical Framework
              ┌─────────────────────────────────────────┐
              │ Multi-Layer Fake Influencer Detection   │
              └────────────────────┬────────────────────┘
                                   │
  ┌────────────────────┬───────────┴───────────┬────────────────────┐
  ▼                    ▼                       ▼                    ▼
┌───────────┐        ┌───────────┐           ┌───────────┐        ┌───────────┐
│Text Layer │        │Action     │           │Network    │        │Hyperlink  │
│           │        │Layer      │           │Layer      │        │Layer      │
└─────┬─────┘        └─────┬─────┘           └─────┬─────┘        └─────┬─────┘
      │                    │                       │                    │
• Sentiment          • Daily Post            • Follower/          • Bio Links
• Spam Rate            Frequency               Following          • Link Security
• WordCloud          • Interaction             Ratio                Analysis
Patterns


### 1. 📝 Text Layer Analysis
* **Focus:** Authenticity of comments, spam rate, and language patterns.
* **Sentiment Analysis:** Analyzed comment sentiment distributions (Positive, Neutral, Negative) on platform X.
* **Spam Rate Analysis:** Evaluated `spam_comments_rate` across real vs. fake status.
* **Text Mining (WordCloud):** Extracted high-frequency n-grams from fake profiles. Frequently recurring terms included *"normal user"*, *"strong followers"*, *"balanced activity"*, *"genuine account"*, and *"spreading links"*, reflecting template-driven text generation.

### 2. ⚡ Action Layer Analysis
* **Focus:** Behavioral engagement and posting consistency.
* **Posting Frequency:** Computed `posts_per_day` on Instagram.
* **Insight:** Real influencers exhibited higher and more consistent daily posting activity (average ~0.36 posts/day) compared to fake accounts (average ~0.29 posts/day).

### 3. 🌐 Network Layer Analysis
* **Focus:** Structural account relationships and follower dynamics.
* **Metric:** Evaluated `follower_following_ratio` on Instagram.
* **Insight:** Real and fake accounts demonstrated surprisingly similar ratio distributions, confirming that network ratios alone cannot serve as a standalone detector.

### 4. 🔗 Hyperlink Layer Analysis
* **Focus:** Bio link security and promotional behavior.
* **Metric:** Checked for `suspicious_links_in_bio`.
* **Insight:** While most accounts had clean profiles, suspicious links appeared in both real and fake accounts, necessitating contextual cross-validation.

### 5. 🔗 Integrated Multi-Layer Correlation Analysis
* Constructed a multi-feature correlation matrix incorporating all four layers (`spam_comments_rate`, `posts_per_day`, `follower_following_ratio`, `suspicious_links_in_bio`, and `sentiment_score`).
* **Core Finding:** Individual feature correlations with `is_fake` were weak (e.g., spam rate at +0.04, posting rate at -0.02). This empirically proves that **single-feature filters fail**, and **multi-layer integration is required** for robust fraud detection.

---

## 📈 Summary of Key Findings & Results

| Analytical Layer | Evaluated Metric | Key Finding / Behavior Observed | Single Indicator Strength |
| :--- | :--- | :--- | :--- |
| **Text Layer** | Sentiment & Spam Rate | Fake accounts show slightly elevated spam rates & repetitive text patterns. | ⚠️ Moderate |
| **Action Layer** | Posts Per Day | Real accounts maintain higher and more consistent daily activity. | ⚠️ Moderate |
| **Network Layer** | Follower/Following Ratio | Real and fake accounts show overlapping distributions; easily gamed by bots. | ❌ Weak |
| **Hyperlink Layer**| Suspicious Links | Suspicious links exist across classes; requires cross-verification. | ❌ Weak |
| **Integrated** | Multi-Layer Matrix | Weak isolated correlations confirm that multi-layered integration is essential. |  ✅ Strong |

---

## 💡 Practical Business Recommendations
1. **Abandon Single-Metric Vetting:** Never hire influencers based solely on follower counts or network ratios.
2. **Implement Multi-Layer Audit Pipelines:** Evaluate candidates holistically across text authenticity, action frequency, network structure, and profile link security.
3. **Automate Fraud Scoring:** Combine features into an integrated machine learning classifier to generate risk scores before signing promotional contracts.

---

## 💻 Tech Stack & Environment
* **Language:** Python 3.x
* **Notebook Environment:** Google Colab / Jupyter Notebook
* **Core Libraries:**
  * `pandas` - Data manipulation and filtering
  * `matplotlib` & `seaborn` - High-resolution statistical data visualization
  * `wordcloud` - Text frequency and pattern visualization
  * `openpyxl` - Excel dataset ingestion

---

## 📂 Repository File Structure
.
├── Project_Code.ipynb                       # Complete Google Colab Python notebook with code & outputs
└── Detecting Fake Influencers_Report1.pdf   # Detailed formal project report


---
