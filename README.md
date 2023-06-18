#  Team3
Our question: How does gender inequality affect crime rates in Europe?

Team name: "Team 3". Student names: Ruben Chocron, Gaby Levis, Yarden Tzaraf, Ziv Fenigstein

Overview of the steps in our analysis:

1. Importing data:
The imported data includes gender inequality index (gii_data), economical crimes (economical_crimes), violent and sexual crimes (violent_sexual_crimes), GII by year (gii_by_year), population per country (population_per_country) and trust rate in institutions for European countries (trust_statistics) .

2.  Data cleaning:
The column names of the imported data frames are decapitalized using the clean_names() function from the janitor package. This standardizes the column names by converting them to lowercase.

3. Grouping and summarizing data:
The economical_crimes2 and violent_sexual_crimes2 data frames are created by grouping the respective data frames by country, category, indicator, and year. The average value per group is calculated using the mean() function. The resulting data frames contain the average values of that crime for each group.

4. Combining data:
The all_crimes2 data frame is created by combining the economical_crimes2 and violent_sexual_crimes2 data frames.
The data frame is then sorted by country.

5. Handling missing values:
The rows with missing values in the all_crimes2 data frame are filtered out using filter() and complete.cases() functions. The filtered rows are stored in the na_rows data frame.

6. Calculating values per 100,000:
The value_per_100000 column is created in the all_crimes2 data frame by dividing the average value by the population of that country and multiplying by 100,000.

7. Merging data frames:
The crimes_gii2 data frame is created by merging the all_crimes2 and gii_by_year data frames based on the country_code and year columns.

8. Filtering and subset selection:
The crimes_gii2 data frame is subsetted to keep only the rows with European country codes using the subset() function and the european_country_codes vector.

9. Grouping and summarizing data (create grouped_crimes2):
The grouped_crimes2 data frame is created by grouping the crimes_gii2 data frame by country_code, country, year, crime_category, gender_inequality_index, police_trust, legal_system_trust, and political_system_trust. The sum_cases_per_100k column is calculated as the sum of value_per_100000 for each group using the summarise() function. The ungroup() function is used to remove the grouping.

10. Normalization:
The gender_inequality_index column in the grouped_crimes2 data frame is normalized using min-max normalization. The values are scaled between 0 and 1 using the minimum and maximum values of the column.

