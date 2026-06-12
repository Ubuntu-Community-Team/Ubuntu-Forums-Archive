---
title: "Eclipse Freezes when debugging 2nd debug after terminating application"
date: 2009-03-04
forum: Programming Talk
---

### Post by Crimsonblah on 2009-03-04
I've been struggling with this problem for quite a while so I'm hoping that one of ya'll can help me out - I'm happy to post more details if necessary.

It is *similar* the problem listed in this post, but I have tried all solutions there (I only have one project) and nothing has helped so far... [http://ubuntuforums.org/showthread.php?p=6043402](http://ubuntuforums.org/showthread.php?p=6043402)

I think its related to Java, see the code block at the bottom. 

I am currently running Eclipse with the CDT and SVN (Subclipse) plugins. I've been running in this configuration for over 6 months, debugging and testing my application. If I load up Eclipse and hit "debug", I am usually able to get the application to debug without problems. This correspond to the attached screenshot which has the name "...normal and working.jpg"

However, if I hit the "kill" red stop button while debugging (instead of exiting out of the application by closing it hitting the "x" button), the NEXT time I debug I experience funny behavior. One of the two following things happens next time I try to debug the program. 
1. The program will *appear* to load up, but my GUI front end  will not appear and  gdb/mi window will be listed as "Suspended" (see the "Eclipse is responsive" picture attached). The first break point, usually placed on gtk_init, is NOT hit. At this point I cannot cause the system to debug properly. 
2. Eclipse will freeze and become non-responsive while the status bar in the lower right hand corner will list either 50% or 85% (see the "Eclipse is frozen..." screenshot attached). If I click on the window at this time, the Eclipse GUI will become non-responsive (failing to update its screen) and the only option that I have had is to end the process, which I do through the system monitor.

The only solution I have to #1 above is to exit eclipse, at which point I receive a "Progress information" screen which states that the "user operation is waiting for  background work to complete". I've found this is linked to the Java process, but the Java process is listed as "sleeping". By killing the java process I can start the whole process over again (reload Eclipse, rinse and repeat and attempt to debug).

If I kill the Java process situation #2 above, I receive the following error message:
```
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
-exitdata 80008
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-6-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 
```

My current workaround for this is to restart Eclipse every time I want to debug the application, but this doesn't always work (sometimes it still freezes) and I'm really looking to root cause this. Any suggestions that you might have (reinstalling Java, or something like that) would be appreciated. I'm happy to provide more information if necessary. 

Thanks for your help!

---

### Post by Crimsonblah on 2009-03-06
Still haven't been able to solve this error. I think something is seriously corrupt in Eclipse :-/ Anyone have any recommended advice?

---

