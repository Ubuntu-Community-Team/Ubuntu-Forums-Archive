---
title: "Eclipse wont start xubuntu 14.04"
date: 2014-08-19
forum: Programming Talk
---

### Post by geekyhawkes on 2014-08-19
I am having problems getting Eclipse to start on my Xubuntu machine but I am not sure what has changed since the last time. I used Eclipse without any issues.

Offical Sun java 8 is installed, eclipse still doesnt run the output of console reads:

```
eclipse -debug -console -consoleLog
Start VM: /usr/lib/jvm/jdk1.8.0_11/bin/java
-Xms512m
-Xmx1024m
-Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins
-XX:MaxPermSize=512M
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
-exitdata 25f000f
-debug
-console
-consoleLog
-vm /usr/lib/jvm/jdk1.8.0_11/bin/java
-vmargs
-Xms512m
-Xmx1024m
-Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins
-XX:MaxPermSize=512M
-jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar 
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Install location:
    file:/usr/lib/eclipse/
Configuration file:
    file:/usr/lib/eclipse/configuration/config.ini loaded
Configuration location:
    file:/home/geeky/.eclipse/org.eclipse.platform_3.8_155965261/configuration/
Configuration file:
    file:/home/geeky/.eclipse/org.eclipse.platform_3.8_155965261/configuration/config.ini loaded
Shared configuration location:
    file:/usr/lib/eclipse/configuration/
Framework located:
    file:/usr/lib/eclipse/plugins/org.eclipse.osgi_3.8.1.dist.jar
Framework classpath:
    file:/usr/lib/eclipse/plugins/org.eclipse.osgi_3.8.1.dist.jar
Splash location:
    /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp
Debug options:
    file:/home/geeky/Desktop/.options not found
Time to load bundles: 37
!SESSION 2014-08-19 10:46:11.409 -----------------------------------------------
eclipse.buildId=debbuild
java.version=1.8.0_11
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x86_64 -debug -console -consoleLog

!ENTRY org.eclipse.osgi 2 0 2014-08-19 10:46:13.636
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2014-08-19 10:46:13.637
!MESSAGE Bundle reference:file:../../../home/geeky/.eclipse/org.eclipse.platform_3.8_155965261/plugins/org.eclipse.m2e.usagedata_1.0.200.20111228-1245.jar was not resolved.
!SUBENTRY 2 org.eclipse.m2e.usagedata 2 0 2014-08-19 10:46:13.637
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(|(&(osgi.ee=JavaSE)(version=1.5))(&(osgi.ee=JavaSE)(version=1.6)))".
!SUBENTRY 2 org.eclipse.m2e.usagedata 2 0 2014-08-19 10:46:13.637
!MESSAGE Missing required bundle org.eclipse.epp.usagedata.gathering_0.0.0.

!ENTRY org.eclipse.osgi 2 0 2014-08-19 10:46:13.641
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2014-08-19 10:46:13.642
!MESSAGE Bundle org.eclipse.m2e.usagedata_1.0.200.20111228-1245 [219] was not resolved.
!SUBENTRY 2 org.eclipse.m2e.usagedata 2 0 2014-08-19 10:46:13.642
!MESSAGE Missing required bundle org.eclipse.epp.usagedata.gathering_0.0.0.
!SUBENTRY 2 org.eclipse.m2e.usagedata 2 0 2014-08-19 10:46:13.642
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(|(&(osgi.ee=JavaSE)(version=1.5))(&(osgi.ee=JavaSE)(version=1.6)))".
Starting application: 2235
____________________________
Welcome to Apache Felix Gogo

g! No bp log location saved, using default.
[000:000] Browser XEmbed support present: 1
[000:000] Browser toolkit is Gtk2.
[000:000] Using Gtk2 toolkit
[000:000] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:000] No bp log location saved, using default.
[000:000] Browser XEmbed support present: 1
[000:000] Browser toolkit is Gtk2.
[000:000] Using Gtk2 toolkit
No bp log location saved, using default.
[000:000] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:000] No bp log location saved, using default.
java version "1.7.0_55"
OpenJDK Runtime Environment (IcedTea 2.4.7) (7u55-2.4.7-1ubuntu1)
OpenJDK 64-Bit Server VM (build 24.51-b03, mixed mode)
```

I am not sure why OPENJDK is still listed just before the crash when the log starts with Sun java 1.8?

Thanks Andy

---

### Post by lordbah2 on 2014-08-19
I am by no means an expert on Eclipse, just used it a few times. But doesn't it look like that 'bundles' is requiring specific versions of Java - 1.5 or 1.6 - and choosing not to work with 1.8 (or 1.7 for that matter)? Maybe there's an update to the bundle or maybe you have to use one of those 'alternatives' commands to pick a different version of Java for long enough to launch Eclipse?

---

### Post by geekyhawkes on 2014-08-20
Thanks for the suggestion.  I actually "solved" the issue by installing Eclipse 4.2 and then importing my existing work space.

---

