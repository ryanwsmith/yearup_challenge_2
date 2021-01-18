# Yearup Challenge 2: Python

# Main Challenge: Generate Twitter CVE Metrics

## Overview
The goal of this challenge is to generate a number of metrics from Twitter CVE data similar to what we saw used the last challenge.

In this challenge there's a full month of data, each day in it's own file in the [data/yearup folder](data/yearup_challenge/)

The starter code will load each of the log files in the [data/yearup folder](data/yearup_challenge/), filter out invalid tweets, and extract certain data fields from each tweet.

There is also a framework for a simple report generator and example metrics functions to get you started.

For the bonus challenge, this program will also write out a CSV file "twitter_data.csv" to the current directory

:information_source:  **Tips** 
- use Python3 to run yearup_challenge2.py (python3 yearup_challenge2.py)
- run yearup_challenge2.py from inside it's current directory (otherwise you'll have trouble accessing the data)


## Main Challenge: Metrics

:information_source:   Places were you need to make updates are marked with TODO in the comments, anything marked with "INFO" comments are optional for debugging

1. First, I need your help fixing the _filter_tweet_data_ function by adding some code [here](https://github.com/ryanwsmith/yearup_challenge_2/blob/a79b4a30e763400131c30582bb41da18690716ee/yearup_challenge2.py#L113-L116)
2. Next, I need you to update _print_tweet_data_metrics_ function by writing new functions to compute the metrics and adding a call to that code [here](https://github.com/ryanwsmith/yearup_challenge_2/blob/a79b4a30e763400131c30582bb41da18690716ee/yearup_challenge2.py#L103)

For #2, I've added 3 examples above the TODO that you can use/copy/modify as you see fit.  You should notice a pattern for each section:
1. call a function to get the computed metrics in a dictionary 
2. print the title of the metric for the report
3. print the metrics (a pretty_print function has been provided to handle formatting)

Each of your metrics functions should return a dictionary where the KEY is the name of the metrics and the VALUE is the value of the metrics.  
One example of nested dictionaries is shown in _get_weekday_metrics_for_by_cve_ in case you want to try that.

Review the metrics functions in the examples, you should be able to copy and modify them to create new metrics for the report.

For the main challenge add as many of the additional metrics as you can: (they get harder further down the list)
- number of tweets for each cve (like challenge #1)
- most popular day of the week for all tweets
- total number (sum) of "followers" who could have have seen any tweet for a CVE (use user follower count in tweet)
- number of cves not from 2020 (remember the year is in the format of the CVE: CVE-YYYY-...  date_year is the year the tweet was _sent_)
- count of CVEs from each CVE release year (using the year in the CVE number)
- average number of tweets for each user (user_status_count is the number of tweets they've sent)
- date that the CVE was first seen in a tweet and the date it was last seen in the tweet

Feel free to get creative and add any additional metrics you like.  If you get REALLY adventurous, you can extract additional fields in the _extract_data_from_tweet_json_ function

Be sure to review an [example of the extracted tweet data](https://github.com/ryanwsmith/yearup_challenge_2/blob/a79b4a30e763400131c30582bb41da18690716ee/yearup_challenge2.py#L150-L166) to help you find the data you'll need

:warning:  Notice that I've marked a comment _"# NO NEED TO EDIT BELOW THIS LINE, FEEL FREE TO MAKE CHANGES BUT BE CAREFUL"_
As this says, everything below is starter code and there should be no **need** to update it, but you're welcome to make changes if you like.


## Bonus Challenge: SQL

:warning:   This bonus challenge may be quite difficult and I haven't had the time to provide any starter code for it, check back and I may provide some tips later this week.
We may also have a chance to do some demos on Thursday.

## Your Challenge

Use the csv file generated twitter_data.csv

- **Option 1:** If you have access to an AWS account, setup a new Athena data base and table to run SQL commands on the data in S3. 
- **Option 2:** If you have access to an AWS account, you could also setup a free-tier RDS instance.
- **Option 3:** Setup a SQL database on your laptop (e.g. mysql, sqlite) create a new database and table, then load data from the CSV file to run SQL commands on the data

:warning:  If you choose option #1 with Athena be sure to gzip the CSV file (gzip twitter_data.csv) before uploading it to S3 to save on any costs.  This will reduce it from ~16MB -> ~3MB, so each Athena query should only cost about 2 cents 

## Beyond the Challenge

Feel free to have fun and explore what you can do with this data.  

If you have different ideas than what's in the challenge, feel free to submit and demo them as well.