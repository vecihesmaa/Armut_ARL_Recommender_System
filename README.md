# Armut_ARL_Recommender_System

## Project Description

Armut, Turkey's largest online service platform, connects service providers with customers. Users can easily access services such as cleaning, renovation, and transportation through their computers or smartphones. In this project, a service recommendation system was created using the Association Rule Learning method based on Armut's user data.

## Dataset
The dataset consists of services received by customers and their respective categories. Each service includes a timestamp indicating when it was purchased. The dataset variables are as follows:

- **UserId**: Customer ID.
- **ServiceId**: Anonymized service IDs. (Example: A sofa cleaning service under the cleaning category)
- **CategoryId**: Anonymized category IDs. (Example: Cleaning, transportation, renovation categories)
- **CreateDate**: The date when the service was purchased.

## Data Preparation

### Step 1: Reading the Dataset
- The "armut_data.csv" file was read.

### Step 2: Creating Service Identifiers
- **ServiceID** and **CategoryID** were combined to create a new variable ("ServiceID_CategoryID").

### Step 3: Defining Shopping Baskets
- Since the dataset does not include a predefined basket structure, each customer's monthly purchased services were treated as a shopping basket.
- A new date variable containing only the year and month was created from **CreateDate**.
- **UserID** and the new date variable were combined to generate a unique **BasketID**.

## Generating Association Rules

### Step 1: Creating a Service-Basket Pivot Table
- A pivot table for service purchases was created.
- Example format:

  | BasketID     | 0_8 | 10_9 | 11_11 | 12_7 | ... |
  |-------------|----|----|------|-----|-----|
  | 0_2017-08   |  0 |  0 |   0  |  0  | ... |
  | 0_2017-09   |  0 |  0 |   0  |  0  | ... |
  | 10000_2017-08 |  0 |  0 |   0  |  0  | ... |

### Step 2: Extracting Association Rules
- The Apriori algorithm was applied to generate association rules between services.
- Support, Confidence, and Lift values were calculated.

### Step 3: Implementing a Recommendation Function
- The `arl_recommender` function was developed.
- For example, if a user recently received the **"2_0"** service, the function suggests the most relevant services based on association rules.

## Usage

The `arl_recommender` function provides personalized service recommendations based on users' past service purchases and the discovered association rules. This enables a better service experience tailored to user preferences.

## Conclusion
This project analyzed Armut users' service consumption patterns and applied Association Rule Learning to extract meaningful insights. The developed recommendation system suggests relevant services to users based on their past service purchases, improving their overall experience on the platform.
