# Does-College-Major-Impact-Your-Income-
This is part of the data analysis practice in the *Regression Models* class, which is the 2nd class in the *Statistics and Machine Learning* Specialization.


Your assignment is to study how income varies across college major categories. Specifically answer: “Is there an association between college major category and income?”

To get started, start a new R/RStudio session with a clean workspace. To do this in R, you can use the q() function to quit, then reopen R. The easiest way to do this in RStudio is to quit RStudio entirely and reopen it. After you have started a new session, run the following commands. This will load a data.frame called college for you to work with.


``` {r installpackages, echo = TRUE, results = "hide}
install.packages("devtools")
devtools::install_github("jhudsl/collegeIncome")
library(collegeIncome)
data(college)
```

Next download and install the matahari R package with the following commands:

``` {r morepack, echo = TRUE, results = "hide}
devtools::install_github("jhudsl/matahari")
library(matahari)
```

This package allows a record of your analysis (your R command history) to be documented. You will be uploading a file containing this record to GitHub and submitting the link as part of this quiz.

Before you start the analysis for this assignment, enter the following command to begin the documentation of your analysis:

``` {r start, echo = TRUE, results = "hide}
dance_start(value = FALSE, contents = FALSE)
```

You can then proceed with the rest of your analysis in R as usual. When you have finished your analysis, use the following command to save the record of your analysis on your desktop:

``` {r stop, echo = TRUE, results = "hide"}
dance_save("~/Desktop/college_major_analysis.rds")
```

Please upload this college_major_analysis.rds file to a public GitHub repository. In question 4 of this quiz, you will share the link to this file.

A codebook for the dataset is given below:

- rank: Rank by median earnings
- major_code: Major code
- major: Major description
- major_category: Category of major
- total: Total number of people with major
- sample_size: Sample size of full-time, year-round individuals used for income/earnings estimates: p25th, median, p75th
- p25th: 25th percentile of earnings
- median: Median earnings of full-time, year-round workers
- p75th: 75th percentile of earnings
- perc_men: % men with major (out of total)
- perc_women: % women with major (out of total)
- perc_employed: % employed (out of total)
- perc_employed_fulltime: % employed 35 hours or more (out of employed)
- perc_employed_parttime: % employed less than 35 hours (out of employed)
- perc_employed_fulltime_yearround: % employed at least 50 weeks and at least 35 hours (out of employed and full-time)
- perc_unemployed: % unemployed (out of employed)
- perc_college_jobs: % with job requiring a college degree (out of employed)
- perc_non_college_jobs: % with job not requiring a college degree (out of employed)
- perc_low_wage_jobs: % in low-wage service jobs (out of total)

### Code for the Analysis
``` {r code, echo = TRUE, results = "hide}
dance_start(value = FALSE, contents = FALSE)
View(college)
str(college)
plot(as.factor(college$major_category), college$median)
fit <- lm(median ~ as.factor(major_category), data = college)
summary(fit)
plot(fit, which = 1)
dance_save("~/Desktop/college_major_analysis.rds")
```

**Question: Based on your analysis, would you conclude that there is a significant association between college major category and income?**

Answer: I have investigated the linear relationship between the college major category (major_category) as the predictor and the median income (median) as the outcome. Using the function lm, it has shown in the p-values column of the coefficients section that most of the p-values are larger than 0.05. Hence, suggesting that the relationship is not significant. Also, from the residual plot for median income against the major category, it doesn't seem to have any particular pattern either. **This reinforces the claim that the college major category has no significant impact on median income.**



