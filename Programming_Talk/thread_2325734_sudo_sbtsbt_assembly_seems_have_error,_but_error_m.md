---
title: "sudo sbt/sbt assembly seems have error, but error message since example can not run"
date: 2016-05-24
forum: Programming Talk
---

### Post by zerop2 on 2016-05-24
[COLOR=#000000][FONT=Verdana]after run [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]sudo sbt/sbt assembly [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]got error [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana][warn] [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn] /home/martin/Downloads/spark-1.6.1/sql/core/src/main/scala/org/apache/spark/sql/execution/datasources/WriterContainer.scala:204: constructor TaskID in class TaskID is deprecated: see corresponding Javadoc for more information. [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn]     this.taskId = new TaskID(this.jobId, true, splitId) [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn] [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn] /home/martin/Downloads/spark-1.6.1/sql/core/src/main/scala/org/apache/spark/sql/execution/datasources/text/DefaultSource.scala:92: constructor Job in class Job is deprecated: see corresponding Javadoc for more information. [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn]     val job = new Job(sqlContext.sparkContext.hadoopConfiguration) [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn] [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][info] Compiling 2 Scala sources and 2 Java sources to /home/martin/Downloads/spark-1.6.1/external/mqtt/target/scala-2.10/test-classes... [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][info] Compiling 238 Scala sources and 4 Java sources to /home/martin/Downloads/spark-1.6.1/mllib/target/scala-2.10/classes... [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn] /home/martin/Downloads/spark-1.6.1/mllib/src/main/scala/org/apache/spark/ml/Transformer.scala:119: method callUDF in object functions is deprecated: Use udf. This will be removed in Spark 2.0. [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn]       callUDF(this.createTransformFunc, outputDataType, dataset($(inputCol)))) [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn]       ^ [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn] /home/martin/Downloads/spark-1.6.1/mllib/src/main/scala/org/apache/spark/mllib/api/python/PythonMLLibAPI.scala:344: method setRuns in class KMeans is deprecated: Support for runs is deprecated. This param will have no effect in 1.7.0. [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn]       .setRuns(runs) [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn]        ^ [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn] /home/martin/Downloads/spark-1.6.1/mllib/src/main/scala/org/apache/spark/mllib/clustering/KMeans.scala:502: method setRuns in class KMeans is deprecated: Support for runs is deprecated. This param will have no effect in 1.7.0. [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn]       .setRuns(runs) [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn]        ^ [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn] /home/martin/Downloads/spark-1.6.1/mllib/src/main/scala/org/apache/spark/mllib/clustering/KMeans.scala:526: method setRuns in class KMeans is deprecated: Support for runs is deprecated. This param will have no effect in 1.7.0. [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn]       .setRuns(runs) [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn]        ^ [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][warn] four warnings found [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][info] Compiling 28 Scala sources and 1 Java source to /home/martin/Downloads/spark-1.6.1/sql/hive/target/scala-2.10/classes... [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]/home/martin/Downloads/spark-1.6.1/build/sbt-launch-lib.bash: line 72:  4210 Killed                  "$@" [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]martin@ubuntu:~/Downloads/spark-1.6.1$ [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]martin@ubuntu:~/Downloads/spark-1.6.1$ ./bin/run-example SparkPi 10 [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Failed to find Spark examples assembly in /home/martin/Downloads/spark-1.6.1/lib or /home/martin/Downloads/spark-1.6.1/examples/target [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]You need to build Spark before running this program [/FONT][/COLOR]

---

### Post by Buek_Torao_Garc on 2016-05-26
I got the same error!!

---

### Post by Habitual on 2016-05-27
[http://ubuntuforums.org/showthread.php?t=2325514](http://ubuntuforums.org/showthread.php?t=2325514)

---

