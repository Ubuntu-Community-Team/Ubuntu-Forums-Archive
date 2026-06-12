---
title: "Installing Eclipse Europa in Hardy"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by aor_dreamer on 2008-05-12
Oh well, here goes my first post,
I'm desperately trying to install Eclipse Europa in Hardy using the how-to in [http://www.ubuntued.com/?p=40]("http://www.ubuntued.com/?p=40"), but with no luck. I did follow all the steps and when I run Eclipse I get these:

```
JVM terminated. Exit code=13
/usr/bin/java
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
-jar /opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /opt/eclipse/eclipse
-name Eclipse
--launcher.library /opt/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.3.R33x_v20080118/eclipse_1023.so
-startup /opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar
-exitdata 4d801c
-clean
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
-jar /opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar 
```

At first I thought that it was a Java problem (as usual) but then I followed the link of /usr/bin/java, which points to /etc/alternatives/java, which points to /usr/lib/jvm/java-1.5.0-sun/jre/bin/java, which :popcorn: looks OK. 
I took a quick look in the forum but didn't find anything helpful. 
Any ideas??

Thanks.

---

### Post by hyper_ch on 2008-05-12
why didn't you simply:
```

sudo apt-get install eclipse

```?

---

### Post by aor_dreamer on 2008-05-12
> **hyper_ch said:**
> why didn't you simply:
```

sudo apt-get install eclipse

```?

Eclipse 3.3 is not available in the Ubuntu repository yet and I need this version because the plugins I'm using require it.

---

### Post by Inxsible on 2008-05-12
> **hyper_ch said:**
> why didn't you simply:
```

sudo apt-get install eclipse

```?
I don't know about Hardy, but Ubuntu repos until Gutsy didn't have Eclipse Europa in the repos.

@ the op: You can simply explode the downloaded eclipse tar.gz wherever you like. There is nothing else to do except create an icon or a launcher for it.

---

### Post by Thingymebob on 2008-05-12
Are you by any chance running 64bit. If you are then you will need a 32bit jvm

---

### Post by aor_dreamer on 2008-05-12
> **Thingymebob said:**
> Are you by any chance running 64bit. If you are then you will need a 32bit jvm

Actually I am, I didn't know that! 
Thanks!

---

