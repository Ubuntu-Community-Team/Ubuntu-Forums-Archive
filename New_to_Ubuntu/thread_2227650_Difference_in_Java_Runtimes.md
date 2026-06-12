---
title: "Difference in Java Runtimes"
date: 2014-06-03
forum: New to Ubuntu
---

### Post by ViliX64 on 2014-06-03
I've discovered, that there are three different JDK sources:


[LIST]
[*]IBM JDK
[*]OpenJDK
[*]Oracle JDK
[/LIST]

What is the difference between them? I though, that there is only one JRE and it's being developed by Oracle.

---

### Post by slickymaster on 2014-06-03
The difference between Oracle JDK and Open JDK are a consequence of the goal of each one (OpenJDK is meant to be the reference implementation, open to the community, while Oracle is meant to be a commercial one). They both have "almost" the same code of the classes in the Java API; but the code for the virtual machine itself used to be different, and when it comes to libraries, OpenJDK tends to use open libraries while Oracle tends to use closed ones.
As of Java 7, Oracle replaced a number of closed source parts with their open source equivalent. The code for the virtual machine is actually almost completely identical, but there are a couple of libraries which are closed. For instance, the [font library]("http://technfun.wordpress.com/2013/01/18/last-difference-openjdk-oracle-jdk").

For the differences between IBM JDK and Oracles', they mainly reside in the fact that IBM uses a different JIT and Garbage collectors since IBM's JVM has a different heap structure than Oracle's JVM. Also, IBM JVM has a different kind of compiler known as Ahead Of time Compiler (AOT compiler), which work to reduce some overhead form JITing code whenever JVM starts. AOT compiler memory maps pre-compiled class file so that they don't need to go JIT compilation when IBM's JVM runs.

---

