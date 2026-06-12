---
title: "Eclipse 3.4/Ganymede hangs loading workbench"
date: 2008-09-15
forum: Programming Talk
---

### Post by ostraaten on 2008-09-15
Hi,
I have been working with Eclipse 3.4/Ganymede for maybe two months now. Now suddenly I'm experiencing some problems with it. Probably installed a little too much software?

If start Eclipse I can select a workspace then it starts loading. It stops on "loading workbench". If I run from terminal and hit cntrl-c it shows the information below.

I have seen another post here with subject "java unusable on Ubuntu". I hope it is not that bad, I just want to run Eclipse and dome some development work.

Any ideas on how I can fix this?
Thanks and Regards,
Onno

Exception in thread "Thread-0" org.eclipse.swt.SWTException: Invalid thread access
	at org.eclipse.swt.SWT.error(SWT.java:3777)
	at org.eclipse.swt.SWT.error(SWT.java:3695)
	at org.eclipse.swt.SWT.error(SWT.java:3666)
	at org.eclipse.swt.widgets.Widget.error(Widget.java:446)
	at org.eclipse.swt.widgets.Widget.checkWidget(Widget.java:385)
	at org.eclipse.swt.widgets.Control.isVisible(Control.java:3092)
	at org.eclipse.swt.widgets.ProgressBar.timerProc(ProgressBar.java:274)
	at org.eclipse.swt.widgets.Display.windowTimerProc(Display.java:4117)
	at org.eclipse.equinox.launcher.JNIBridge._takedown_splash(Native Method)
	at org.eclipse.equinox.launcher.JNIBridge.takeDownSplash(JNIBridge.java:110)
	at org.eclipse.equinox.launcher.Main.takeDownSplash(Main.java:1863)
	at org.eclipse.equinox.launcher.Main$SplashHandler.run(Main.java:106)
[email]ostraaten@ostraaten-toshiba:~/Apps/eclipse-SDK-3.4-linux-gtk.tar.gz[/email]_cvs_bugzilla_radrails_collabnet$ ./eclipse
Killed

---

### Post by tinny on 2008-09-15
Have you installed any additional JRE's lately?

Whats the output of...
```

java -version

```

and

```

javac -version

```

---

### Post by jespdj on 2008-09-16
> **ostraaten said:**
> I have seen another post here with subject "java unusable on Ubuntu". I hope it is not that bad, I just want to run Eclipse and dome some development work.
Java is absolutely not "unusable on Ubuntu" and you shouldn't start believing things like that after reading one thread by some random person on Internet.

Eclipse 3.4 works just fine on Ubuntu with Sun Java 6 or OpenJDK Java 6. Make sure you are not using GCJ Java (GNU Java, which is a very slow and incomplete implementation of Java 1.4).

If you have multiple versions of Java installed, you can select which one you want to use by default using the following command:
```
sudo update-alternatives --config java
```
You could also try starting Eclipse from the command line with the "-clean" option, or as a last resort you can delete the ~/.eclipse directory (which will delete all your Eclipse configuration settings and Eclipse software updates you downloaded!).

---

### Post by razorxpress on 2008-10-13
Even on Eclipse 3.3/Europa the problem is same. It hangs loading workbench. The IDE failed to start only i had my internet connection on. That means when there is ppp0 on eclipse hanged. When i did "sudo poff -a" and loaded eclipse again it loaded as if nothing had happened. So i think the problem might be eclipse trying to search something silently. I think eclipse is searching for javadoc(not sure might be.) which i could not install on the computer because it failed from synaptic. I even removed sun-java6-jre, jdk and installed sun-java-5jre. I am waiting for Ubuntu 8.10. I might have messed up by installing many software. Something like dbus (update). But before that i will try to remove gcj as it might be the one. Any ways if you get any help please reply

---

### Post by anezch on 2008-10-22
Hi, i have the same problem. I'm using jdk 1.6u7 and eclipse ganymede for Java EE. When the splash disappear it shows a blank gray dialog.

@razorxpress: I tried to disconnect all network connections but it didn't work.

Any solutions found? I'm stuck here and need help... :confused:

---

### Post by turboxs on 2008-12-04
I was also having a terrible time getting Ganymede going on my install of ubuntu 8.04. Long hangs while workbench was loading and random crashes. Went and used synaptic package manager to remove gij and my older version of jkd, then install the openjdk and now everything is good to go! Thanks for the help.

