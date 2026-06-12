---
title: "problem in starting eclipse for first time"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by smita raj on 2008-11-18
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
-exitdata 24000a
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-6-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 

i am getting above error msg while opening eclipse IDE.

---

### Post by waffen on 2008-12-10
Whats versions of Eclipse, Ubuntu, java do you use? put the complete message from the console

---

### Post by Michael.Godawski on 2008-12-10
hi smita raj,

how did you install eclipse on your machine? Via the terminal or from the homepage?

Usually the command to run eclipse is:

```
/opt/eclipse/eclipse 
```

---

