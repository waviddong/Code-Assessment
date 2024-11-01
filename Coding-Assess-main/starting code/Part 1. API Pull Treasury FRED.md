# Part 1: API Pulling, Data Wrangling, and Visualizations

## Objective
Retrieve daily Treasury yield data from FRED, calculate bond spreads over the Treasury curve, and create visualizations.

## Steps

### 1. API Registration
Go to [FRED API Documentation](https://fred.stlouisfed.org/docs/api/fred/) and register for a free API Key.

### 2. Data Pulling
Write a Python function to pull daily constant maturity yield data from `2023-01-01` to `2023-12-31` for the following Treasury tenors: 1M, 3M, 6M, 1Y, 2Y, up to 30Y.

- FRED field names for each tenor:
  - **1M**: `"DGS1MO"`
  - **3M**: `"DGS3MO"`
  - **6M**: `"DGS6MO"`
  - **1Y**: `"DGS1"`
  - **2Y**: `"DGS2"`
  - Continue this list up to **30Y** with `"DGS30"`

### 3. Data Storage
Store the pulled data in a DataFrame with `date` as the index.

### 4. Spread Calculation
Load the file `data/Part 1.bond_yields.xlsx`. For each bond:
- Calculate its spread over the Treasury curve.
- If a bond’s WAL (Weighted Average Life) falls between two points on the Treasury curve, use linear interpolation.

### 5. Visualizations
Create at least two types of visualizations to demonstrate the relative value of each sector based on the calculated spreads.

---

## Pseudocode for Implementation

```python
import requests
import pandas as pd

def fetch_fred_yield(series_id, start_date="2023-01-01", end_date="2023-12-31", api_key="your_api_key"):
    # Define the API URL and parameters here
    
    # Make an API request and handle errors
    
    # Convert response JSON into a DataFrame, setting 'date' as index
    # Convert the 'value' column to numeric and rename it based on series_id
    
    return df[[series_id]]  # Final DataFrame with date index and yield column

# List of Treasury yield series IDs on FRED
tenor_series_ids = [
    "DGS1MO", "DGS3MO", "DGS6MO", "DGS1",  # Short-term yields
    "DGS2", "DGS3", "DGS5",               # Medium-term yields
    "DGS7", "DGS10", "DGS20", "DGS30"     # Long-term yields
]

# Initialize API key

# Fetch data for each tenor, store in a dictionary of DataFrames

# Combine all DataFrames into a single DataFrame, joining on the date index

# Print the number of rows in the final DataFrame