---

### Post by caleb12 on 2008-12-19
I hate to resurrect an old post... but I'm at a loss here... 

Eclipse 3.4, Ubuntu 8.10, Sun Java 6 -

java - version: 
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)

I launch eclipse, and it goes through the splash... looks like it's loading and then I get a dialog box with nothing in it... and it just sits. No output onto the command line, nothing... just sits there. I have to manually kill it. 

I've checked and re-checked Java paths and various installed JREs. I have no idea what is going on here... If I could at least get an error, I'd be happy... 

It seems to be the same problem that **_anezch_** mentioned in his post... 

Anyone come across this??? Any ideas even??? 

Thanks...

---

### Post by bobrocks on 2008-12-20
Hello,

Are you starting eclipse from a terminal? If not start from a terminal and see if it prints out its stack trace to the terminal and post it here.

Make sure if you are running 64bit java that you are running 64bit eclipse or vice versa for 32 bit.

---

### Post by caleb12 on 2008-12-20
I've checked and re-checked the java versions, I have 32bit Java installed and 32bit eclipse. I even downloaded a different version from Eclipse, I started with Eclipse IDE for Java EE Developers, and then switched to Eclipse IDE for Java Developers - hoping that would make a difference... and still the same result.

I've tried making Open-JDK the default java on the system and still the same result. 

I'm pretty sure that something with my system is causing this, to many people download eclipse for this to be a real bug that has not been addressed yet.  

A minor miracle occurred just now... Up to this point, I have been getting nothing on the command line after issuing a CTR+C to kill Eclipse. Although, I just hit CTR+C this time and I actually got a backtrace... 

