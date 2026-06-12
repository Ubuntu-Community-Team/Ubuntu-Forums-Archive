---
title: "Stupidly noobish Java question"
date: 2006-08-22
forum: Programming Talk
---

### Post by Geekbeard on 2006-08-22
So, I downloaded and installed the Java SDK in a special folder, /java-sdk.

But if I want to compile a program, I have to go 

$ sudo /java-sdk/jdk1.5.0_08/bin/javac /Hello.java

instead of 

$ sudo javac /Hello.java

How can I fix/change this?

---

### Post by Gustav on 2006-08-22
Make a link from /usr/bin/ to /java-sdk/jdk1.5.0_08/bin/javac (and /java-sdk/jdk1.5.0_08/bin/java)

---

### Post by LordHunter317 on 2006-08-22
Err umm, no, don't do that.

Add the proper parts of /java-sdk to your PATH.  Globally define it in /etc/.bashrc or locally in ~/.bashrc.  Don't forget JAVA_HOME as well.

---

### Post by hod139 on 2006-08-22
Sun's JDK and JRE are in the repository, you don't have to download anything manually.  For the JDK, you only have to install the package:
 sun-java5-jdk
and then run the command
```

sudo update-java-alternatives -s java-1.5.0-sun

```
if you wish Sun's java to become the default on the system.

---

### Post by chonger on 2006-08-22
You shouldn't use sudo to compile. Why would javac need admin (root) privilleges to create a file? 

Once you stop using sudo, you might find another issue where you have to specify the full path to javac to compile. You need to make sure javac is in your $PATH variable. See this article:

[http://www.ibiblio.org/gferg/ldp/practical_linux_guide/x80.html](http://www.ibiblio.org/gferg/ldp/practical_linux_guide/x80.html)

---

