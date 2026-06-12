---
title: "classpath in linux..."
date: 2010-09-22
forum: Programming Talk
---

### Post by miko5054 on 2010-09-22
i cant run any program im receiving for everything 


```
    Code:
 Exception in thread "main" java.lang.NoClassDefFoundError: bank/aaa
Caused by: java.lang.ClassNotFoundException: bank.aaa
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: bank.aaa. Program will exit.
```
im guessing that is class-path issue but which path i need to set, to were???

im using ubuntu and eclipse ...

---

### Post by kahumba on 2010-09-22
1) If you don't know where/what "bank/aaa" is then no one can help you.
2) Setting classpath under eclipse is easy to find out by... googling!

---