```
*** glibc detected *** /opt/usr/eclipse/eclipse: double free or corruption (!prev): 0x09cb3330 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7db63f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7db8456]
/usr/lib/libglib-2.0.so.0(g_free+0x36)[0xb7b47c06]
/usr/lib/libORBit-2.so.0(giop_recv_buffer_unuse+0x49)[0xb22a2959]
/usr/lib/libORBit-2.so.0(giop_connection_handle_input+0xe0)[0xb22a2e70]
/usr/lib/libORBit-2.so.0[0xb22c2733]
/usr/lib/libORBit-2.so.0[0xb22c5006]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb7b3f6f8]
/usr/lib/libglib-2.0.so.0[0xb7b42da3]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1d2)[0xb7b432c2]
/usr/lib/libgtk-x11-2.0.so.0(gtk_dialog_run+0x1b5)[0xb730d215]
/opt/usr/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.101.R34x_v20080805/eclipse_1115.so(displayMessage+0x81)[0xb7c2345d]
/opt/usr/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.101.R34x_v20080805/eclipse_1115.so(run+0x8c1)[0xb7c1d1cb]
/opt/usr/eclipse/eclipse(setlocale+0x5f2)[0x804904e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d5d685]
/opt/usr/eclipse/eclipse(dlopen+0x41)[0x8048c6d]
======= Memory map: ========
06000000-0642a000 r-xp 00000000 fe:02 1066874    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386/client/libjvm.so
0642a000-06444000 rw-p 0042a000 fe:02 1066874    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386/client/libjvm.so
06444000-06864000 rw-p 06444000 00:00 0 
08048000-0804c000 r-xp 00000000 fe:04 8415128    /opt/usr/eclipse/eclipse
0804c000-0804d000 rw-p 00003000 fe:04 8415128    /opt/usr/eclipse/eclipse
0916b000-09d75000 rw-p 0916b000 00:00 0          [heap]
740a0000-743c0000 rwxp 740a0000 00:00 0 
743c0000-75450000 rwxp 743c0000 00:00 0 
75450000-77940000 rwxp 75450000 00:00 0 
77940000-840a0000 rwxp 77940000 00:00 0 
840a0000-85ae0000 rwxp 840a0000 00:00 0 
85ae0000-940a0000 rwxp 85ae0000 00:00 0 
940a0000-94694000 r--s 00001000 fe:02 1068175    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386/client/classes.jsa
94694000-948a0000 rwxp 94694000 00:00 0 
948a0000-94fae000 rw-p 005f5000 fe:02 1068175    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386/client/classes.jsa
94fae000-954a0000 rwxp 94fae000 00:00 0 
954a0000-9557c000 rw-p 00d03000 fe:02 1068175    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386/client/classes.jsa
9557c000-958a0000 rwxp 9557c000 00:00 0 
958a0000-958a4000 r-xs 00ddf000 fe:02 1068175    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386/client/classes.jsa
958a4000-95ca0000 rwxp 958a4000 00:00 0 
aea6f000-af352000 r--p 00000000 fe:02 868660     /usr/share/icons/hicolor/icon-theme.cache
af352000-afa35000 r--p 00000000 fe:02 868607     /usr/share/icons/gnome/icon-theme.cache
afa35000-afa80000 r--p 00000000 fe:02 967223     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
afa80000-afa81000 ---p afa80000 00:00 0 
afa81000-b0281000 rwxp afa81000 00:00 0 
b0281000-b0282000 ---p b0281000 00:00 0 
b0282000-b0a82000 rwxp b0282000 00:00 0 
b0a82000-b0a83000 ---p b0a82000 00:00 0 
b0a83000-b1283000 rwxp b0a83000 00:00 0 
b1283000-b1284000 ---p b1283000 00:00 0 
b1284000-b1a84000 rwxp b1284000 00:00 0 
b1a84000-b1a85000 ---p b1a84000 00:00 0 
b1a85000-b2285000 rwxp b1a85000 00:00 0 
b2285000-b22ce000 r-xp 00000000 fe:02 1425466    /usr/lib/libORBit-2.so.0.1.0
b22ce000-b22d6000 r--p 00049000 fe:02 1425466    /usr/lib/libORBit-2.so.0.1.0
b22d6000-b22d8000 rw-p 00051000 fe:02 1425466    /usr/lib/libORBit-2.so.0.1.0
b22d8000-b2306000 r-xp 00000000 fe:02 1425472    /usr/lib/libgconf-2.so.4.1.5
b2306000-b2307000 ---p 0002e000 fe:02 1425472    /usr/lib/libgconf-2.so.4.1.5
b2307000-b2308000 r--p 0002e000 fe:02 1425472    /usr/lib/libgconf-2.so.4.1.5
b2308000-b230a000 rw-p 0002f000 fe:02 1425472    /usr/lib/libgconf-2.so.4.1.5
b2329000-b232a000 ---p b2329000 00:00 0 
b232a000-b2b2a000 rwxp b232a000 00:00 0 
b2b2a000-b2b3f000 r-xp 00000000 fe:02 798224     /usr/lib/libICE.so.6.3.0
b2b3f000-b2b40000 rw-p 00014000 fe:02 798224     /usr/lib/libICE.so.6.3.0
b2b40000-b2b42000 rw-p b2b40000 00:00 0 
b2b42000-b2b8f000 r-xp 00000000 fe:02 798228     /usr/lib/libXt.so.6.0.0
b2b8f000-b2b93000 rw-p 0004c000 fe:02 798228     /usr/lib/libXt.so.6.0.0
b2b93000-b2bc9000 r-xp 00000000 fe:02 1501368    /lib/libdbus-1.so.3.4.0
b2bc9000-b2bca000 r--p 00035000 fe:02 1501368    /lib/libdbus-1.so.3.4.0
b2bca000-b2bcb000 rw-p 00036000 fe:02 1501368    /lib/libdbus-1.so.3.4.0
b2bcb000-b2be6000 r-xp 00000000 fe:02 798285     /usr/lib/libdbus-glib-1.so.2.1.0
b2be6000-b2be7000 r--p 0001a000 fe:02 798285     /usr/lib/libdbus-glib-1.so.2.1.0
b2be7000-b2be8000 rw-p 0001b000 fe:02 798285     /usr/lib/libdbus-glib-1.so.2.1.0
b2be8000-b2c27000 r-xp 00000000 fe:02 798991     /usr/lib/libhunspell-1.2.so.0.0.0
b2c27000-b2c28000 r--p 0003e000 fe:02 798991     /usr/lib/libhunspell-1.2.so.0.0.0
b2c28000-b2c2c000 rw-p 0003f000 fe:02 798991     /usr/lib/libhunspell-1.2.so.0.0.0
b2c2c000-b2c40000 r-xp 00000000 fe:02 802062     /usr/lib/libnssutil3.so
b2c40000-b2c43000 r--p 00013000 fe:02 802062     /usr/lib/libnssutil3.so
b2c43000-b2c44000 rw-p 00016000 fe:02 802062     /usr/lib/libnssutil3.so
b2c44000-b2d6b000 r-xp 00000000 fe:02 802060     /usr/lib/libnss3.so
b2d6b000-b2d6c000 ---p 00127000 fe:02 802060     /usr/lib/libnss3.so
b2d6c000-b2d70000 r--p 00127000 fe:02 802060     /usr/lib/libnss3.so
b2d70000-b2d72000 rw-p 0012b000 fe:02 802060     /usr/lib/libnss3.so
b2d72000-b2d94000 r-xp 00000000 fe:02 802063     /usr/lib/libsmime3.so
b2d94000-b2d95000 ---p 00022000 fe:02 802063     /usr/lib/libsmime3.so
b2d95000-b2d97000 r--p 00022000 fe:02 802063     /usr/lib/libsmime3.so
b2d97000-b2d98000 rw-p 00024000 fe:02 802063     /usr/lib/libsmime3.so
b2d98000-b2dc5000 r-xp 00000000 fe:02 802061     /usr/lib/libssl3.so
b2dc5000-b2dc7000 r--p 0002c000 fe:02 802061     /usr/lib/libssl3.so
b2dc7000-b2dc8000 rw-p 0002e000 fe:02 802061     /usr/lib/libssl3.so
b2dc8000-b3929000 r-xp 00000000 fe:02 865150     /usr/lib/xulrunner-1.9.1b2/libxul.so
b3929000-b39f9000 r--p 00b60000 fe:02 865150     /usr/lib/xulrunner-1.9.1b2/libxul.so
b39f9000-b3a1f000 rw-p 00c30000 fe:02 865150     /usr/lib/xulrunner-1.9.1b2/libxul.so
b3a1f000-b3a30000 rw-p b3a1f000 00:00 0 
b3a30000-b3a62000 r-xp 00000000 fe:02 798277     /usr/lib/libnspr4.so
b3a62000-b3a63000 r--p 00031000 fe:02 798277     /usr/lib/libnspr4.so
b3a63000-b3a64000 rw-p 00032000 fe:02 798277     /usr/lib/libnspr4.so
b3a64000-b3a66000 rw-p b3a64000 00:00 0 
b3a66000-b3b23000 r-xp 00000000 fe:02 865161     /usr/lib/xulrunner-1.9.1b2/libmozjs.so
b3b23000-b3b24000 ---p 000bd000 fe:02 865161     /usr/lib/xulrunner-1.9.1b2/libmozjs.so
b3b24000-b3b26000 r--p 000bd000 fe:02 865161     /usr/lib/xulrunner-1.9.1b2/libmozjs.so
b3b26000-b3b29000 rw-p 000bf000 fe:02 865161     /usr/lib/xulrunner-1.9.1b2/libmozjs.so
b3b29000-b3b2a000 rw-p b3b29000 00:00 0 
b3b2a000-b3bed000 r-xp 00000000 fe:02 799069     /usr/lib/libasound.so.2.0.0
b3bed000-b3bef000 r--p 000c2000 fe:02 799069     /usr/lib/libasound.so.2.0.0
b3bef000-b3bf2000 rw-p 000c4000 fe:02 799069     /usr/lib/libasound.so.2.0.0
b3c00000-b3c06000 r-xp 00000000 fe:02 201286     /usr/lib/xulrunner-1.9.1b2/components/libdbusservice.so
b3c06000-b3c07000 r--p 00005000 fe:02 201286     /usr/lib/xulrunner-1.9.1b2/components/libdbusservice.so
b3c07000-b3c08000 rw-p 00006000 fe:02 201286     /usr/lib/xulrunner-1.9.1b2/components/libdbusservice.so
b3c08000-b3c0a000 r-xp 00000000 fe:02 797173     /usr/lib/gconv/UTF-16.so
b3c0a000-b3c0b000 r--p 00001000 fe:02 797173     /usr/lib/gconv/UTF-16.so
b3c0b000-b3c0c000 rw-p 00002000 fe:02 797173     /usr/lib/gconv/UTF-16.so
b3c0c000-b3c0f000 r-xp 00000000 fe:02 865143     /usr/lib/xulrunner-1.9.1b2/libxpcom.so
b3c0f000-b3c10000 r--p 00002000 fe:02 865143     /usr/lib/xulrunner-1.9.1b2/libxpcom.so
b3c10000-b3c11000 rw-p 00003000 fe:02 865143     /usr/lib/xulrunner-1.9.1b2/libxpcom.so
b3c11000-b3cf4000 r-xp 00000000 fe:02 795564     /usr/lib/libstdc++.so.6.0.10
b3cf4000-b3cf5000 ---p 000e3000 fe:02 795564     /usr/lib/libstdc++.so.6.0.10
b3cf5000-b3cf9000 r--p 000e3000 fe:02 795564     /usr/lib/libstdc++.so.6.0.10
b3cf9000-b3cfa000 rw-p 000e7000 fe:02 795564     /usr/lib/libstdc++.so.6.0.10
b3cfa000-b3d00000 rw-p b3cfa000 00:00 0 
b3d00000-b3dee000 rw-p b3d00000 00:00 0 
b3dee000-b3e00000 ---p b3dee000 00:00 0 
b3e00000-b3e4Aborted

```

