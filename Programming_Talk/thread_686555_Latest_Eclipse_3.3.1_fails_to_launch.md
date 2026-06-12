---
title: "Latest Eclipse 3.3.1 fails to launch"
date: 2008-02-03
forum: Programming Talk
---

### Post by adrynov on 2008-02-03
I have used Eclipse for learning purposes only, so I am not as experienced as you are. Please help.

I have been using version 3.3.1.1 (M20071023-1652) but with constant abuse of it it turned into a beast. I want to substitute it with newer version - clean install.

When I download latest Europa from Eclipse site and launch it, it fails to launch with the following swearing

VM terminated. Exit code=13
/usr/bin/java
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
-jar /home/andrei/Desktop/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /home/andrei/Desktop/eclipse/eclipse
-name Eclipse
--launcher.library /home/andrei/Desktop/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.2.R331_v20071019/eclipse_1021.so
-startup /home/andrei/Desktop/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar
-exitdata 13c801e
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
-jar /home/andrei/Desktop/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar


I do not understand it - it is basically the same version, slightly updated. The old one starts well and runs, the new one doesn't

running Eclipse with the -clean option or cleaning the config directory do not help

I run Ubuntu 7.10 64-bit, sun java JDK 1.6

---

