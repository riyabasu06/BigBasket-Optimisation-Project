# BigBasket Optimization Project

## Overview

This project utilizes transactional data from BigBasket to analyze customer purchasing patterns and generate actionable insights using the **Apriori Algorithm** for Market Basket Analysis. The primary objective is to identify associations between products to optimize inventory management, improve product recommendations, and enhance customer experience.

## Dataset

The dataset (`BigBasket.csv`) consists of transactional data where each row represents a list of items purchased together. It is structured with products listed in columns, and transactions span multiple rows.

### Example Data Structure:
| Product 1         | Product 2         | ... | Product N  |
|--------------------|-------------------|-----|------------|
| Mineral Water      | Eggs             | ... | Chicken    |
| Spaghetti          | Tomatoes         | ... | Mineral Water |

- **Rows**: Transactions
- **Columns**: Products purchased in a transaction

## Implementation

### Tools and Libraries Used

- **Python**: Programming language for analysis and model implementation.
- **Pandas**: Data manipulation and preprocessing.
- **Apyori**: A library for implementing the Apriori Algorithm to discover association rules.

### Methodology

1. **Data Preprocessing**:
   - Transactions were extracted and converted into a list format suitable for analysis.
   - Empty values were handled gracefully to ensure clean data.

2. **Market Basket Analysis**:
   - The **Apriori Algorithm** was applied to find frequent itemsets and generate association rules.
   - Parameters used:
     - Minimum Support: `0.003`
     - Minimum Confidence: `0.2`
     - Minimum Lift: `3`
     - Maximum Itemset Length: `2`

3. **Output**:
   - Frequent itemsets and their corresponding association rules were extracted and analyzed.
   - Results include metrics like **support**, **confidence**, and **lift**, which indicate the strength of the relationships.

### Example Code Snippet

```python
from apyori import apriori

# Preparing data
transactions = []
for i in range(0, len(df)):
    transactions.append([str(df.values[i, j]) for j in range(0, 10)])

# Applying Apriori
rules = apriori(transactions, min_support=0.003, min_confidence=0.2, min_lift=3, min_length=2, max_length=2)

# Extracting Results
results = list(rules)
```

## Results

The analysis provided insights into customer purchasing behavior:
- Frequently bought-together items
- Strong associations between specific products

These findings can be used to:
- Design targeted promotions
- Enhance cross-selling strategies
- Optimize inventory levels

## How to Run the Project

1. Install dependencies:
   ```bash
   pip install pandas apyori
   ```
2. Place the dataset (`BigBasket.csv`) in the project directory.
3. Execute the Python script or Jupyter Notebook:
   ```bash
   python BigBasket.py
   ```
   OR
   Open `BigBasket.ipynb` in Jupyter Notebook and run all cells.

## Future Enhancements

- Incorporate advanced machine learning models for predictive analytics.
- Expand analysis to include more diverse product categories.
- Integrate real-time data for dynamic optimization.

## License

This project is open-source and available under the [MIT License](https://opensource.org/licenses/MIT).