Honestly, it doesnt make that much sense to me... Hopefully its helpful. Thanks...

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After spending much time playing with variables, I was able to find a solution... 

I uninstalled xulrunner 1.9.1 - apparently Epiphany requires this version, I don't use epiphany and don't really remember installing it... probably via some meta-package. 

At any rate... it works fine now. 

For future reference though, launching eclipse with these parameters helped narrow it down: 

eclipse -debug -consolelog 

prints all stderr to the console...

---

### Post by bobrocks on 2008-12-20
Yeah this Xulrunner thing can happen alot after people installed Firefox 3.  A quick fix is usually to set MOZILLA_FIVE_HOME from a script that starts eclipse.

eg - adding:
MOZILLA_FIVE_HOME=/usr/lib/firefox (or where ever you have it)
export MOZILLA_FIVE_HOME

This is a setting eclipse will use on startup before any other method to find out the system's default browser.  One of the other methods seems to cause a few problems.

Glad you got it fixed.

---

### Post by shil on 2009-03-03
i had the same problem, though my system runs Gentoo.

To "fix" it i moved the workspace directory to a temporary folder and then i ran eclipse, this time it started without a problem.

all i had to do was import my projects and now everything is back to normal

---

### Post by all-in on 2009-03-10
I am having similar problem in launching Eclipse 3.4/Ganymede.  Eclipse keeps failing on startup.  Below is debug message when I start eclipse with:

