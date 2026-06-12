---
title: "OpenJDK and Sun (Oracle) JDK"
date: 2011-09-09
forum: Programming Talk
---

### Post by dwhitney67 on 2011-09-09
I prefer to use the Sun (Oracle) JDK on my system, and thus I have it installed, and I thought I had removed OpenJDK.  Yet when I examine both 'java' and 'javac', I see the following:
```

$ ls -l /usr/bin/java /usr/bin/javac
lrwxrwxrwx 1 root root 22 2010-10-09 00:04 /usr/bin/java -> /etc/alternatives/java*
lrwxrwxrwx 1 root root 23 2010-10-12 21:04 /usr/bin/javac -> /etc/alternatives/javac*

$ ls -l /etc/alternatives/java /etc/alternatives/javac
lrwxrwxrwx 1 root root 40 2010-10-09 00:04 /etc/alternatives/java -> /usr/lib/jvm/java-6-openjdk/jre/bin/java
lrwxrwxrwx 1 root root 33 2010-10-12 21:04 /etc/alternatives/javac -> /usr/lib/jvm/java-6-sun/bin/javac

```
Note the difference... one is using openjdk, the other java-6-sun.  Is this normal?

When browsing the installed packages via the Synaptic Package Manager, I see the java-6-sun installed, and open-jdk as not installed (see attached image).

Should this be a concern?

---

### Post by dwhitney67 on 2011-09-09
Never mind.  I just realized in this late hour, I was confusing JDK with JRE.  Apparently I still had the OpenJDK JRE package still installed.  By removing it, now my system is all well.

```

ls -l /etc/alternatives/java /etc/alternatives/javac
lrwxrwxrwx 1 root root 36 2011-09-09 21:43 /etc/alternatives/java -> /usr/lib/jvm/java-6-sun/jre/bin/java
lrwxrwxrwx 1 root root 33 2010-10-12 21:04 /etc/alternatives/javac -> /usr/lib/jvm/java-6-sun/bin/javac

```

---

### Post by sammiev on 2011-09-09
I just checked on my setup and I don't show anything for OpenJDK when I type in the same as you. I would work on removing it. GL :)

---

