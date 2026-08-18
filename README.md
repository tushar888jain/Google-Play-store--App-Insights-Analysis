# App Insights Unlocked

**A Data Analytics Case Study on the Google Play Store**

*Solution Guide & Final Report*

Dataset: Google Play Store Apps (Kaggle) — 9,659 apps, 29,692 user reviews

## Executive Summary

This report analyzes 9,659 Google Play Store apps and 29,692 associated user reviews to identify what drives app success, which categories perform best, and how price, size, and content rating relate to user satisfaction. The dataset was cleaned prior to analysis: a corrupted record was removed, duplicate app entries were dropped, Installs/Price/Size fields were converted from text to numeric values, and missing ratings were imputed using category-level medians.

Key headline findings:

- The average app rating across the store is 4.19 out of 5, and 80% of apps are rated 4.0 or above — the bar for "acceptable" quality on the platform is high.
- Free apps vastly outnumber paid apps (8,903 vs 756, or 92%/8%), and free apps also receive far more reviews on average (234,244 vs 8,725) — installs and engagement, not price, drive review volume.
- Games dominate total installs (13.9B), followed by Communication (11.0B) and Tools (8.0B) — these three categories represent the largest addressable audiences.
- Install volume and rating are barely correlated (r = 0.035) — being popular does not make an app better-rated, and vice versa. Highly-installed apps (10M+) do edge out smaller apps on average rating.
- Paid apps show a small negative correlation between price and rating (r = -0.106) — more expensive apps trend slightly lower-rated.
- Sentiment analysis confirms the rating signal is real: apps rated 4.5+ get 70.5% positive reviews, while apps rated 3.0 or below get only 32.6% positive and 40.9% negative reviews.

## Part 1 — Basic-Level Questions

Finding: The average rating across all 9,659 apps is 4.19 out of 5.

Business Impact: This sets a quality benchmark — new apps should target a 4.2+ rating to be competitive with the market norm.

Finding: There are 33 unique categories in the cleaned dataset.

Business Impact: This breadth shows a highly diverse marketplace; the company should map its own portfolio against underserved categories.

Finding: App size (in MB) ranges from 0.01 MB to 100 MB, with a mean of 20.4 MB, median of 12.0 MB, and 75th percentile of 28.0 MB. (1,227 apps report "Varies with device" and were excluded from this calculation.)

Business Impact: Most successful apps stay well under 30MB — useful for setting internal size budgets and considering low-bandwidth markets.

Finding: 8,903 apps are Free (92.2%) and 756 are Paid (7.8%).

Business Impact: The freemium model dominates the store; a paid-only strategy sharply limits addressable audience.

Finding: "Everyone" is the most common content rating, covering the vast majority of apps.

Business Impact: Broad-audience content remains the safest default positioning for new app development.

| App | Installs |
| --- | --- |
| Instagram | 1,000,000,000+ |
| Google Street View | 1,000,000,000+ |
| Google Play Books | 1,000,000,000+ |
| Subway Surfers | 1,000,000,000+ |
| Google Drive | 1,000,000,000+ |

Business Impact: Category leaders (social, gaming, productivity, and Google-owned utilities) show that trusted brand + broad utility is the winning combination at the very top of the market.

Finding: 7,749 apps (80.2% of the dataset) have a rating of 4.0 or higher.

Business Impact: A 4.0+ rating is table stakes, not a differentiator — competitive apps must clear this bar comfortably.

Finding: Free apps average 234,244 reviews; paid apps average only 8,725 reviews — roughly 27x fewer.

Business Impact: Free apps generate dramatically more user feedback, valuable for iterative product improvement and social proof in store listings.

| Category | Avg. Size (MB) |
| --- | --- |
| Game | 41.87 |
| Family | 27.19 |
| Travel And Local | 24.20 |
| Sports | 24.06 |
| Entertainment | 23.04 |

Business Impact: Games are inherently the heaviest category — infrastructure and CDN planning should weight capacity toward gaming content specifically.

Finding: 6,284 apps (65% of the dataset) were last updated in 2018, the most recent year in the data.

Business Impact: Update recency correlates with active maintenance; the concentration in the most recent year reflects a generally well-maintained marketplace at the time of data collection.

## Part 2 — Medium-Level Questions

Finding: The correlation is r = 0.035 — essentially no linear relationship. Popularity does not predict quality.

