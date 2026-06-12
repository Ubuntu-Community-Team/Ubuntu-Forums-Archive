---
title: "I just installed eclipse. It wont open. It shows: JVM terminated.Exit Code=1."
date: 2009-03-17
forum: Programming Talk
---

### Post by the_analyzer on 2009-03-17
While opens, I got the message error containing:

JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=nev er
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 1e8012
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=nev er
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar


After getting this I installed Java Runtime Environment, cause I thought it would be the problem (its a fresh system, just formated, running ubuntu)
help me please..

---

### Post by click4851 on 2009-03-17
just did a fresh install of Intrepid, and happened to have just loaded this as well from Synaptic, along with a few other eclipse-related packages. Opened and ran fine, did the little "hello world" tutorial. Is it possible you need one of those other eclipse-related packages?

---

### Post by the_analyzer on 2009-03-17
I did not got it quite well, but What I'll do is: Im gonna install eclipse from synaptic package manager, right?

---

### Post by click4851 on 2009-03-17
I would, if only based on my 30 min of experience with eclipse. Synaptic will defintely get you farther than you are now....:)

You could also click SYSTEM--->ADD/REMOVE PROGRAMS--->and type in "eclipse", search and install from there. Whichever you are most comfortable with.

---

### Post by lvleph on 2009-03-17
Maybe reinstall Java? It seems as though you have a problem with Java, but I could be wrong.

---

### Post by HotCupOfJava on 2009-03-17
> **the_analyzer said:**
> 
After getting this I installed Java Runtime Environment, cause I thought it would be the problem (its a fresh system, just formated, running ubuntu)
help me please..

You will probably need the Java Development Kit, not just the runtime environment.

---

### Post by jespdj on 2009-03-18
Hey, I saw the exact same question in another forum, and replied to it: [http://ubuntuforums.org/showthread.php?t=1098960](http://ubuntuforums.org/showthread.php?t=1098960)

Please don't crosspost...

---

### Post by darksideforge on 2009-03-20
> **click4851 said:**
> just did a fresh install of Intrepid, and happened to have just loaded this as well from Synaptic, along with a few other eclipse-related packages. Opened and ran fine, did the little "hello world" tutorial. Is it possible you need one of those other eclipse-related packages?

click,
would you mind taking a look at this post [http://ubuntuforums.org/showthread.php?t=1101462]("http://ubuntuforums.org/showthread.php?t=1101462") and seeing if you can help me?
thanks.

---

