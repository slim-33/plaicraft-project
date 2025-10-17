# Subscription Prediction from Minecraft Player Data using KNN Classification

This project explores whether a Minecraft player’s **age** and **total playtime** can be used to predict their **subscription status** to a game-related newsletter. We use **K-Nearest Neighbors (KNN) classification** in R to develop a model that can assist a UBC AI research group in understanding their audience and optimizing their recruitment strategy.

---

## Group Members

This project was completed as a group of four students as part of a university data science course.

---

## Project Motivation

A Minecraft server set up by UBC's Computer Science department is used to collect AI-related player interaction data. Recruitment for players is complex, so our goal was to **analyze behavioral data to help streamline recruitment and resource allocation**.

### Research Question

> **Can the number of played hours and the age of the players be used to predict a player's subscription status?**

We hypothesize that younger players that spend more time playing are more likely to subscribe to the newsletter.

---

## Data Description

Two datasets were used, but only one was central to our analysis.

- `players.csv`: Contains player metadata (age, gender, experience level, playtime, subscription status).
- `sessions.csv`: Contains game session data per player. *(Not used in modeling.)*

### Variables Used

- `subscribe`: Whether the player is subscribed to the newsletter.
- `played_hours`: Total time played.
- `Age`: Player's age.

> Missing values (e.g., NA in age) were handled by dropping affected rows.

---

## Methodology

### Exploratory Data Analysis (EDA)

- **Histograms** to show subscription vs playtime.
- **Boxplots** to compare age distributions by subscription.
- **Scatterplots** to observe patterns between age and playtime.

### Modeling: K-Nearest Neighbors (KNN)

- Used **tidymodels** in R.
- Dataset split: 80% training / 20% testing (stratified by `subscribe`).
- Tuned K from 1 to 30 via 5-fold cross-validation.
- Selected **K=13** based on a balance of accuracy and model simplicity.

---

## Results

### Final Model Accuracy

- **Training accuracy (cross-validation):** ~72.7%
- **Testing accuracy:** ~67.5%

### Confusion Matrix
|               | Predicted: No | Predicted: Yes |
|---------------|---------------|----------------|
| **Actual: No** | 3             | 8              |
| **Actual: Yes**| 5             | 24             |

> The model didn't just predict the majority class, indicating it learned meaningful patterns.

### Key Insights

- All players with **>10 hours** of playtime subscribed.
- Majority of subscribers are between **10–28 years old**.
- Playtime and age can be reasonable predictors of subscription.

---

## Limitations

- The dataset is **small** and **imbalanced** (more subscribed players than unsubscribed).
- Players over age 30 are underrepresented.
- No players with **long playtime but no subscription**, limiting model generalizability.
- Data points with `NA` in age were dropped instead of imputed.

---

## Project History & Version Control

> **Note on Commit History**  
> This project was completed **before** Git and GitHub were integrated into our workflow.  
> As a result, the commit history is limited to a single upload of the final version.  

In future projects, we plan to implement proper version control throughout the development lifecycle.

---

## References

- Woodward, E. (2025). *Minecraft Player Demographics Report*.
- Tidyverse & Tidymodels Documentation: [https://www.tidymodels.org](https://www.tidymodels.org)

---