---
title: "Eclipse not starting (no errors)"
date: 2011-02-23
forum: Programming Talk
---

### Post by purdticker on 2011-02-23
Ubuntu 10.10
Eclipse Helios for Java EE Developers

```
$ java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode)
```

```
$ ./eclipse -debug
Start VM: /usr/bin/java
-Dosgi.requiredJavaVersion=1.5
-XX:MaxPermSize=256m
-Xms40m
-Xmx512m
-jar /home/cferguso/disney/eclipse/plugins/org.eclipse.equinox.launcher_1.1.0.v20100507.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /home/cferguso/disney/eclipse/eclipse
-name Eclipse
--launcher.library /home/cferguso/disney/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.1.1.R36x_v20100810/eclipse_1309.so
-startup /home/cferguso/disney/eclipse/plugins/org.eclipse.equinox.launcher_1.1.0.v20100507.jar
-exitdata 13000b
-product org.eclipse.epp.package.jee.product
-debug
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-XX:MaxPermSize=256m
-Xms40m
-Xmx512m
-jar /home/cferguso/disney/eclipse/plugins/org.eclipse.equinox.launcher_1.1.0.v20100507.jar 
Install location:
    file:/home/cferguso/disney/eclipse/
Configuration file:
    file:/home/cferguso/disney/eclipse/configuration/config.ini loaded
Configuration location:
    file:/home/cferguso/disney/eclipse/configuration/
Framework located:
    file:/home/cferguso/disney/eclipse/plugins/org.eclipse.osgi_3.6.1.R36x_v20100806.jar
Framework classpath:
    file:/home/cferguso/disney/eclipse/plugins/org.eclipse.osgi_3.6.1.R36x_v20100806.jar
Splash location:
    /home/cferguso/disney/eclipse/plugins/org.eclipse.platform_3.6.1.v201009090800/splash.bmp
Debug options:
    file:/home/cferguso/disney/eclipse/.options not found
Time to load bundles: 7
Starting application: 834

```

No errors pop up.  Not sure what to try now...

Thanks for any help!

---

### Post by purdticker on 2011-02-24
Yay I found something that helped:
[http://wiki.eclipse.org/SDK_Known_Issues#Linux_issues](http://wiki.eclipse.org/SDK_Known_Issues#Linux_issues)

> General UI problems such as buttons not being clickable or the update system not showing anything in its tree

Are you using running on GTK+ 2.17.x/2.18.x? Try declaring the GDK_NATIVE_WINDOWS environment variable and see how that goes.

$ export GDK_NATIVE_WINDOWS=true
$ ./eclipse


---