eclipse -debug -console 


Visually, on start up, I saw status loading different components.  And, it keeps failing at the time the splash screen saying "loading workbench".  It failed and there is an empty dialog show up. 

I have no idea how to fix this because I have no idea what went wrong.  Any suggestion/help is greatly appreciated.  THANK YOU.


myubuntu@dell-desktop:~/Work/eclipse$ eclipse -debug -console
Start VM: -Dosgi.requiredJavaVersion=1.5
-Xms128m
-Xmx1024m
-XX:MaxPermSize=256m
-Djava.class.path=/home/myubuntu/Work/eclipse/plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20081125.jar
-os linux
-ws gtk
-arch x86
-showsplash /home/myubuntu/Work/eclipse//plugins/org.eclipse.platform_3.3.101.v200902111700/splash.bmp
-launcher /home/myubuntu/Work/eclipse/eclipse
-name Eclipse
--launcher.library /home/myubuntu/Work/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.101.R34x_v20080805/eclipse_1115.so
-startup /home/myubuntu/Work/eclipse/plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20081125.jar
-framework plugins/org.eclipse.osgi_3.4.3.R34x_v20081215-1030.jar
-debug
-console
-vm /usr/lib/jvm/java-6-sun-1.6.0.07/jre/bin/../lib/i386/client/libjvm.so
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms128m
-Xmx1024m
-XX:MaxPermSize=256m
-Djava.class.path=/home/myubuntu/Work/eclipse/plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20081125.jar 
Install location:
    file:/home/myubuntu/Work/eclipse/
Configuration file:
    file:/home/myubuntu/Work/eclipse/configuration/config.ini loaded
Configuration location:
    file:/home/myubuntu/Work/eclipse/configuration/
Framework located:
    file:/home/tnguyen/Work/eclipse/plugins/org.eclipse.osgi_3.4.3.R34x_v20081215-1030.jar
Framework classpath:
    file:/home/myubuntu/Work/eclipse/plugins/org.eclipse.osgi_3.4.3.R34x_v20081215-1030.jar
Splash location:
    /home/myubuntu/Work/eclipse//plugins/org.eclipse.platform_3.3.101.v200902111700/splash.bmp
