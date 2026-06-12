---
title: "How to find Java install directory?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by VolvoPunch on 2008-09-02
I need to find out where the Java Runtime Environment files have been installed. 

Whats the correct directory? 
```

root@test-corp-esx-03:/# find ./ -name java
./etc/java
./etc/alternatives/java
./var/lib/dpkg/alternatives/java
./root/jre1.5.0_11/bin/java
./usr/bin/java
./usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/bin/java
./usr/lib/jvm/java-1.5.0-sun-1.5.0.15/bin/java
./usr/lib/jvm/java-6-sun-1.6.0.06/jre/bin/java
./usr/lib/jvm/java-6-sun-1.6.0.06/bin/java
./usr/share/java
./usr/share/doc/libcommons-launcher-java/examples/example/src/java
root@test-corp-esx-03:/#

```

```

root@test-corp-esx-03:/opt/SUNWut/webadmin/conf# java -version                  java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)
root@test-corp-esx-03:/opt/SUNWut/webadmin/conf#

```

This is why I need to know
```

root@test-corp-esx-03:/opt/SUNWut/webadmin/conf# /opt/SUNWut/lib/utwebadmin start
No Java Runtime Environment (JRE) found at /usr/share/java.
root@test-corp-esx-03:/opt/SUNWut/webadmin/conf#

```

---

### Post by VolvoPunch on 2008-09-02
Bump because I never get any help in Ubuntuforums.org! :confused:

---

### Post by t0p on 2008-09-02
> **VolvoPunch said:**
> Bump because I never get any help in Ubuntuforums.org! :confused:

Whoa dude chill out!  You posted this thread only a few minutes ago! Be patient, someone who can help you will be along soonish.

---

### Post by VolvoPunch on 2008-09-02
> **t0p said:**
> Whoa dude chill out!  You posted this thread only a few minutes ago! Be patient, someone who can help you will be along soonish.

No I post here quite often but I rarely get any help. Anyways the directory turned out to be 

```
/usr/lib/jvm/java-6-sun-1.6.0.06
```

:guitar:

---

### Post by t0p on 2008-09-02
Incidentally, your search has narrowed it down to 2 possible locations - 

/usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/bin/java

/usr/lib/jvm/java-6-sun-1.6.0.06/jre/bin/java

- so I figure it won't be too hard for you to figure out yourself...

**EDIT:** oh look! You *did* figure it out!

---

### Post by jamesstansell on 2008-09-02
There are several other ways you could have found the directory you wanted to use, but I won't belabor the point.

I often use the form /usr/lib/jvm/java-6-sun (note that it's a symbolic link) so that apps continue to work even after upgrading (i.e. the Java 6u7 security patch should be in the archives soon, and will replace the old *1.6.0.06 directory with *1.6.0.07.)

Sincerely,

-james.

---

### Post by kansasnoob on 2008-09-02
You know you can install sun-java6-*** from synaptic?

I always install all sun-java6-**** but -docs and -source.

---

### Post by psyncho on 2009-06-23
I think >which java
will do it

---

