---
title: "Codebook"
date: "01/05/2020"
output: word_document
---
## This is Code Book for Peer Assignment of Getting and Cleaning Data 

Under this Assignment following Steps need to follow
1. Dowload Data Set From given source 
 30 volunteers performed 6 different activities while wearing a smartphone. The smartphone captured various data about their movements.
Explanation of each file

    1.features.txt: Names of the 561 features.

    2.activity_labels.txt: Names and IDs for each of the 6 activities.

    3.X_train.txt: 7352 observations of the 561 features, for 21 of the 30 volunteers.

    4.subject_train.txt: A vector of 7352 integers, denoting the ID of the volunteer related to each of the observations in X_train.txt.

    5.y_train.txt: A vector of 7352 integers, denoting the ID of the activity related to each of the observations in X_train.txt.

    6.X_test.txt: 2947 observations of the 561 features, for 9 of the 30 volunteers.

    7.subject_test.txt: A vector of 2947 integers, denoting the ID of the volunteer related to each of the observations in X_test.txt.

    8.y_test.txt: A vector of 2947 integers, denoting the ID of the activity related to each of the observations in X_test.txt.

More information about the files is available in README.txt. More information about the features is available in features_info.txt.
## Data files that were not used
This analysis was performed using only the files above, and did not use the raw signal data. Therefore, the data files in the "Inertial Signals" folders were ignored.
## Processing steps
      
  1.Merges the training and the test sets to create one data set

    X (10299 rows, 561 columns) is created by merging x_train and x_test using rbind() function
    Y (10299 rows, 1 column) is created by merging y_train and y_test using rbind() function
    Subject (10299 rows, 1 column) is created by merging subject_train and subject_test using rbind() function
    Merged_Data (10299 rows, 563 column) is created by merging Subject, Y and X using cbind() function


2.Extracts only the measurements on the mean and standard deviation for each measurement

    TidyData (10299 rows, 88 columns) is created by subsetting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

3.Uses descriptive activity names to name the activities in the data set

    Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of the activities variable

4.Appropriately labels the data set with descriptive variable names

    code column in TidyData renamed into activities
    All Acc in column’s name replaced by Accelerometer
    All Gyro in column’s name replaced by Gyroscope
    All BodyBody in column’s name replaced by Body
    All Mag in column’s name replaced by Magnitude
    All start with character f in column’s name replaced by Frequency
    All start with character t in column’s name replaced by Time

5.From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject

    FinalData (180 rows, 88 columns) is created by sumarizing TidyData taking the means of each variable for each activity and each subject, after groupped by subject and activity.
    Export FinalData into FinalData.txt file.

   