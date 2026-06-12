---
title: "Why is this Java program working?"
date: 2007-12-15
forum: Programming Talk
---

### Post by pmdkh on 2007-12-15
You read it right. I don't understand why something is working.

I recently installed Xubuntu 7.10 on a flash drive, and I've been messing around with setting up Java. I got everything working correctly, and because of a stupid mistake of my own*, I started messing around with the CLASSPATH variable.

I ended up removing the CLASSPATH variable, and I am able to compile and run Java programs. I don't even have the current directory (./) set for the CLASSPATH, and I am able to run programs that call on different Java classes. I also don't use the -cp option for the java and javac commands.

So my question is, how does Java know where to look for other classes if I don't have CLASSPATH set?

Thanks for the help.

*The stupid mistake was trying to use a method from the Math class (java.lang.Math) in a program named Math.java. For quite a while I couldn't understand why it couldn't find the function, until it finally hit me.

---

### Post by LaRoza on 2007-12-15
Maybe it has a default.

---

### Post by ghostdog74 on 2007-12-16
what does 
echo $CLASSPATH 
say?

---

### Post by pmdkh on 2007-12-16
It says nothing because I removed everything from it when I was trying to figure out the solution to the problem I was having.

---

### Post by nitro_n2o on 2007-12-16
Which Java you have? the default one, or the one from Sun?

---

### Post by pmdkh on 2007-12-16
I am using the Sun version. The packages I have installed are sun-java6-jdk, sun-java6-jre, and sun-java6-bin.

```
ubuntu@ubuntu:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
```

---

### Post by jespdj on 2007-12-16
Since Java 5, the current directory is in the classpath by default, if you don't have the CLASSPATH environment variable set.

In fact, it is advisable to not set a CLASSPATH variable at all. If you need to run a program that needs certain directories or JAR files in the classpath, then use the "-cp" or "-classpath" switch on the command line to start it, for example:

java -cp /some/dir/with/classes:somejarfile.jar com.mypackage.MyProgram

You do not have to put the standard Java API classes in the classpath. (That's never necessary, also not on older versions of Java).

---

### Post by pmdkh on 2007-12-16
[quote="jespdj"]Since Java 5, the current directory is in the classpath by default, if you don't have the CLASSPATH environment variable set.

In fact, it is advisable to not set a CLASSPATH variable at all. If you need to run a program that needs certain directories or JAR files in the classpath, then use the "-cp" or "-classpath" switch on the command line to start it, for example:

java -cp /some/dir/with/classes:somejarfile.jar com.mypackage.MyProgram

You do not have to put the standard Java API classes in the classpath. (That's never necessary, also not on older versions of Java).[/quote]

That's interesting. Based off of your post, and what I've read about the CLASSPATH variable, I'm going to be using the -cp option from now on. Thanks for the info.

---

