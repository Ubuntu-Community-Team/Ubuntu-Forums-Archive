---
title: "directory for java jdk"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by meteora184 on 2011-10-17
Hello all so recently i installed ubuntu 11.1 on my toshiba laptop. I was trying to get netbeans running and it said it could not find the correct jdk necessary to run netbeans.

Now i have openJDK Java 7 Runtime installed, is this what I should have? and if so where would I find the directory of this so I can specify it in the netbeans installer?

---

### Post by 11jmb on 2011-10-17
do you have openjdk java 7 jdk installed?

---

### Post by cavh on 2011-10-17
Presuming you have the JDK installed and not just the JRE (11jmb asks you the right question ;)), in a terminal:

```
whereis java

```

you need the folder with 'bin' in the path. In my system, the location is /usr/bin/java.

See also [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

---

### Post by meteora184 on 2011-10-17
first of all you are right i did not have the actual jdk installed. the fact that it is called openjdk confused me. 
I installed the jdk and then the installer managed to find the folder so thanks a bunch 
this forum never ceases to let me down!

---

### Post by 11jmb on 2011-10-17
great to hear :)
please remember to mark the thread as solved

---

