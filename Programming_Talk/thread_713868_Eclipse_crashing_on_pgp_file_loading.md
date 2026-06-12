---
title: "Eclipse crashing on pgp file loading"
date: 2008-03-03
forum: Programming Talk
---

### Post by RyanZec on 2008-03-03
I have installed eclipse through the installer manager, install JVM 1.5 through installer manager, and the pdt plugin through the eclipse updater. eclipse loads file and i have my php projects setip correctly however when i try to load any php file, eclipse crashes with this error message:

JVM terminated. Exit code=1
/usr/lib/jvm/java-1.5.0-sun/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=nev er
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86_64
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 2e0002
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-1.5.0-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=nev er
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar

---

### Post by RyanZec on 2008-03-03
Hep on this would be great as i am really trying to make a switch to linux but i need an editor with the functionality on PhpED(basically highlighting, code templates/snippets, auto-complete) and also support C++ with compiling and debug tools(which i believe the CDT plugin for eclipse has.  Since eclipse supports both , that is great cause only using 1 editor for both my programming would be great.  is there are any other editor that support all this please let me know and i will try them out.

---

### Post by RyanZec on 2008-03-03
found the fix in another post.  un checking the browser preview options fixes the issue.  it good for me since i use external browser for my testing anyways.

---

