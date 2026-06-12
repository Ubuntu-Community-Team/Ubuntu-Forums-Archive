---
title: "Problem with Eclipse 3.3"
date: 2007-11-23
forum: Programming Talk
---

### Post by lin4crew on 2007-11-23
I was surprised to see that the package version of Eclipse in Gutsy was 3.2 when 3.3 has been out quite a while.  At first I thought it was no big deal.  I installed Sun's JDK 6 (the Ubuntu way) and then got the Eclipse package (the Ubuntu way).  It started up just fine.  Then I discovered that a plugin I need to use requires Eclipse 3.3.  So I uninstalled Eclipse (the Ubuntu way) and downloaded 3.3 for Linux from the Eclipse website.  I extracted it and put it in /opt (as /opt/eclipse).

But when I try to run it I get the following error:

JVM terminated. Exit code=13
/usr/bin/java
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx512m
-jar /opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /opt/eclipse/eclipse
-name Eclipse
--launcher.library /opt/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.2.R331_v20071019/eclipse_1021.so
-startup /opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar
-exitdata 190011
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx512m
-jar /opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar

If it matters, this is a 64-bit install of Ubuntu 7.10.

Thanks in advance.

---

### Post by kabronkline on 2007-11-24
Open a terminal (press and hold ctrl + alt + t) 
```

opt/eclipse/eclipse -vm /usr/lib/jvm/java-6-sun/bin
 
```

You're eclipse is launching with an outdated JRE. If you installed the Java 6 JDK via synaptic, the above command should be fine. 

I'm assuming Eclipse finds the outdated JRE because of some type of environmental variables, anybody know how this actual works and/or how to actual change the default behavior of Eclipse (and other Java based apps) to launch using a system prefered JRE?

---

### Post by lin4crew on 2007-11-24
That didn't help.  It just changed my error message to:

JVM terminated. Exit code=13
/usr/lib/jvm/java-6-sun/bin/java
-Xms40m
-Xmx256m
-jar /opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /opt/eclipse/eclipse
-name Eclipse
--launcher.library /opt/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.2.R331_v20071019/eclipse_1021.so
-startup /opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar
-exitdata 62800b
-vm /usr/lib/jvm/java-6-sun/bin/java
-vmargs
-Xms40m
-Xmx256m
-jar /opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar 

I had a feeling it wouldn't change the error because the original error showed it was using /usr/bin/java which is a link to /etc/alternatives/java which is a link to /usr/lib/jvm/java-6-sun/jre/bin/java.

(I also used the argument -vm /usr/lib/jvm/java-6-sun/jre/bin but I got a similar error).

Any other ideas?

---

### Post by lin4crew on 2007-11-24
I'm starting to think this must be related somehow to the 64-bit issue.  I just tried exactly the same thing with my 32-bit Ubuntu Gutsy on another machine and I had no issues at all.

---

### Post by gekkio on 2007-11-24
Make sure you download the 64-bit version of eclipse, because the 32-bit version won't run on the 64-bit JVM.

Latest Eclipse SDK (3.3.1.1) can be found here:
[http://download.eclipse.org/eclipse/downloads/drops/R-3.3.1.1-200710231652/index.php](http://download.eclipse.org/eclipse/downloads/drops/R-3.3.1.1-200710231652/index.php)
Use the Linux (x86_64/GTK 2) package.

Or if you prefer the 32-bit one, install ia32-sun-java6-bin and force eclipse to use it (by editing eclipse.ini or by globally switching to it with update-java-alternatives)

---

### Post by tenmillionmilesaway on 2007-11-24
Eclipse uses swt, which makes use of native libraries.  Presumably the normal 32bit eclipse has 32bit native swt stuff which would cause you a problem.  As gekkio says i would expect that the 64bet version of eclipse should work.

---

### Post by lin4crew on 2007-11-24
I installed the 64-bit eclipse and that did the trick.  Thanks!

---

### Post by peryn on 2008-02-25
> **gekkio said:**
> Make sure you download the 64-bit version of eclipse, because the 32-bit version won't run on the 64-bit JVM.

Latest Eclipse SDK (3.3.1.1) can be found here:
[http://download.eclipse.org/eclipse/downloads/drops/R-3.3.1.1-200710231652/index.php](http://download.eclipse.org/eclipse/downloads/drops/R-3.3.1.1-200710231652/index.php)
Use the Linux (x86_64/GTK 2) package.

Or if you prefer the 32-bit one, install ia32-sun-java6-bin and force eclipse to use it (by editing eclipse.ini or by globally switching to it with update-java-alternatives)

great! it helps :guitar:

---

### Post by salemboot on 2011-12-11
In synaptic:
find:  ia32-sun-java6-bin

Install that and eclipse works.

* useful for android development
* must have 3rd party vendor support repository enabled

---

