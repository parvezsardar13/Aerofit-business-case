# Aerofit Customer Segmentation & EDA Case Study
*A comprehensive exploratory data analysis of customer demographics, purchasing patterns, and probabilistic profiling to optimize treadmill recommendations.*

## 📌 Badges
`![Python](https://img.shields.io/badge/Python-3.x-blue.svg)` `![Colab](https://img.shields.io/badge/Jupyter-Colab-orange.svg)` `![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458.svg)` `![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-3776AB.svg)`

## 🎯 Project Overview
Aerofit is a leading brand in the field of fitness equipment, providing a product range including treadmills, exercise bikes, gym equipment, and fitness accessories. This case study analyzes customer purchase behavior to identify the distinct target audience characteristics for each treadmill model. By understanding the demographic and behavioral profiles of buyers, Aerofit can enhance its product recommendations and target future marketing campaigns effectively.

## ❓ Business Problem / Objectives
- What are the distinct characteristics of customers who purchase each treadmill model (KP281, KP481, and KP781)?
- How do demographics (age, gender, education, marital status, income) and fitness habits (weekly usage, fitness rating, target miles) influence product selection?
- What are the conditional probabilities of purchasing specific models based on customer segments?
- How can Aerofit better recommend products to new customers and optimize its marketing and upsell strategies?

## 📊 Dataset
- **Source:** [ADD DATASET LINK] (`aerofit_treadmill.csv`)
- **Dimensions:** 180 rows, 9 columns

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| **Product** | Categorical (String) | Model purchased: KP281, KP481, or KP781 |
| **Age** | Integer | Age of the customer in years (range: 18–50) |
| **Gender** | Categorical (String) | Gender of the customer (Male or Female) |
| **Education** | Integer | Total years of education completed (range: 12–21) |
| **MaritalStatus** | Categorical (String) | Relationship status (Single or Partnered) |
| **Usage** | Integer | Planned number of times the customer plans to use the treadmill per week |
| **Fitness** | Integer | Self-rated fitness score on a scale of 1 to 5 |
| **Income** | Integer | Annual income of the customer in USD |
| **Miles** | Integer | Expected weekly mileage target |

## 🧰 Tools & Libraries
- **Python** (Core programming language)
- **Pandas** (Data manipulation and aggregation)
- **NumPy** (Numerical operations and percentile clipping)
- **Matplotlib** (Data visualization and plotting layout)
- **Seaborn** (Statistical data visualization, heatmaps, and distribution plots)

## ⚙️ Methodology
1. **Data Loading & Inspection:** Imported dataset using pandas, verified basic metrics (`head()`, `shape`, `info()`, `nunique()`), and inspected column data types.
2. **Data Type Conversion:** Converted categorical and encoded string columns (`Product`, `Gender`, `MaritalStatus`, `Fitness`) into proper categorical data types.
3. **Missing Value & Duplicate Checks:** Checked for null values and duplicate entries to ensure data integrity.
4. **Outlier Detection & Treatment:** Examined continuous variables (`Age`, `Education`, `Usage`, `Income`, `Miles`, `Fitness`) using descriptive statistics and boxplots, and clipped extreme values between the 5th and 95th percentiles to handle upper-end skewness.
5. **Non-Graphical Analysis:** Computed value counts, proportions, and marginal probabilities across categorical features.
6. **Univariate & Bivariate Analysis:** Generated histograms, countplots, and distribution plots (`displot`, `histplot`, `countplot`) to evaluate feature distributions relative to product tiers.
7. **Correlation Analysis:** Computed the numerical correlation matrix and visualized relationships using a Seaborn heatmap.
8. **Probability Modeling:** Calculated marginal and conditional probabilities (e.g., product purchase probabilities given gender, fitness, and usage) using cross-tabulations.