Debug options:
    file:/home/myubuntu/Work/eclipse/.options not found

osgi> Time to load bundles: 5
Starting application: 800

---

### Post by Funnnny on 2009-03-10
Try to normally start Eclipse, and post the error log here.
Many user have the problem starting Eclipse because of xulrunner ( even you installed it, it still give this error)

---

### Post by all-in on 2009-03-12
Sorry for the delay in posting the log file up. I was tie up with some other tasks.

Below is the logfile after I start Eclipse the normal way (ie. running "eclipse" from command line).  Below is the content of the ".log" file.  I see the exception "Widget disposed too early" but don't have a clue what causing it.  

Any help is appreciated. THANK YOU.


!SESSION 2009-03-11 21:21:31.792 -----------------------------------------------
eclipse.buildId=M20090211-1700
java.version=1.6.0_07
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.ui.workbench 4 0 2009-03-11 21:21:41.574
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1182)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1163)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1026)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:211)
	at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:466)
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1948)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:442)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1893)
	at org.eclipse.swt.widgets.Display.release(Display.java:3083)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:237)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:129)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.ui.workbench 4 0 2009-03-11 21:21:41.577
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1182)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1163)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1026)

	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:211)
	at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:466)
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1948)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:442)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1893)
	at org.eclipse.swt.widgets.Display.release(Display.java:3083)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:237)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:129)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.ui.workbench 4 0 2009-03-11 21:21:41.578
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1182)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1163)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1026)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:211)
	at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:466)
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1948)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:442)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1893)
	at org.eclipse.swt.widgets.Display.release(Display.java:3083)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:237)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:129)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.ui.workbench 4 0 2009-03-11 21:21:41.579
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1182)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1163)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1026)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:211)
	at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:466)
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1948)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:442)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1893)
	at org.eclipse.swt.widgets.Display.release(Display.java:3083)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:237)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:129)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.osgi 4 0 2009-03-11 21:21:41.601
!MESSAGE Application error
!STACK 1
org.eclipse.swt.SWTError: XPCOM error -2147467262
	at org.eclipse.swt.browser.Mozilla.error(Mozilla.java:1638)
	at org.eclipse.swt.browser.Mozilla.setText(Mozilla.java:1861)
	at org.eclipse.swt.browser.Browser.setText(Browser.java:737)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.generateContentForPage(BrowserIntroPartImplementation.java:252)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.dynamicStandbyStateChanged(BrowserIntroPartImplementation.java:451)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.doStandbyStateChanged(BrowserIntroPartImplementation.java:658)
	at org.eclipse.ui.internal.intro.impl.model.AbstractIntroPartImplementation.standbyStateChanged(AbstractIntroPartImplementation.java:249)
	at org.eclipse.ui.internal.intro.impl.model.IntroPartPresentation.standbyStateChanged(IntroPartPresentation.java:443)
	at org.eclipse.ui.intro.config.CustomizableIntroPart.standbyStateChanged(CustomizableIntroPart.java:266)
	at org.eclipse.ui.internal.ViewIntroAdapterPart$2.run(ViewIntroAdapterPart.java:74)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
	at org.eclipse.ui.internal.ViewIntroAdapterPart.setStandby(ViewIntroAdapterPart.java:70)
	at org.eclipse.ui.internal.ViewIntroAdapterPart$1.propertyChanged(ViewIntroAdapterPart.java:55)
	at org.eclipse.ui.internal.WorkbenchPartReference.fireInternalPropertyChange(WorkbenchPartReference.java:374)
	at org.eclipse.ui.internal.WorkbenchPartReference.fireZoomChange(WorkbenchPartReference.java:539)
	at org.eclipse.ui.internal.PartPane.setZoomed(PartPane.java:349)
	at org.eclipse.ui.internal.PartStack.setZoomed(PartStack.java:1526)
	at org.eclipse.ui.internal.PartSashContainer.zoomIn(PartSashContainer.java:884)
	at org.eclipse.ui.internal.PartSashContainer.childRequestZoomIn(PartSashContainer.java:905)
	at org.eclipse.ui.internal.LayoutPart.requestZoomIn(LayoutPart.java:354)
	at org.eclipse.ui.internal.PartStack.setState(PartStack.java:1501)
	at org.eclipse.ui.internal.WorkbenchPage.setState(WorkbenchPage.java:3872)
	at org.eclipse.ui.internal.WorkbenchPage.toggleZoom(WorkbenchPage.java:3944)
	at org.eclipse.ui.internal.WorkbenchIntroManager.setIntroStandby(WorkbenchIntroManager.java:201)
	at org.eclipse.ui.internal.WorkbenchIntroManager.showIntro(WorkbenchIntroManager.java:136)
	at org.eclipse.ui.application.WorkbenchWindowAdvisor.openIntro(WorkbenchWindowAdvisor.java:173)
	at org.eclipse.ui.internal.ide.application.IDEWorkbenchWindowAdvisor.openIntro(IDEWorkbenchWindowAdvisor.java:458)
	at org.eclipse.ui.internal.WorkbenchWindow.open(WorkbenchWindow.java:777)
	at org.eclipse.ui.internal.Workbench$22.runWithException(Workbench.java:1043)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:133)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3378)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3036)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:803)
	at org.eclipse.ui.internal.Workbench$27.runWithException(Workbench.java:1363)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:133)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3378)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3036)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2295)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2200)
	at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:495)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:288)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:490)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:113)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

