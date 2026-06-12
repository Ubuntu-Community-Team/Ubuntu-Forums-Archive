---
title: "Problem with Eclipse"
date: 2007-12-21
forum: Programming Talk
---

### Post by hamvil on 2007-12-21
Hi,

I've installed Eclipse 3.2 from the gutsy repository. I;ve also installad JDT and some plugins for J2EE development.

Then I've created a new dynamic web project and I've set Tomcat 5.5 as target. However after clicking on the button finish the JVm crashes reporting the following error:

JVM terminated. Exit code=1
/usr/lib/jvm/java-6-sun/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 2d800b
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-6-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 

I've tried with two different JVM (1.5 and 1.6) and I've used update-alternatives for setting the right version.

Do you have any hints?

---

### Post by realstraw on 2008-04-13
I'm having exact the same problem, is there a fix?

---

### Post by realstraw on 2008-04-13
Strange my desktop doesn't have this problem, but my t61 laptop (ubuntu 7.10, eclipse 3.2.2, java6, tomcat5.5, they have exactly the same plugin). This solved by using eclipse 3.3.

---

