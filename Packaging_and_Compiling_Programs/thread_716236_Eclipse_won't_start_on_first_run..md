---
title: "Eclipse won't start on first run."
date: 2008-03-05
forum: Packaging and Compiling Programs
---

### Post by wozzinator on 2008-03-05
I can't run eclipse on startup on this fedora machine (I use Ubuntu, but they only use Fedora in my universities lab which is the distro that i'm having the problem on.)

The text from /home/user/workspace/.metadata/.log  :

!SESSION 2008-03-05 09:10:18.780 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.5.0_03
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.update.configurator 2008-03-05 09:10:21.685
!MESSAGE Could not install bundle plugins/org.eclipse.pde.build/   Bundle "org.eclipse.pde.build" version "3.2.1.r321_v20060823" has already been installed from: [email]update@plugins/org.eclipse.pde.buil[/email]d_3.2.1.r321_v20060823/

!ENTRY org.eclipse.osgi 4 0 2008-03-05 09:10:25.528
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /usr/lib64/eclipse/configuration/org.eclipse.osgi/bundles/16/1/.cp/libswt-pi-gtk-3236.so: /usr/lib64/eclipse/configuration/org.eclipse.osgi/bundles/16/1/.cp/libswt-pi-gtk-3236.so: wrong ELF class: ELFCLASS64
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:822)
	at java.lang.System.loadLibrary(System.java:992)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:436)
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
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

Any help would be great so I can stop switching between Fedora and WinXP in the lab!

---

### Post by cpuobsessed on 2008-03-09
I think there is a problem using 64bit Java libraries, have you tried using EasyEclipse you just unzip and run.

---