---

### Post by Funnnny on 2009-03-12
Open your Eclipse.ini ( in eclipse's folder ) and add this line
> -Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner
Now eclipse should be start now

---

### Post by all-in on 2009-03-12
Thank you so much for your help.  I just tried out with you suggestion but I still having the same problem.  

Below is my current "eclipse.ini" file and the new log after I ran "eclipse".  I think the log has the same output as before.  I am basically clueless at the moment.  I hope that you can continue to help. :)


CONTENT OF "eclipse.ini"

-showsplash
org.eclipse.platform
-framework
plugins/org.eclipse.osgi_3.4.3.R34x_v20081215-1030.jar
-Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms128m
-Xmx1024m
-XX:MaxPermSize=256m



NEW LOG:

!SESSION 2009-03-11 22:12:42.488 -----------------------------------------------
eclipse.buildId=M20090211-1700
java.version=1.6.0_07
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  -Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner
Command-line arguments:  -os linux -ws gtk -arch x86 -Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner

!ENTRY org.eclipse.ui.workbench 4 0 2009-03-11 22:12:49.702
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1182)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1163)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1026)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:211)
	at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:466)
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1948)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:442)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1893)
	at org.eclipse.swt.widgets.Display.release(Display.java:3083)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:237)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:129)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.ui.workbench 4 0 2009-03-11 22:12:49.706
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1182)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1163)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1026)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:211)
	at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:466)
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1948)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:442)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1893)
	at org.eclipse.swt.widgets.Display.release(Display.java:3083)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:237)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:129)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.ui.workbench 4 0 2009-03-11 22:12:49.707
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1182)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1163)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1026)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:211)
	at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:466)
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1948)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:442)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1893)
	at org.eclipse.swt.widgets.Display.release(Display.java:3083)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:237)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:129)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.ui.workbench 4 0 2009-03-11 22:12:49.708
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1182)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1163)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1026)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
	at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:211)
	at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:466)
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1948)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
	at org.eclipse.swt.widgets.Control.release(Control.java:3221)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:442)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1893)
	at org.eclipse.swt.widgets.Display.release(Display.java:3083)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:237)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:129)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.osgi 4 0 2009-03-11 22:12:49.731