Business Impact: Marketing spend to drive installs should not be assumed to improve perceived quality; ratings must be earned through product experience separately.

| Category | Avg. Rating |
| --- | --- |
| Events | 4.46 |
| Books And Reference | 4.38 |
| Education | 4.37 |
| Art And Design | 4.36 |
| Personalization | 4.35 |

Business Impact: Niche, utility-driven categories outperform mass-market ones on satisfaction — a promising space for differentiated, high-quality entrants.

Finding: Correlation between price and rating among paid apps is r = -0.106, a weak negative relationship.

Business Impact: Premium pricing does not guarantee premium perception — pricing strategy should be paired with clearly communicated value, not used alone as a quality signal.

| Content Rating | Avg. Rating |
| --- | --- |
| Adults only 18+ | 4.30 |
| Everyone | 4.19 |
| Everyone 10+ | 4.23 |
| Mature 17+ | 4.13 |
| Teen | 4.23 |
| Unrated | 4.20 |

Business Impact: Ratings are fairly stable across audience segments; content rating is not a major lever for perceived quality.

| Genre | Apps with 1M+ Installs |
| --- | --- |
| Tools | 172 |
| Action | 128 |
| Photography | 123 |
| Communication | 99 |
| Productivity | 91 |

Business Impact: Utility and entertainment genres reach mass scale most reliably — strong candidates for growth-focused investment.

Finding: The dataset stores one record per app (its most recent update only), so per-app update intervals cannot be computed directly. The "Last Updated" dates span from May 2010 to August 2018, with the volume of updates increasing sharply each year (from 1 in 2010 to 6,284 in 2018 alone), indicating accelerating release cadence store-wide.

Business Impact: The accelerating update trend reflects growing competitive pressure — staying relevant increasingly requires frequent releases.

Finding: Correlation between size and installs is r = 0.134, a weak positive relationship.

Business Impact: Larger apps are not meaningfully penalized by users in install decisions, but the relationship is weak enough that size should be optimized for performance, not treated as a growth lever.

| App | Reviews | Rating |
| --- | --- | --- |
| Facebook | 78,158,306 | 4.1 |
| WhatsApp Messenger | 69,119,316 | 4.4 |
| Instagram | 66,577,313 | 4.5 |
| Messenger | 56,642,847 | 4.0 |
| Clash of Clans | 44,891,723 | 4.6 |

Business Impact: Even the most-reviewed apps range from 4.0–4.6 — massive scale does not push ratings to the ceiling, reinforcing that install volume and rating are independent dimensions.

Finding: "Everyone" dominates both segments (7,248 free apps, 655 paid apps), followed by "Teen." Paid apps skew slightly more toward broad-audience content than free apps.

Business Impact: Both business models target the same broad audience; content-rating segmentation is not a strong differentiator between free and paid strategies.

| Category | Total Installs |
| --- | --- |
| Game | 13,878,924,415 |
| Communication | 11,038,276,251 |
| Tools | 8,001,771,915 |
| Productivity | 5,793,091,369 |
| Social | 5,487,867,902 |

Business Impact: These five categories represent the largest available user bases and should anchor category-prioritization decisions for new development.

## Part 3 — Advanced-Level Questions

Finding: The top 10 apps by rating (all 5.0) are overwhelmingly niche apps with very low review counts (2–32 reviews) and modest install bases (5–1,000 installs), e.g. "Wallpapers FN SCAR H" and "CQ ESPM." None of the top-reviewed mass-market apps (Facebook, Instagram, WhatsApp) appear in the top-rated list.

Business Impact: Perfect ratings at this scale are a statistical artifact of small sample sizes, not evidence of superior quality. Rating alone is an unreliable success metric without a minimum review-count threshold — the company should weight ratings by review volume (e.g. Bayesian average) rather than trusting raw averages for low-volume apps.

Finding: Update counts grew consistently year over year: 2013 (108) → 2014 (203) → 2015 (449) → 2016 (779) → 2017 (1,794) → 2018 (6,284, partial year). This is a clear accelerating trend, not seasonal — it reflects the growth of the Play Store ecosystem itself and rising competitive pressure to ship updates.

Business Impact: The exponential growth in update frequency means release cadence itself has become a competitive necessity; a company shipping only annual updates risks appearing stale relative to the market.

