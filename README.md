# Amazon Recommendation System

## Compatibility
The code is tested using enviroment Spark 1.2.1 with Python 2.7 on Virtual Box.

## Setup
### Datasets :
- Amazon Review Data accessed from (http://snap.stanford.edu/data/web-Amazon-links.html)
- Number of reviews : 34,686,770
- Number of users : 6,643,669 (56,772 with more than 50 reviews)
- Number of products : 2,441,053
### Paper:
http://snap.stanford.edu/class/cs224w-2012/projects/cs224w-044-final.v01.pdf

## How to run

### Step 1:
Start Hadoop on Virtual box.

### Step 2:
Setup ``numpy``, ``scipy`` library.

### Step 3:
Run ``export SPARK_HOME=/usr/hdp/2.2.4.2-2/spark`` on terminal.

### Step 4:
Move 4 file ``AmazonALS.py``, ``ratings.dat``, ``products.dat``, ``users.dat`` to folder of Hadoop:
	
	/workspace/AmazonRecommendation

### Step 5:
Create folder in HDFS ``/user/AZ_P/input``, and move 3 file ``.dat`` to the newly created ``input`` directory with the following command:
	
	$ hdfs dfs -mkdir /user/AZ_P/input
	
	$ hdfs dfs input <file_name> <path>

### Step 6:
Go to the ``Demo`` folder containing the ``AmazonALS.py`` file. Open the terminal here and run:

	$ su root

	$ spark-submit AmazonALS.py <InputDirectory> <OutputFileName> <Iterations> <Partitions>
	
	$ spark-submit AmazonALS.py /user/AZ_P/input outputAmazonReco.dat 10 4

### Step 7:
A ``outputAmazonReco.dat`` file has been created in the current directory with columns:
	
	userID, recommendedProduct, predictedRating
