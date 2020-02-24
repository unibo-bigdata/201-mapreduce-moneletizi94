# 201 MapReduce

Module 1, Big Data course (81932), University of Bologna.

## 201-1 Compile and run a MapReduce job

Goal: run the first MapReduce job

The old way:
```shell
# Get the job file from the virtual cluster's HDFS
hdfs dfs –get /bigdata/mapreduce/wordcount/WordCount.java
# Compile the Java source file and create the jar
# Notice: the command hadoop classpath returns the class path(s) needed to get the Hadoop jar and the required libraries
javac -classpath $(hadoop classpath) -d . WordCount.java
jar cf wc.jar WordCount*.class
# OR: directly get the jar
hdfs dfs –get /bigdata/mapreduce/wordcount/wc.jar mapreduce/wordcount
```

The new way:

- Pull this assignment's code
- Compile with ```./gradlew```

To run the job, use ```hadoop jar <jar-file> <Main-class> <inputDir> <outputDir> [params]```, where

- <inputDir> is the existing directory on HDFS that contains the input files (e.g., "/bigdata/dataset/sample-input")
- <outputDir> is the directory on HDFS to be created by the job to store the results (e.g., "mapreduce/wordcount/output")
- [params] are the optional parameters
- Example: ```hadoop jar wc.jar WordCount /bigdata/dataset/sample-input mapreduce/wordcount/output```
