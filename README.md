# customer-lifetime-value-prediction
Predict CLV based on RFM model

Source: https://www.analyticsvidhya.com/blog/2020/10/a-definitive-guide-for-predicting-customer-lifetime-value-clv/

Improvement:
- The source is for the retail and the script is adapted for the Home-Try-On business model
- Looping to give the predicted value for the next months during a 12-month period
- Transform output into ready-to-use format

Model: 
- Contractual business context: Modeled using survival-based approaches
- RFM & BG/NBD for expected repurchasing rate
- Gamma-gamma for expected AOV

Data used:
- Recency ~ Months after enrolment
(How long ago was the customer last transaction?)
- Frequency  ~ Repurchasing rate
(How many repeated purchases are there?)
- Monetary Value ~AOV
(How much revenue did they generate?)

Default model result:
- over-predict -> Errors lie mostly in: Customer predicted purchase churns (false positive)
- Compare the test and actual CLV 12 months after enrollment of past cohort data to get the delta
- For the delta to be under 5%, adjust the weight to be between 10% and 25%. In this script, we take the average of the predicted value when the weight is 25% (conservative) and 10% (aggressive)
