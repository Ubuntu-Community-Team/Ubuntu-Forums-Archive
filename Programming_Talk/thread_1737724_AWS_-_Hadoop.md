---
title: "AWS - Hadoop"
date: 2011-04-23
forum: Programming Talk
---

### Post by ubu@ on 2011-04-23
[COLOR=DimGray][I]AWS  = amazon web service.
[/I][/COLOR]

Hello world,

I'm trying to write a *mapper*\*reducer* classes but ECLIPSE wont recognize *hadoop* package.

I have the AWS **(amazon web service**) plug-in and I used it till now and it worked perfectly. ('till I tried the map-reduce platform, using hadoop package)
searching with google, I saw there are some jars I need to import, but no tutorial for Ubuntu.


programming language: JAVA.
error lines are:

```
import org.apache.hadoop.mapreduce.Mapper; 
import org.apache.hadoop.mapreduce.Reducer;
```thanks, 
ubu@

---

### Post by ubu@ on 2011-04-24
give me something...

---

### Post by ubu@ on 2011-04-24
odd but I'm solving my own thread:

download "hadoop.jar" for eclipse -> add it to the project -> right click on the jar in the project and press "buid path".

thanks anyway,
ubu@

---

