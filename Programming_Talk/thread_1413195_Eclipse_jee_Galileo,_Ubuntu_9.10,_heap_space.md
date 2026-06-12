---
title: "Eclipse jee Galileo, Ubuntu 9.10, heap space"
date: 2010-02-22
forum: Programming Talk
---

### Post by munaf on 2010-02-22
Hi everyone.
I'm having tremendous problems with my Eclipse Jee Galileo and Ubuntu 9.10 setup. Not one session goes without a heapspace or a permgen error:

This is my config:
munaf@Optimus:~/Eclipses/Eclipse_jee_Galileo$ cat eclipse (to get rid of the button-click bug)
```
#! /bin/bash
export GDK_NATIVE_WINDOWS=1
/home/munaf/Eclipses/Eclipse_jee_Galileo/eclipse_r &
```

```

munaf@Optimus:~/Eclipses/Eclipse_jee_Galileo$ cat eclipse.ini
-startup
plugins/org.eclipse.equinox.launcher_1.0.201.R35x_v20090715.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.200.v20090520
-product
org.eclipse.epp.package.jee.product
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
2048m
-vmargs
-Dosgi.requiredJavaVersion=1.5
-XX:MaxPermSize=1024m
-Xms80m
-Xmx2048m


```



This error occurred when I started up and did nothing!


```
Exception in thread "Java indexing" java.lang.OutOfMemoryError: Java heap space
	at org.eclipse.jdt.internal.compiler.util.HashtableOfObject.<init>(HashtableOfObject.java:38)
	at org.eclipse.jdt.internal.compiler.util.HashtableOfObject.rehash(HashtableOfObject.java:139)
	at org.eclipse.jdt.internal.compiler.util.HashtableOfObject.put(HashtableOfObject.java:112)
	at org.eclipse.jdt.internal.core.index.DiskIndex.copyQueryResults(DiskIndex.java:349)
	at org.eclipse.jdt.internal.core.index.DiskIndex.mergeWith(DiskIndex.java:522)
	at org.eclipse.jdt.internal.core.index.Index.save(Index.java:191)
	at org.eclipse.jdt.internal.core.search.indexing.IndexManager.saveIndex(IndexManager.java:659)
	at org.eclipse.jdt.internal.core.search.indexing.AddJarFileToIndex.execute(AddJarFileToIndex.java:204)
	at org.eclipse.jdt.internal.core.search.processing.JobManager.run(JobManager.java:401)
	at java.lang.Thread.run(Thread.java:619)
```



```

munaf@Optimus:~/Eclipses/Eclipse_jee_Galileo$ free -m
             total       used       free     shared    buffers     cached
Mem:          3016       1573       1442          0         69        705
-/+ buffers/cache:        799       2216
Swap:         2910          0       2910


```

I desperately need help with this. Any hints would be appreciated. Thanks in advance.

---

### Post by GregBrannon on 2010-02-22
I don't know what your problem is.  I can only offer the following output from my own eclipse.ini file from my installation which works just fine:

```
-startup
plugins/org.eclipse.equinox.launcher_1.0.201.R35x_v20090715.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.0.200.v20090519
-product
org.eclipse.epp.package.jee.product
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
256m
-vmargs
-Dosgi.requiredJavaVersion=1.5
-XX:MaxPermSize=256m
-Xms40m
-Xmx512m
```

Very similar to yours; looks like 64-bit, same build, and pretty much identical to yours except for the memory settings which are double to quadruple mine.  Why don't you try cranking your memory settings down.

Good luck!

---

