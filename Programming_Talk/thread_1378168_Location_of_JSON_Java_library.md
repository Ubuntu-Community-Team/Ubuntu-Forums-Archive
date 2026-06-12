---
title: "Location of JSON Java library?"
date: 2010-01-11
forum: Programming Talk
---

### Post by DejitaruJin on 2010-01-11
Okay, I'm trying to compile some Java code in Ubuntu 9.10, and I've installed libjson-java, which my code needs. But... where did it go? I'm apparently supposed to add its location (and the location of other required libraries I can only assume were installed as dependencies) to my classpath, but it gave no indication on how to do that, and my Google searches tell me I'm the first person ever to attempt this in Linux. When I downloaded the JSON libraries for Python, it knew precisely where they were immediately. How do I direct the Java compiler to the needed files?

---

### Post by myrtle1908 on 2010-01-11
I've not used the 'libjson-java' that you speak of (I assume you got this from the repos?).  Typically I download the source from json.org and compile myself and create a JAR.  Takes less than a minute.  Once you have a JAR, place it anywhere on your disk and reference it via the -cp switch to javac and java eg.

Compile: javac -cp ./lib/json.jar MyApp.java
Run: java -cp ./lib/json.jar MyApp

These would assume your JAR is in a sub-folder named 'lib'.

I could attach a good JSON.jar if you like.

---

### Post by tcgarvin on 2011-06-10
I know this is an old thread, but for the sake of the next googler:  As of 11.04, json-lib.jar seems to be placed in /usr/share/java (along with many other jars).

As for how to tell the compiler where it is, I think you want to play with classpath.

Cheers!

---

