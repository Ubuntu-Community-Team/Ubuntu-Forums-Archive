---
title: "cant open eclipse and displays the following message"
date: 2017-12-05
forum: New to Ubuntu
---

### Post by mutta255 on 2017-12-05
```
JVM terminated. Exit code=1
/usr/bin/java
-Xms40m
-Xmx384m
-Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins
-XX:MaxPermSize=256m
-jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
-os linux
-ws gtk
-arch x86_64
-showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
--launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so
-startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
--launcher.overrideVmargs
-exitdata 17800b
-clean
-initialize
-vm /usr/bin/java
-vmargs
-Xms40m
-Xmx384m
-Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins
-XX:MaxPermSize=256m
-jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
```

---

### Post by slickymaster on 2017-12-05
Hi mutta225, welcome to the forums

See if this solution helps you: [https://stackoverflow.com/questions/31146089/eclipse-error-jvm-terminated-exit-code-1-usr-java70-jre-bin-java#31190899](https://stackoverflow.com/questions/31146089/eclipse-error-jvm-terminated-exit-code-1-usr-java70-jre-bin-java#31190899)

---

### Post by mutta255 on 2017-12-07
thanks this has helped , i installed multiple versions of java on my chromebook and all i had to do was specify witch java path to use

---

