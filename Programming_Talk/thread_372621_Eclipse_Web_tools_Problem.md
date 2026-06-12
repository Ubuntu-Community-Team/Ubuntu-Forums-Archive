---
title: "Eclipse Web tools Problem"
date: 2007-02-28
forum: Programming Talk
---

### Post by dd1403 on 2007-02-28
Hi, 
I am a Java developer and was working on the Suse10.1 earlier. I have sucessfully installed the Sun's jdk1.6.0 and eclipse 3.2 with WebTools platform (wtp) on my system and was using it in working condition. 

Then I migrated to Ubuntu 6.0.6 LTS Dapper Drake from one of the installation CDs.
I converted the jdk1.6-amd64.bin file to deb package and installed it sucessfully on my system.

Then I extracted the wtp(eclipse) on my home folder and when I am trying to run the eclipse  splash screen appears and vanishes after some time and I am not able to open eclipse any more on unbuntu.  I googled a lot but didn't find the proper solutions. Also the WTP (WebTools Eclipse)  is not available in ubuntu repository and I don't want to use that. I need a steps to install Sun's JDK 6 and Eclipse 3.2 (web tools platform) on my ubuntu. 

It's very important for me to run eclipse 3.2 on my system. here is the eclipse log that I am getting followed by my machine details. One more thing my JDK 6 is properly setup and I can see it working from command prompt. Even javac is also working fine. I followed the Ubuntu wiki page to setup sun's JDK .

!SESSION 2007-02-28 22:28:39.058 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.version=1.6.0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_IN
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2007-02-28 22:28:45.362
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/devendra/eclipse/configuration/org.eclipse.osgi/bundles/98/1/.cp/libswt-pi-gtk-3235.so: /home/devendra/eclipse/configuration/org.eclipse.osgi/bundles/98/1/.cp/libswt-pi-gtk-3235.so: cannot open shared object file: No such file or directory
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

-------------------------
Machine Details

**devendra@devendra-galaxy:~$ uname -a**
Linux devendra-galaxy 2.6.15-26-amd64-generic #1 SMP PREEMPT Thu Aug 3 02:52:35 UTC 2006 x86_64 GNU/Linux


**devendra@devendra-galaxy:~$ java -version**
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)
devendra@devendra-galaxy:~$

Please help me out I don't want to switch to Suse as there package manager is very slow for me.
Waitng for the positive reply.

Thanks & Regards
Devendra Dave

---

