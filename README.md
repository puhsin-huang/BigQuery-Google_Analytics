# BigQuery-Google_Analytics

The PDF report, datasets, and ipynb file can be retrieved here: https://drive.google.com/drive/folders/1XkWsdkP2Sw9cb7QJIQcGnSvtuDXzU0Qh?usp=sharing

### Data Description:
The ecommerce website data includes traffic source, content, transactional data: https://console.cloud.google.com/marketplace/product/obfuscated-ga360-data/obfuscated-ga360-data

The detailed column definition can be found here: https://support.google.com/analytics/answer/3437719?hl=en

### Project Goal: Help companies prioritize user segments and allocate budget efficiently to increase sales.
### Detailed Approach Description:
By dividing a customer base into groups of individuals that are similar in specific ways, marketers can custom-tailor their content and media to unique audiences. In short, by doing customer segmentation, this analysis help marketers create segmented campaigns, lower marketing costs, and build better products. This report mainly includes three parts:

- EDA: Time series metrics performance tracking
- Customer segmentation: RFM + k-means clustering -> interpret the centroid of that cluster.
- Cohort Analysis: The repeat purchase rate is closely related to churn rate.
CLV calculation: Prioritize High CLV(Customer livetime value) user

First, Exploratory data analysis provides a high-level overview of the context to answer questions such as if the seasonality exists, what's the average sales, is it common to see big fluctuations in metric performance...etc.

Next, RFM segmentation analysis is conducted to identify 5 groups - active high-value users, inactive high-value users, active low-value users, inactive low-value users, and super stars. Marketers can approach each group with tailored discounts options and with different frequency. Also, by observing the recency and frequency patterns, we can predict which customers are likely to churn, and further reach out to these people.

Besides doing segmentation by purchase behavior, another approach would be segmenting people by cohorts. A Cohort is first-time customers from each month. When those first-timers make additional purchases in the following months, I calculate the "Repeat %". It is extremely important to track this metric since it is related to the churn rate. The monthly purchase behavior should be closely monitor and mind if there are big gaps between cohorts.

Lastly, one question many organizations often encounter is how to predict the livetime value of a customer? To prioritize customer segments that are most valuable to the company, CLV is an important metric that measures the total revenue reasonably expected from a customer.

I define the value of a user as total revenue coming from that user within the first year since the first time he/she comes to the site. Hence, I go back in time and pick users who first visit the website in August, 2016, and calculate how much revenue each new users generates in the following year (~August, 2017). This way, I can explore which channels, device, browsing behavior means higher CLV. Utilizing this approach, marketers can then allocate limited budget to target identified channels/ device/ users that are highly possible to bring more revenue.

### Insights:
- This is a healthy grown up company with an average 75% of monthly revenue coming from existing customers. The metric performance trend is overall quite stable with a few peaks probably due to seasonality.
- RFM models is conducted to help track the engagement of the identified five groups. Marketers can consider launching VIP programs for super stars and active high-value users, or to offer discounts to groups with less engagement.
- New users coming from display ads have the highest avg CLV. However, the number of users from this channel is quite small. Marketers can consider to invest more on this channel to acquire more high-value customers.
- Through the CLV analysis, one can find that besides the U.S., the Philippine market also has high potential. A deep dive research can help devise the best strategy to target this market.


### Things worth to explore & Limitations:
- Funnel Analysis - Explore the 'Hits' field.
	The hits column contains information about how users interact with the site. Due to the time limitation, I did not look into this part. 
	However, it’s worth to work with field expert to understand what are the key behaviors they care, and possibly run analysis such as funnel analysis to understand what’s the retention/churn rate in each stage (visits, signups, product views, add-to-cart, checkout, order complete…) and further make business suggestions.


- Machine Learning - CLV prediction: Predict customer value.(need more data)
	I’d like to build a ML model that predicts a user’s LTV based on her behavior during first time visiting the site. I define the value of a user as total revenue coming from that user within the first year since the first time she comes to the site. I will go back in time and pick users who came to our site more than 1 year back since we do know the revenue coming from them. 	Next, I will collect browsing behavior features such as device used, source channels, time spent on site…etc, and use these features to predict the revenue this person will bring.
	However, this model can’t be built since only one year data is available, and there are only 1046 unique purchasers in the first month(2016/8). A longer period of data is required to try out this idea.

