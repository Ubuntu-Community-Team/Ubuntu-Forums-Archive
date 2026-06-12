---
title: "Problem launching Eclipse"
date: 2006-08-30
forum: Programming Talk
---

### Post by Ferio on 2006-08-30
It never launches entirely, but it returns this code:
```
JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/share/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 7ac001d
-install /usr/share/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/share/eclipse/startup.jar
```
Any idea about what it could be?

---

### Post by Ferio on 2006-08-30
It was a bug, I've solved it following this Howto: [http://www.ubuntuforums.org/showthread.php?t=201378](http://www.ubuntuforums.org/showthread.php?t=201378)

---

### Post by nephish on 2006-08-30
which version of java are you using ? i could not get eclipse to work with the main ubuntu java, i had to have sun java installed. Also, did you install eclipse with apt? or just download the directory and execute it from the eclipse file in the eclipse folder ( the easiest way, i have found )
let us know.

---

