---
title: "error when running mahout recommenditembased"
date: 2016-06-20
forum: Programming Talk
---

### Post by zerop2 on 2016-06-20
mahout/bin/mahout recommenditembased -s similarity_euclidean_distance -i /home/martin/Downloads/rdata.txt -o /home/martin/Downloads/output.txt --numRecommendations 5



16/06/20 20:23:52 INFO Job: Job job_local904270468_0005 running in uber mode : false
16/06/20 20:23:52 INFO Job:  map 0% reduce 0%
16/06/20 20:23:52 INFO Job: Job job_local904270468_0005 failed with state FAILED due to: NA
16/06/20 20:23:52 INFO Job: Counters: 0
16/06/20 20:23:52 INFO deprecation: mapred.compress.map.output is deprecated. Instead, use mapreduce.map.output.compress
16/06/20 20:23:52 INFO deprecation: mapred.output.dir is deprecated. Instead, use mapreduce.output.fileoutputformat.outputdir
16/06/20 20:23:52 INFO JvmMetrics: Cannot initialize JVM Metrics with processName=JobTracker, sessionId= - already initialized
16/06/20 20:23:53 INFO FileInputFormat: Total input paths to process : 1
16/06/20 20:23:53 INFO JobSubmitter: Cleaning up the staging area file:/tmp/hadoop-martin/mapred/staging/martin205977617/.staging/job_local205977617_0006
Exception in thread "main" org.apache.hadoop.mapreduce.lib.input.InvalidInputException: Input path does not exist: file:/home/martin/Downloads/temp/similarityMatrix
	at org.apache.hadoop.mapreduce.lib.input.FileInputFormat.singleThreadedListStatus(FileInputFormat.java:320)
	at org.apache.hadoop.mapreduce.lib.input.FileInputFormat.listStatus(FileInputFormat.java:263)
	at org.apache.hadoop.mapreduce.lib.input.SequenceFileInputFormat.listStatus(SequenceFileInputFormat.java:59)
	at org.apache.hadoop.mapreduce.lib.input.FileInputFormat.getSplits(FileInputFormat.java:375)
	at org.apache.hadoop.mapreduce.lib.input.DelegatingInputFormat.getSplits(DelegatingInputFormat.java:115)
	at org.apache.hadoop.mapreduce.JobSubmitter.writeNewSplits(JobSubmitter.java:493)
	at org.apache.hadoop.mapreduce.JobSubmitter.writeSplits(JobSubmitter.java:510)
	at org.apache.hadoop.mapreduce.JobSubmitter.submitJobInternal(JobSubmitter.java:394)
	at org.apache.hadoop.mapreduce.Job$10.run(Job.java:1285)
	at org.apache.hadoop.mapreduce.Job$10.run(Job.java:1282)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:422)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1556)
	at org.apache.hadoop.mapreduce.Job.submit(Job.java:1282)
	at org.apache.hadoop.mapreduce.Job.waitForCompletion(Job.java:1303)
	at org.apache.mahout.cf.taste.hadoop.item.RecommenderJob.run(RecommenderJob.java:249)
	at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:70)
	at org.apache.mahout.cf.taste.hadoop.item.RecommenderJob.main(RecommenderJob.java:335)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.apache.hadoop.util.ProgramDriver$ProgramDescription.invoke(ProgramDriver.java:72)
	at org.apache.hadoop.util.ProgramDriver.run(ProgramDriver.java:145)
	at org.apache.hadoop.util.ProgramDriver.driver(ProgramDriver.java:153)
	at org.apache.mahout.driver.MahoutDriver.main(MahoutDriver.java:195)

---

