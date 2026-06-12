---
title: "Eclipse wont start..."
date: 2008-02-15
forum: Programming Talk
---

### Post by saz on 2008-02-15
I get this on the console when i try to start eclipse:
```
sa@Thorn:~$ eclipse 
searching for compatible vm...
  testing /usr/lib/jvm/java-6-sun-1.6.0.00/jre...not found
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...not found
  testing /usr/lib/jvm/java-1.5.0-sun...not found
  testing /usr/lib/j2se/1.5...not found
  testing /usr/lib/j2se/1.4...found
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension
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

then this window pops up saying this:
```
JVM terminated. Exit code=1
/usr/lib/j2se/1.4/bin/java
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
-exitdata 4b40012
-install /usr/lib/eclipse
-vm /usr/lib/j2se/1.4/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
```

someone can help me with that?

---

### Post by Shin_Gouki2501 on 2008-02-15
its seems that it can't find your installed java version.

what does :
java -version
show you?

---

### Post by saz on 2008-02-15
sa@Thorn:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

don't worry anyway, It was just some kind of java confusion, i installed all java packages again and it worked..

Pls mark this as SOLVED

Thnks for your fast reply!

---

