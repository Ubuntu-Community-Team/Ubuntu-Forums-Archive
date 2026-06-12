---
title: "eclipse c++ php ecc.."
date: 2008-09-26
forum: Programming Talk
---

### Post by giuseppe500 on 2008-09-26
Hy.
I would use eclipse on linux ubuntu for php and c++ programming.
IS possible to put in "all in one" package where both php and c++ work on the same ide(eclipse) ?
And from eclipse i can choose a c++ or php project?

---

### Post by Reiger on 2008-09-26
Yes on both accounts if I understood your questions correctly.

---

### Post by giuseppe500 on 2008-09-27
> **Reiger said:**
> Yes on both accounts if I understood your questions correctly.

and how?
What version of eclipse i must install and what plugins?
Thanks.

---

### Post by jespdj on 2008-09-27
I would download "Eclipse for C/C++ Developers" from the [Eclipse download page](http://www.eclipse.org/downloads/) and then install the PHP development stuff on top of it with Eclipse's built-in software update manager.

I don't use Eclipse for PHP so I can't tell you what you need exactly for PHP. But just look around in Eclipse's update manager, it will probably not that difficult to see what you'll need.

---

### Post by drumz on 2008-09-27
Yes, you can use one installed version of Eclipse for multiple programming languages.  At work we use it for PHP with plans for C/C++ and Python using the different add-on plug-ins that support those languages.  All the plug-ins are installed, we just haven't used all of them yet.

We installed the latest version of Eclipse (Ganymede), and then searched for a plug-in for each language and followed the instructions to install them.  For most, it was as simple as adding a URL to the project in Eclipse's update manager and then clicking on a checkbox to select and install it.

I can't speak yet on how good the C/C++ and Python plug-ins are yet, but the PHP plugin (PDT) works fine.  We previously used the Zend IDE, but in their latest version they switched to Eclipse themselves and for us it isn't as stable as the previous version.  So that drove us to try 'normal' Eclipse and it's worked out well.  The ONLY difference that we've noticed so far is debugging.  With Zend's version, everyone can share the same code base installed on the web server but use a locally checked out copy that they do their work on and it's smart enough to transparently run the code files you have open in Eclipse in place of what's on the web server.  This isn't possible using 'normal' Eclipse with the PDT plug-in, so now we maintain one public directory with the version everyone has access to for last minute testing along with a separate directory on the web server for each developer that's their private work area (and contains everything the public copy does) - so we waste a big of disk space and everyone has to make sure they eventually merge their changes into the public copy for testing but it works and is stable.

---

### Post by giuseppe500 on 2008-09-27
great!
But i search in google for a Ganymede , and there are a lot of distro!
WHat you advice to install?
and..there are some gui ui plugin for eclipse?
Thanks.

---

### Post by drubin on 2008-09-27
> **jespdj said:**
> I would download "Eclipse for C/C++ Developers" from the [Eclipse download page](http://www.eclipse.org/downloads/) and then install the PHP development stuff on top of it with Eclipse's built-in software update manager.

I don't use Eclipse for PHP so I can't tell you what you need exactly for PHP. But just look around in Eclipse's update manager, it will probably not that difficult to see what you'll need.

I think it is a package PDT 
[www.eclipse.org/pdt/](www.eclipse.org/pdt/)

I use eclipse for java/php/python I think it is amazing.

---

### Post by drumz on 2008-09-27
I just download Eclipse from the main Eclipse site ([www.eclipse.org](www.eclipse.org)) and intall it by hand.  A lot of distros are behind in the version they provide so I tend to maintain it by hand myself.

There are some GUI UI plug-ins but I don't have any experience with them.

---

### Post by drubin on 2008-09-27
> **drumz said:**
> I just download Eclipse from the main Eclipse site ([www.eclipse.org](www.eclipse.org)) and intall it by hand.  A lot of distros are behind in the version they provide so I tend to maintain it by hand myself.

There are some GUI UI plug-ins but I don't have any experience with them.

+1 never to a apt-get eclipse the version would be far to outdated.

---

### Post by giuseppe500 on 2008-09-27
I install the c++ version of eclipse but it crash and this is the .log file:
SESSION 2008-09-27 17:14:21.038 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=it_IT
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2008-09-27 17:14:23.327
!MESSAGE Application error
!STACK 1
java.lang.IllegalStateException: Unable to acquire application service. Ensure that the org.eclipse.core.runtime bundle is resolved and started (see config.ini).
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:72)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:363)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:176)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

---

### Post by giuseppe500 on 2008-09-27
sorry , this is the error:
JVM terminated. Exit code=13
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx512m
-XX:MaxPermSize=256m
-Djava.class.path=/plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20080819.jar
-os linux
-ws gtk
-arch x86
-showsplash //plugins/org.eclipse.platform_3.3.101.v200809111700/splash.bmp
-launcher /eclipse
-name Eclipse
--launcher.library /plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.101.R34x_v20080805/eclipse_1115.so
-startup /plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20080819.jar
-vm /usr/lib/jvm/java-6-sun-1.6.0.06/jre/bin/../lib/i386/client/libjvm.so
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx512m
-XX:MaxPermSize=256m
-Djava.class.path=/plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20080819.jar

---

### Post by drumz on 2008-09-27
Not sure how much help I'll be on this, but doing some quick googling based on the 'JVM terminated. Exit code=13' part:

1.  Are you running a 32 bit OS or 64 bit?  If you have a 64 bit OS installed then you need to download the 64 bit version of Eclipse.  Based on the directories included in your output it looks like you're on a 32bit OS.

2.  I'm not sure how well Eclipse will run with a Java VM 1.6.  The one line in the output indicates it needs 1.5 ('-Dosgi.requiredJavaVersion=1.5').  My system has 1.5 installed and I'm not having any problems, I haven't tried it with 1.6.

---

### Post by giuseppe500 on 2008-09-27
No . dont work i try with 5 and 6 vm, how to uninstall eclipse from my ubuntu and try to reinstall all?
Thanks

---

### Post by drumz on 2008-09-28
If you downloaded the .tar.gz file and decompressed it, all you need to do is delete the directory named 'eclipse' and (if it exists) the 'workspace' directory in your home directory (make sure there's nothing you want to keep in it first).

---

