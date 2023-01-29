# Data Visualization Project (Loan Data from Prosper)

## by Taima Alosaimi


## Dataset

Loan Data from Prosper dataset: This dataset is financial dataset and this is related to the loan, borrowers, lenders, interest rates and stuffs like that. Prosper or Prosper Marketplace Inc. is a San Francisco, California based company specializing in loans at low interest rates to the borrowers.

there are (113,937) loans with (81) associated variables (characteristics), some of the variables are:

- Term: The length of the loan expressed in months.
- LoanStatus : Current status of the loan: Cancelled, Chargedoff, Completed, Defaulted, FinalPaymentInProgress, PastDue, etc..
- ProsperScore : Risk Factor score from 1 to 10. 10 being least risky
- BorrowerAPR : The Borrower’s Annual Percentage Rate (APR) for the loan.
- BorrowerRate : The Borrower’s interest rate for this loan.
- EmploymentStatus : Current type of employment
- Occupation : Occupation of borrower at the time of listing
- ProsperRating..Alpha. : Prosper rating for borrowers in alphabets
- StatedMonthlyIncome : Monthly income of the borrower
- MonthlyLoanPayment : Monthly loan payment amount
- LoanOriginalAmount : Original amount of the loan

Data Source: https://s3.amazonaws.com/udacity-hosted-downloads/ud651/prosperLoanData.csv.

Data dictionary to understand all variables more in this link: https://docs.google.com/spreadsheets/d/1gDyi_L4UvIrLTEC6Wri5nbaMmkGmLQBk-Yx3z0XDEtI/edit#gid=0

**some operations on the data (tidy, adjust, change the form of the data):**
- first I select only the columns that are related to our exploration of the loan. So I chose about 23 Out of 81 columns to investigate
- I adjusted the datetime columns ('ListingCreationDate', 'ClosedDate', 'LoanOriginationDate')
- I adjusted datatype for the categorical columns ('Occupation', 'ProsperScore', 'BorrowerState', 'LoanStatus', 'EmploymentStatus')
- then mapping the list dictionary of ListingCategory
- after that replacing the (Past Due (1-15 days), Past Due (31-60 days), etc...) with just (Past Due) in the bar chart of LoanStatus
- The bar chart of the ProsperScore shows that there are some borrowers with a score of 11 which should not be possible since the score ranges from 1-10, so I cleaned (exclude all records with a Prosper Score of 11)



## Summary of Findings

In the beginning of the analysis I started by looking at the distribution of the main variables of interest and I found Some Unusual distributions in following:

- most of the borrowers are employed of different kind of employment (full-time, part-time, self-emplpoyed) but some of the borrowers are unemployed or retired  and they could get a loan.

- There are around 935 loans with a monthly payment of 0 which does not make sense but maybe they related to some special agreements (for example: the customer does not need to pay back the loan for the first 6 months).

but I was most interested in figuring out What factors affect a BorrowerRate (The Borrower's interest rate for this loan) in the dataset so I focus on that, at the first I expect that "EmploymentStatus, term, ProsperScore and LoanOriginalAmount" have the strongest effect on the interest rate.

and from bivariate exploration we saw that there are some negative relationship between employment status and interest rate. where not employed Borrowers have in average higher interest rate than the Borrowers who have jobs. we saw also that there is a positive relationship between term and interest rate, where 36 and 60 have in average higher interest rate than 12. so, We can conclude that the higher the length of loan term the higher the interest rate. in addition, we saw that there is a clear and strong relationship between Prosper Score and interest rate. so, We can conclude that the higher the score the lower the interest rate. and there is a negative relationship between loan original amount and interest rate, means large loan amount have less interest rate than low loan amount. and for loan categories We saw that Cosmetic Procedure loans have highest interest rates while personal loans have lowest interest rate.

lastly, I did not expect that 'ListingCategory' has an affect on the interest rate the at the beginning of the investigation, but the plots shows that some categories have high interest rate and some have low interest rate.

and in multivariate exploration, it's observed that there is a relationship between BorrowerRate and ProsperScore as well with Term. We found that the loans of 5 year (60 months) are generally have higher rate than the other loan regardless of the prosper Score (with the exception of (2, 3, 4, 5, 6) prosper Score. so we can conclude that the long of loan term the higher is the loan risk. and as it is mentioned before, the rates are the lowest, for borrowers with a high prosper Score.

**In conclusion**, we found that the borrower with a low Prosper Score and long term get a higher BorrowerRate (interest rate) due to the higher risk that the loan will be defaulted.


## Key Insights for Presentation

For the presentation, I focused on the factors most affect the Borrower Rate (ProsperScore, Term) and left out the other factors. I start by introducing the relationship between these factors with Borrower Rate.

lastly, plot the relationship of factors and Borrower Rate with each other using pointplot.