| Install Range | Avg. Rating |
| --- | --- |
| 0–1K | 4.24 |
| 1K–10K | 4.05 |
| 10K–100K | 4.10 |
| 100K–1M | 4.20 |
| 1M–10M | 4.27 |
| 10M–100M | 4.36 |
| 100M+ | 4.30 |

Finding: Ratings dip slightly in the 1K–10K install range, then climb steadily as apps scale past 1 million installs, peaking in the 10M–100M range before a marginal dip at 100M+.

Business Impact: Apps that survive and scale past the early adoption phase (1M+ installs) tend to be genuinely better products — this "survivorship quality curve" suggests the mid-scale growth phase is where the most reliable quality signal emerges, useful for identifying benchmark apps to study.

Finding: Using the companion reviews dataset (29,692 reviews with sentiment labels), apps rated 4.5+ receive 70.5% positive, 9.8% neutral, and 19.6% negative reviews, with an average sentiment polarity of +0.216. Apps rated 3.0 or below receive only 32.6% positive, 26.5% neutral, and 40.9% negative reviews, with an average polarity of -0.058.

Business Impact: The star rating and the actual text sentiment of reviews are strongly aligned, validating star ratings as a trustworthy proxy for user satisfaction at scale. Analyzing negative review text specifically for low-rated apps can surface concrete, actionable complaint themes for product teams.

Finding: Highest-rated genres (min. 5 apps): Casual;Brain Games (4.48), Events (4.46), Books & Reference (4.38), Puzzle;Brain Games (4.37), Art & Design (4.36). Lowest-rated: Video Players & Editors (4.06), Maps & Navigation (4.05), Dating (4.00), Educational;Creativity (3.96), Educational (3.93).

Business Impact: Utility categories that solve a narrow, functional need (dating, maps, education, video tools) consistently underperform on satisfaction — likely due to high user expectations or technical complexity. These are lower-risk-of-disappointment categories to avoid unless the company can clearly differentiate on execution quality.

## Strategic Recommendations

- Prioritize Games, Communication, and Tools for new development — they command the largest total install bases and the broadest audience reach.
- Target a 4.2+ rating as the internal quality bar; treat anything below 4.0 as underperforming relative to 80% of the market.
- Don't rely on raw star ratings alone for competitive benchmarking — weight by review volume, since low-volume apps can show misleadingly perfect scores.
- Keep app size lean (under ~28MB where possible, except for graphically intensive games) to align with the market median and support performance-sensitive markets.
- If pursuing a paid pricing model, invest heavily in perceived value — price alone trends slightly negative with rating, so price increases must be justified with clear differentiation.
- Increase release cadence — update frequency across the store has grown exponentially, and infrequent updates risk appearing neglected relative to competitors.
- Use sentiment analysis on review text as an early-warning system: apps trending toward more negative-sentiment reviews are a leading indicator of rating decline, even before the star average drops.
- Treat Dating, Maps & Navigation, and Education as higher-difficulty categories where user expectations are hardest to meet — enter only with a genuinely differentiated product.

## CONCLUSION

This analysis of 9,659 Google Play Store apps and 29,692 user reviews shows that app success on the platform is driven far more by category positioning, content strategy, and consistent quality than by price or install volume alone. Games, Communication, and Tools command the largest audiences, a 4.2 rating is the realistic bar for competitiveness, and user sentiment closely tracks star ratings, confirming that satisfaction signals in this dataset are reliable. The strongest opportunity for a new entrant lies in niche, high-satisfaction categories like Events, Books and Reference, and Education, where users are already primed to rate generously, while categories like Dating and Maps and Navigation carry higher execution risk.

*This analysis and report were prepared with the assistance of a generative AI tool (Claude) for data cleaning, statistical computation, under the direction and review of the analyst.*
<img width="617" height="345" alt="OVERVIEW" src="https://github.com/user-attachments/assets/e687757e-0c28-4f9f-92cc-399b521d6e51" />
<img width="618" height="336" alt="RATINGS AND QUALITY" src="https://github.com/user-attachments/assets/0cd02535-7dac-492c-99d6-2929010adc45" />
<img width="618" height="341" alt="PRICING AND SIZE" src="https://github.com/user-attachments/assets/af488ae0-4990-4f74-bbe1-432c38d41844" />
<img width="620" height="341" alt="SENTIMENT AND INSIGHTS" src="https://github.com/user-attachments/assets/7db70bf1-8a19-4912-9ee9-f1a1e74b5ee0" />



