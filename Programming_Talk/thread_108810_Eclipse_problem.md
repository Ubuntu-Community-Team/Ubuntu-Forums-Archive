---
title: "Eclipse problem"
date: 2005-12-27
forum: Programming Talk
---

### Post by bavs on 2005-12-27
I have installed Eclipse and trying to run helloworld example and when i run it says cannot connect to VM

when i type in java version at terminal it says
java version
Exception in thread "main" java.lang.NoClassDefFoundError: version

i am guessing it is using a different javac and java versions or similar
how can i solve this?

sorry java -version gives me this
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

---

### Post by flai on 2005-12-27
exactly the same here ...

---

### Post by bavs on 2005-12-27
ok got it working now
got to go preferences and make sure the java and jre for buildpath point to the same java folder

right click on your java package and properties now it works very good and also managed to use oracle jdbc driver.

one problem my statement select ename from dept; gives me
ename
ename
ename
ename

instead of listing my 4 department names
wonder why

---