## 💡 Key Insights & Findings
- **Overall Sales Distribution:** KP281 (entry-level) is the top seller at 44.44% (80 units), followed by KP481 (mid-level) at 33.33% (60 units), and KP781 (premium) at 22.22% (40 units). Entry and mid-level models combined account for ~78% of total sales.
- **Income as the Primary Differentiator:** Annual income strongly separates product tiers; KP281 and KP481 buyers share similar mid-income profiles (medians around $46k–$49k), whereas KP781 buyers earn significantly higher incomes (median ~$75k, range up to $90k+).
- **Severe Gender Skew on Premium Models:** While entry and mid-tier models are nearly gender-neutral, male buyers represent 82.5% of KP781 purchasers (18.33% of total buyers are males who bought the KP781, compared to only 3.89% females). Male customers have a ~31.73% probability of buying the premium model, compared to just 9.21% for females.
- **Fitness & Usage Drive Premium Purchases:** High-frequency runners (5 days/week) have a 100% probability of purchasing the KP781, and customers with a self-reported fitness level of 5 have a 93.55% probability of selecting it.
- **Strong Feature Correlations:** Strong positive correlations exist between Fitness and Miles ($r = 0.83$), Usage and Miles ($r = 0.77$), and Usage and Fitness ($r = 0.66$). Higher income also moderately correlates with education ($r = 0.63$) and fitness/miles ($r \approx 0.54–0.55$).
- **Age is Independent of Intensity:** Age shows virtually no correlation with workout intensity ($r \approx 0.02–0.06$), weekly usage, fitness, or target distance, indicating that older customers purchase treadmills for similar intensity goals as younger buyers.
- **Marital Status Parity:** Marital status shows almost equal distribution across product choices (~59% partnered, ~41% single), making it a weak differentiator for product tier selection.

## 📉 Visualizations
![Age vs Product](images/age-vs-product.png)
*Distribution of customer age across product models, showing nearly identical median age (~26–27 years) across all three tiers.*

![Income vs Product Boxplot](images/income-vs-product.png)
*Boxplot comparison demonstrating that higher annual income is the single strongest financial predictor for purchasing the top-tier KP781 treadmill.*

![Correlation Heatmap](images/correlation-heatmap.png)
*Correlation matrix heatmap highlighting strong positive linear relationships between weekly usage, fitness ratings, and target mileage.*

![Conditional Probability Fitness](images/conditional-prob-fitness.png)
*Conditional probability distribution showing that self-reported fitness levels 4 and 5 concentrate heavily on the premium KP781 model.*

## 📋 Recommendations
1. **Segment Marketing by Income & Fitness:** Focus digital campaigns and ad spend on income brackets and self-reported fitness levels rather than broad demographic variables like age or marital status.
2. **Target Female High-Earners for Premium Models:** With ~80% of KP781 buyers being male, design targeted marketing initiatives to capture high-income, fitness-driven female consumers who represent an untapped market segment.
3. **Position KP481 as an Upsell Target:** Market the mid-tier KP481 as the ideal upgrade path for regular runners currently using entry-level models as their fitness habits progress.
4. **Build a 12–18 Month Lifecycle Upsell Campaign:** Nudge loyal KP281 owners toward higher tiers as their reported fitness level and usage frequency increase over time.
5. **Deprioritize Marital Status in Targeting:** Given that purchase probabilities across single and partnered customers show minimal variation, remove marital status filters from core product recommendation models.

## ⚠️ Limitations & Future Work
- **Small Sample Size:** The dataset contains only 180 observations across three products, which limits the statistical robustness of deep sub-segment inferences.
- **Single Snapshot Data:** The data represents a single cross-sectional snapshot at the time of purchase; there is no longitudinal tracking of repeat purchases, customer churn, or actual usage-over-time to validate upgrade trajectories.
- **Future Work:** Collect multi-year customer usage telemetry data and expand sample sizes to build predictive machine learning classification models for automated in-store and online product recommendations.

## 🚀 How to Run
1. Open the notebook directly in Google Colab using the badge or link: [Open in Colab](https://colab.research.google.com/github/parvezsardar13/Aerofit-business-case/blob/main/Aerofit_Business_Case_study.ipynb)
2. Or clone the repository locally:
   ```bash
   git clone [https://github.com/parvezsardar13/Aerofit-business-case.git](https://github.com/parvezsardar13/Aerofit-business-case.git)
   cd Aerofit-business-case

