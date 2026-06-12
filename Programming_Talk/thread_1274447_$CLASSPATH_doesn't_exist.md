---
title: "$CLASSPATH doesn't exist?"
date: 2009-09-24
forum: Programming Talk
---

### Post by ibob_gr on 2009-09-24
Hello

I have 8.04 which was upgraded to 8.10.

The problem I have is that I can't see java's CLASSPATH anywhere.

```

$ uname -a
... 2.6.27-14-generic #1 SMP ... x86_64 GNU/Linux

$javac -version
javac 1.6.0_10

$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)

$ echo $CLASSPATH

$

```

and also there are no JAVA or CLASSPATH when I do "env".

I can **normally** compile and run java programs that use only java standard libraries, but I try to run a java program that was compilled with some jars I downloaded but everything seems to be a mess.

So the question, is there CLASSPATH and JAVA_HOME and others somehow set in ububtu but they are hidden? Any hints are welcome.

---

### Post by falconindy on 2009-09-24
Sun's documentation seems to imply that $CLASSPATH is set for user defined classes and not the ones included with the JDK. A blank classpath isn't a bad sign. Sun has no qualms with you intentionally unsetting that variable. [Source](http://java.sun.com/j2se/1.3/docs/tooldocs/solaris/classpath.html).

What's your execution for the .jar and the error?

---

### Post by ibob_gr on 2009-09-25
I solved the problem of running the specific java app (one library was an older version).

Thanks for the answer to my main question. You seem to be right. I saw the empty CLASSPATH and was afraid that sth was messed up, but this seems to be used only for user defined classes indeed!

---

