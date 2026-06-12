---
title: "mahout build error"
date: 2016-06-20
forum: Programming Talk
---

### Post by zerop2 on 2016-06-20
ubuntu:~/Downloads/mahout$ sudo mvn -X -DskipTests clean install


...

[WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireMavenVersion failed with message:
Detected Maven Version: 3.0.5 is not in the allowed range [3.3.3,).
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary:
[INFO] 
[INFO] Mahout Build Tools ................................ FAILURE [0.888s]
[INFO] Apache Mahout ..................................... SKIPPED
[INFO] Mahout Math ....................................... SKIPPED
[INFO] Mahout HDFS ....................................... SKIPPED
[INFO] Mahout Map-Reduce ................................. SKIPPED
[INFO] Mahout Integration ................................ SKIPPED
[INFO] Mahout Examples ................................... SKIPPED
[INFO] Mahout Math Scala bindings ........................ SKIPPED
[INFO] Mahout H2O backend ................................ SKIPPED
[INFO] Mahout Spark bindings ............................. SKIPPED
[INFO] Mahout Flink bindings ............................. SKIPPED
[INFO] Mahout Spark bindings shell ....................... SKIPPED
[INFO] Mahout Release Package ............................ SKIPPED
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 1.541s
[INFO] Finished at: Mon Jun 20 18:42:24 PDT 2016
[INFO] Final Memory: 8M/20M
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-enforcer-plugin:1.4:enforce (enforce-versions) on project mahout-buildtools: Some Enforcer rules have failed. Look above for specific messages explaining why the rule failed. -> [Help 1]
org.apache.maven.lifecycle.LifecycleExecutionException: Failed to execute goal org.apache.maven.plugins:maven-enforcer-plugin:1.4:enforce (enforce-versions) on project mahout-buildtools: Some Enforcer rules have failed. Look above for specific messages explaining why the rule failed.
	at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:217)
	at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:153)
	at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:145)

---

### Post by Rocket2DMn on 2016-06-21
It looks like you need a newer Maven version (at least 3.3.3) - you're using 3.0.5.

---

