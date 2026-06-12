---
title: "Configure Eclipse on U MATE 18.04"
date: 2018-10-13
forum: Programming Talk
---

### Post by gsahli on 2018-10-13
In the old days... Eclipse installed from repositories and just worked. It's not working on Ubuntu MATE 18.04.
I get this not-so-helpful error message:
```

!SESSION Fri Oct 12 17:40:11 CDT 2018 ------------------------------------------
!ENTRY org.eclipse.equinox.launcher 4 0 2018-10-12 17:40:11.414
!MESSAGE Exception launching the Eclipse Platform:
!STACK
java.lang.ClassNotFoundException: org.eclipse.core.runtime.adaptor.EclipseStart$
        at java.base/java.net.URLClassLoader.findClass(URLClassLoader.java:466)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:566)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:499)
        at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:626)
        at org.eclipse.equinox.launcher.Main.basicRun(Main.java:584)
        at org.eclipse.equinox.launcher.Main.run(Main.java:1438)
        at org.eclipse.equinox.launcher.Main.main(Main.java:1414)
```
I think this is a java problem.
I have the default openjdk installed
```
$ java -version
openjdk version "10.0.2" 2018-07-17
OpenJDK Runtime Environment (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.2)
OpenJDK 64-Bit Server VM (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.2, mixed mode)
```

What's up?

---

### Post by gsahli on 2018-10-14
BTW,
LiClipse, which has its own java vm installed, does work.

---

### Post by gsahli on 2018-10-15
Installed version 4.9 from Eclipse site, and it works with java 11!

---