!MESSAGE Application error
!STACK 1
org.eclipse.swt.SWTError: XPCOM error -2147467262
	at org.eclipse.swt.browser.Mozilla.error(Mozilla.java:1638)
	at org.eclipse.swt.browser.Mozilla.setText(Mozilla.java:1861)
	at org.eclipse.swt.browser.Browser.setText(Browser.java:737)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.generateContentForPage(BrowserIntroPartImplementation.java:252)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.dynamicStandbyStateChanged(BrowserIntroPartImplementation.java:451)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.doStandbyStateChanged(BrowserIntroPartImplementation.java:658)
	at org.eclipse.ui.internal.intro.impl.model.AbstractIntroPartImplementation.standbyStateChanged(AbstractIntroPartImplementation.java:249)
	at org.eclipse.ui.internal.intro.impl.model.IntroPartPresentation.standbyStateChanged(IntroPartPresentation.java:443)
	at org.eclipse.ui.intro.config.CustomizableIntroPart.standbyStateChanged(CustomizableIntroPart.java:266)
	at org.eclipse.ui.internal.ViewIntroAdapterPart$2.run(ViewIntroAdapterPart.java:74)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
	at org.eclipse.ui.internal.ViewIntroAdapterPart.setStandby(ViewIntroAdapterPart.java:70)
	at org.eclipse.ui.internal.ViewIntroAdapterPart$1.propertyChanged(ViewIntroAdapterPart.java:55)
	at org.eclipse.ui.internal.WorkbenchPartReference.fireInternalPropertyChange(WorkbenchPartReference.java:374)
	at org.eclipse.ui.internal.WorkbenchPartReference.fireZoomChange(WorkbenchPartReference.java:539)
	at org.eclipse.ui.internal.PartPane.setZoomed(PartPane.java:349)
	at org.eclipse.ui.internal.PartStack.setZoomed(PartStack.java:1526)
	at org.eclipse.ui.internal.PartSashContainer.zoomIn(PartSashContainer.java:884)
	at org.eclipse.ui.internal.PartSashContainer.childRequestZoomIn(PartSashContainer.java:905)
	at org.eclipse.ui.internal.LayoutPart.requestZoomIn(LayoutPart.java:354)
	at org.eclipse.ui.internal.PartStack.setState(PartStack.java:1501)
	at org.eclipse.ui.internal.WorkbenchPage.setState(WorkbenchPage.java:3872)
	at org.eclipse.ui.internal.WorkbenchPage.toggleZoom(WorkbenchPage.java:3944)
	at org.eclipse.ui.internal.WorkbenchIntroManager.setIntroStandby(WorkbenchIntroManager.java:201)
	at org.eclipse.ui.internal.WorkbenchIntroManager.showIntro(WorkbenchIntroManager.java:136)
	at org.eclipse.ui.application.WorkbenchWindowAdvisor.openIntro(WorkbenchWindowAdvisor.java:173)
	at org.eclipse.ui.internal.ide.application.IDEWorkbenchWindowAdvisor.openIntro(IDEWorkbenchWindowAdvisor.java:458)
	at org.eclipse.ui.internal.WorkbenchWindow.open(WorkbenchWindow.java:777)
	at org.eclipse.ui.internal.Workbench$22.runWithException(Workbench.java:1043)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:133)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3378)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3036)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:803)
	at org.eclipse.ui.internal.Workbench$27.runWithException(Workbench.java:1363)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:133)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3378)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3036)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2295)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2200)
	at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:495)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:288)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:490)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:113)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

---

### Post by all-in on 2009-03-13
I am happy to share I can now start eclipse 3.4/Ganymede successfully after I updated xulrunner to 1.9, 

So, the change I've made to fix the problem were:

1. to add the line:  -Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner to my eclipse.ini file.  THANKS to "Funnny" help above.
2. to update my xulrunner to version 1.9

Hope this will help someone else in the future.

---

### Post by abhinavmodi on 2009-10-10
> **all-in said:**
> I am happy to share I can now start eclipse 3.4/Ganymede successfully after I updated xulrunner to 1.9, 

So, the change I've made to fix the problem were:

1. to add the line:  -Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner to my eclipse.ini file.  THANKS to "Funnny" help above.
2. to update my xulrunner to version 1.9

Hope this will help someone else in the future.

This seems to be the only way to get eclipse 3.4.2 running on karmic. The earlier workaround of deleting the workspace directory contents, etc did not work - that may have been a different issue.

Thanks for the tip !

---

### Post by cdaaawg on 2010-03-05
Thanks shil for the solution. Renaming my workspace directory allowed Eclipse to launch properly. I encountered the blank dialog box after using  Eclipse 3.5.2 for several days. I cannot be certain, but the problem may have been as a result of very little free space left in my home directory, where my original workspace was located.

---

### Post by shammydog on 2010-03-30
> **Funnnny said:**
> Open your Eclipse.ini ( in eclipse's folder ) and add this line

Now eclipse should be start now


Thank you Funnnny!  Works perfectly with Ubuntu 9.10 and Ganymede

---

### Post by cwmoser on 2010-10-08
I followed this thread and what finally got Eclipse running for me was to delete the workspace directory.

Probably, that his not the entire solution because I also exported a path and added the entry to the eclipse.ini file too.

Perhaps, the solution is a combination of all of these.

I'm using Eclipse on Ubuntu 10.04 64-bit version.

Carl

---

### Post by Lutshow on 2010-11-04
// wrong message

---

