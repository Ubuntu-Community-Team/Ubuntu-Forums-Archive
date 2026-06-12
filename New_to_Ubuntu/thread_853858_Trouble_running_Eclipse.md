---
title: "Trouble running Eclipse"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by chetan.89 on 2008-07-08
Hi !

I use Ubuntu 7.10 Gutsy Gibbon (64-bit version) and have some troubles running Eclipse under it. I get the following error msg.

> 
JVM terminated. Exit code=1
/usr/lib/j2se/1.4/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86_64
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 718025
-install /usr/lib/eclipse
-vm /usr/lib/j2se/1.4/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar


I saw many other posts relating to the same problem but couldn't resolve. Please help me out.

Thank you very much !
Chetan.

---

### Post by Diabolis on 2008-07-14
I googled this **JVM terminated. Exit code=1 **and most of the post in other forums are from 2006. Some of them say that they fixed the problem by moving files from one folder to another, deleting meta files and updating path environment variables.

How did you installed JDK and eclipse? Maybe getting the latest version from their original sites will fix your problem.

From your post I figured you are using java 1.4, so this makes a lot of sense:
> Somehow the line 
--launcher.XXMaxPermSize256M 
had been split into two lines 
--launcher.XXMaxPermSize 
256M 
Correcting this. eliminated the problem.
> If you have the sun JVM 1.4.2.x  or 1.5  increase the heap storage with the Xmx Parameter! 
I had the same problem. I changed from Xmx256 to Xmx350

The solutions modified the **eclipse.ini **file, some claim to have fixed it by removing this parameter: **-Xshareclasses:singleJVM,keep**

[read through this thread for more solutions]("http://www.eclipseplugincentral.com/index.php?name=PNphpBB2&file=viewtopic&t=2556&postdays=0&postorder=asc&start=15&sid=95c30bc622df29eea30c10ceaedc9bc0")

[more info about the JVM]("http://publib.boulder.ibm.com/infocenter/javasdk/v1r4m2/index.jsp?topic=/com.ibm.java.doc.diagnostics.142/html/messageandcode.html")

---

### Post by chetan.89 on 2008-07-15
Hi Diabolis !

Thank you so much for your reply. My Eclipse started working yesterday when I installed the latest versions of JDK and JRE :).

Regards,
Chetan.

---

