---
title: "what should be my ANT_HOME"
date: 2014-01-18
forum: Programming Talk
---

### Post by IAMTubby on 2014-01-18
Hello,
 I installed ant using **sudo apt-get install ant**, but I don't know what path should be set as ANT_HOME. 

Some details which could be useful in answering my query
1.**ant -v**
```
root@Inspiron-1545:/usr/bin# ant -vUnable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-openjdk/lib/tools.jar
Apache Ant(TM) version 1.8.2 compiled on August 19 2011
Trying the default build file: build.xml
Buildfile: build.xml does not exist!
Build failed

```

2.**whereis ant**
```
root@Inspiron-1545:/usr/bin# whereis ant
ant: /usr/bin/ant /usr/share/ant /usr/share/man/man1/ant.1.gz

```

Please let me know additional details I can provide.

PS : In general, for other packages too, how do you find out where it was installed if it was done using sudo apt-get install <packagename> Probably, the reply to the query would answer this ?

---

### Post by Habitual on 2014-02-04
Have a look at [http://ant.apache.org/manual/running.html#envvars](http://ant.apache.org/manual/running.html#envvars)

---

