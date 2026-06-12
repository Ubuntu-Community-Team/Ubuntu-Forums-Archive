---
title: "Java, Junit problem"
date: 2007-04-12
forum: Programming Talk
---

### Post by Spunky Alven on 2007-04-12
Hi trying to get Junit to work on Ubuntu Feisty with no results. I have installed Junit but when i try to compile my test, the package doesn't exist. 

```
package junitfaq;
import org.junit.*;
import static org.junit.Assert.*;
import java.util.*;
```

> Test.java:2: package org.junit does not exist
import org.junit.*;
^
Test.java:3: package org.junit does not exist
import static org.junit.Assert.*;


So how do i get the java compiler to find the junit packages?

---

### Post by smokey edgy on 2007-04-13
How are you compiling this? Do you have the junit.jar included in your classpath?

---

### Post by phossal on 2007-04-13
The easiest way to drop .jar files into your classpath is to stick them in the "extensions" folder within the JRE. You'll need to restart your IDE; restart eclipse if you use it. The folder is something like <path_to_jdk>/jre/bin/ext/

---

### Post by amohanty on 2007-04-13
Another easy way is to:
- download junit binary distribution
- untar in /usr/local
- link to jars in /usr/local/junit.../lib in /usr/share/java

javac should pick it up automatically.
Or else set the CLASSPATH env variable to be a list of colon separated jars. If you need I can post a script I use to do that for me.

HTH
AM

---

### Post by smokey edgy on 2007-04-13
I agree with both of approaches you guys suggested. But I probably wouldn't make it a habit of sticking every jar in those directories as that would mean every project you have would include them in the classpath. JUnit is probably a good exception to this rule, as it probably applies across projects. But certain jars may be more project specific.

---

### Post by amohanty on 2007-04-13
> **smokey edgy said:**
> I agree with both of approaches you guys suggested. But I probably wouldn't make it a habit of sticking every jar in those directories as that would mean every project you have would include them in the classpath. JUnit is probably a good exception to this rule, as it probably applies across projects. But certain jars may be more project specific.

Well including everything in the classpath is not necessarily a bad thing. with JIT not all jars/classes will be loaded at app startup. On the plus side, it may make things easier for noobs.

Just my 0.02

AM

---

### Post by phossal on 2007-04-13
> **smokey edgy said:**
> I agree with both of approaches you guys suggested. But I probably wouldn't make it a habit of sticking every jar in those directories as that would mean every project you have would include them in the classpath. JUnit is probably a good exception to this rule, as it probably applies across projects. But certain jars may be more project specific.

*Many* third-party .jar files *suggest* using the /ext folder. For example, you're not *supposed* to import while using MySQL's .jar. itext, looks, javamail, etc... They're updated and used often enough that making them separate from your project is often helpful. For the record, I *do* make it a habit of putting whatever I can in the /ext folder.

---

