# Restaurant Menu Pricing Strategy: Category-Level Analysis & Price Elasticity

An independent data analysis project built in Google Sheets, looking at how pricing, cost efficiency, and price elasticity behave across a 14-item restaurant menu sold through 5 different restaurant categories.

## Why this project

Most menu-level pricing analysis treats a dish as one thing : one price, one cost, one performance number. But the same dish can be sold in very different settings (a fine dining restaurant vs. a food stall vs. a cafe), and those settings can have completely different pricing power, cost structure, and customer price sensitivity. This project started as a standard item-level pricing analysis, and along the way I found that blending all categories together into one number per item was hiding real differences, so the analysis was rebuilt around that finding, at the category-item level instead.

## What's in the analysis

- **Pricing Analysis** : average selling price, market price, and ingredient cost per category-item combination; price gap vs. market; margin %; ingredient cost %; a negotiation-priority framework (which products are worth pushing suppliers on) and a cost-efficiency classification, both benchmarked against each category's own average rather than one blended average across the whole menu.
- **Price Elasticity** : price elasticity of demand per category-item combination, calculated using a log-log regression (`ln(Quantity)` vs. `ln(Price)`), with sample-size and price-variation checks built in so a result isn't trusted just because a formula returned a number.
- **Interactive Dashboard** : revenue and profit by category, monthly revenue trends, and slicers to filter by category and product for closer inspection.

Everything is built on dynamic formulas referencing the raw dataset directly, rather than manual pivot tables or copy-pasted snapshots — so the whole workbook updates automatically as new data is added, without needing to rebuild anything.

## Dashboard

**View Dashboard:** [Google Sheets Analysis & Dashboard](https://docs.google.com/spreadsheets/d/1JUMQupT7qqTVRgpUAVaei7FdZX-TIqzQw9ThI4_P0x8/edit?gid=448116014#gid=448116014)

Access: View Only

![Dashboard Image](https://github.com/sabinamagar7-maker/Restaurant-Menu-Pricing-Strategy-Category-Analysis-Price-Elasticity/blob/main/2_Dashboard_image/Dashboard_Monthly_Revenue_Product_Performance.png)



## Data

The dataset covers 14 menu items sold across 5 restaurant categories (Cafe, Casual Dining, Fine Dining, Food Stall, Kopitiam), with the following fields per transaction:

`Date, Restaurant_ID, Restaurant_Category, Product_Item, Meal_Type, Ingredients, Ingredient_Cost, Market_Price, Selling_Price, Quantity_Sold, Has_Promotion, Special_Event, Weather_Condition`

## Method, in short

- **Category + Item as the unit of analysis** : not blended across categories, since pricing power, cost structure, and price sensitivity differ meaningfully by venue type.
- **Per-unit vs. volume-weighted metrics, chosen deliberately per question** : e.g. margin % is volume-weighted (reflects actual realized profit), while ingredient cost % is per-unit (reflects the dish's structural cost, independent of how much it happened to sell).
- **Category-specific benchmarks**, not one benchmark across the whole menu : so a food stall item isn't judged against a fine dining item's pricing power.
- **Elasticity checked before it's trusted** : sample size and price-point variation are checked per category-item combination before the elasticity number is used for anything.

## Tools

Google Sheets : dynamic array formulas (`UNIQUE`, `FILTER`, `AVERAGEIFS`, `SUMPRODUCT`, `SLOPE`, `RSQ`), no add-ons or external software.

## Limitations

- This is a constructed/practice dataset, not live business data, some patterns (e.g. similar elasticity across very different venue types) may say more about how the dataset was generated than about real customer behavior.
- Elasticity is a simple log-log regression; it doesn't control for confounders like promotions, special events, or weather. A multiple regression or a model built for zero-inflated demand would be a more complete next step.
- Negotiation-priority and cost-efficiency benchmarks are relative to this dataset's own category averages, not external industry or company targets.
- At real business scale (hundreds or thousands of SKUs), this would move from spreadsheet formulas to a proper pricing platform or a Python/SQL pipeline : the logic here is the same, just built by hand and at a much smaller scale.

## Author

Sabina Thapa Magar — [GitHub](https://github.com/sabinamagar7-maker)
