---
title: "Eclipse will not start"
date: 2007-11-01
forum: Programming Talk
---

### Post by Student Driver on 2007-11-01
Gutsy Gibbon, and a new user to Ubuntu (but on/off user of Linux for a long time) and added this via Synaptic.  So, I get a nice graphical failure so I launched it from the terminal and get the following:```

me@ubuntop:~$ eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...not found
  testing /usr/lib/jvm/java-1.5.0-sun...not found
  testing /usr/lib/j2se/1.5...not found
  testing /usr/lib/j2se/1.4...found
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/eclipse/core/launcher/Main (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

```

Any ideas?  Thanks.

---

### Post by dgrif on 2007-11-01
try this:

```
sudo apt-get install sun-java6-jdk
```

that should install the JDK, and if you want javadocs, do the same with sun-java6-doc 

I'm on a fresh install and accidentally installed jdk5 first, uninstalled, then installed jdk6, and it messed up a ton of sym links and I just got all the kinks worked out.  Let me know if it works

darel

---

### Post by Student Driver on 2007-11-01
Thanks, I will give that a shot when I get home today from work.  It wasn't like I was dependent on Java 1.4, but have you found any issues running common applets in Java 6?

---

### Post by Student Driver on 2007-11-01
Yep, that worked.  I thought I had the SDK for 1.4 but I might not.  I might poke around a bit and see what's up.  Thanks.

---

### Post by dgrif on 2007-11-01
no problem :)

---

