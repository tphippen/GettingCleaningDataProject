README for Getting and Cleaning Data Course Project
===================================================

Contents of this repo
---------------------
1. README.md
2. run_analysis.R
3. TidySamsungGalaxyData.txt
4. CodeBook.md

Introduction
------------
The purpose of this course project was to get and clean a data set that was
generated by collecting data from the accelerometers and gyroscopes from the 
Samsung Galaxy S smartphone. The original source of the smartphone data is the 
UCI Machine Learning Repository. A detailed description of the original data set
and its components can be found in CodeBook.md

In brief, the goals of this project as outlined in the Course website's project
description, were to

1. Merge the training and test sets of the machine learning data set into one
data set containing the measurements for all 30 subjects. 
2. Select only the measurements on the mean and standard deviation for each 
measurement. Details on how these measurements were defined for selection can be
found in CodeBook.md
3. Descriptively label the activities that each subject was engaged in while
their mesaurements were being taken by their phone's gyroscope and
accelerometer.
4. Give the variable names descriptive labels.
5. Generate a tidy set with the mean of each selected in which the variable is
aggregated by mean for each subject and each activity.

run_analysis.R
--------------
The developer of run_analysis.R used  
R version 3.0.3 (2014-03-06) -- "Warm Puppy"   
Platform: x86_64-apple-darwin10.8.0 (64-bit)

run_analysis.R loads the package, reshape2, so you will need to have downloaded 
reshape2 prior to running the script. 

run_analysis.R, can be run to accomplish each of the goals outlined in the
introduction above. It accomplishes the goals in a series of eight steps. 

1. It is not assumed that the needed data sets from the UCI machine learning
repositiory are in your working directory. Therefore, in the first step, 
a directory, UCI_HAR_Data, is created to store the data. The data is downloaded,
unzipped, and saved to UCI_HAR_Data.
2. Merge the training and test data sets
3. Select only the measurements on the mean and standard deviation for each
measurement. Details on how these measurements were defined for selection
can be found in CodeBook.md
4. Order merged data by subject ID number and activity label
5. "Melt Data" as described by Hadley Wickham in his paper "Reshaping Data with
reshape Package", Journal of Statistical Software, Nov. 2007, Volume 21, 
Issue 12. 
6. Reshape and aggregate data using mean() function
7. Label the data set with descriptive variable names
8. Write tidy data set to .txt file. Space selected as delimiter.

Detailed comments on how each of these steps is carried out can be found in
run_analysis.R

This script produces three data frames.

1. mergedSet: This frame is formed when the training and test sets are merged.
The dimensions of this set are 10299 x 68 
2. fullMelt: This is a tidy data set formed when MergedSet is "melted" using the
melt function from the reshape2 package. fullMelt has 3 identifier (ID) 
variables (subjectID, activityLabel, and variable) and one measured variable.
Each row represents one observation of one variable. The dimensions of this set
are 679734 X 4
3. TidyData: This data has been aggregated by mean and reshaped. Variable names
have been cleaned and rendered more descriptive. The dimensions of this set are
180 x 68.

TidySamsungGalaxyData.txt
-------------------------
run_analysis.R writes TidyData to a space delimited .txt file with the command   
`write.table(TidyData,"TidySamsungGalaxyData.txt",sep = " ",row.names = FALSE)`  

In addition to including TidySamsungGalaxyData.txt in this respository, it has
been uploaded to the Getting and Cleaning Data course website for evaluation.
Rather than evaluating its tidiness using the URI provided by the course 
website, you may want to veiw it in this repository or load as an R data frame 
using the command    
`TidyData <- read.table("TidySamsungGalaxyData.txt", header = TRUE)`

CodeBook.md
-----------
CodeBook.md is a code book that modifies and updates the code books that were 
donloaded along with the Samsung Galaxy data sets. Variables and summaries
calculated are described in detail. Units, and other relevant information are
also provided.