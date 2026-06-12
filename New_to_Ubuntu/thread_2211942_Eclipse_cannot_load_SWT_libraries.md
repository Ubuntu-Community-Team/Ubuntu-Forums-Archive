---
title: "Eclipse cannot load SWT libraries"
date: 2014-03-18
forum: New to Ubuntu
---

### Post by jang3 on 2014-03-18
Every time I try to open Eclipse in Ubuntu 12.04 I get an Unsatisfied Link Error and it will not open. I have recently installed the java JDK and Android SDK, could this be the problem? I followed [this tutorial]("http://forums.team-nocturnal.com/showthread.php/772").


Here is the log info:
> !SESSION 2012-04-15 21:05:46.902 -----------------------------------------------
eclipse.buildId=I20110613-1736
java.version=1.7.0
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x86_64


!ENTRY org.eclipse.osgi 4 0 2012-04-15 21:05:47.885
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons: 
no swt-gtk-3740 in java.library.path
no swt-gtk in java.library.path
Can't load library: /home/tom/.swt/lib/linux/x86_64/libswt-gtk-3740.so
Can't load library: /home/tom/.swt/lib/linux/x86_64/libswt-gtk.so


at org.eclipse.swt.internal.Library.loadLibrary(Library.java:285)
at org.eclipse.swt.internal.Library.loadLibrary(Library.java:194)
at org.eclipse.swt.internal.C.<clinit>(C.java:21)
at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
at org.eclipse.swt.widgets.Display.<clinit>(Display.java:132)
at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:695)
at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
at org.eclipse.ui.internal.ide.application.IDEApplication.createDisplay(IDEApplication.java:153)
at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:95)
at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:344)
at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
at java.lang.reflect.Method.invoke(Method.java:601)
at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:622)
at org.eclipse.equinox.launcher.Main.basicRun(Main.java:577)
at org.eclipse.equinox.launcher.Main.run(Main.java:1410)
at org.eclipse.equinox.launcher.Main.main(Main.java:1386)

I have tried uninstalling and reinstalling, and removing the ~/.eclipse directory but it still doesn't work

---

### Post by Phil_Freihofner on 2014-08-06
I found information that helped me solve this at the following URL:
[https://bugs.launchpad.net/ubuntu/+source/swt-gtk/+bug/975560](https://bugs.launchpad.net/ubuntu/+source/swt-gtk/+bug/975560)

There are a number of solutions listed there. I did the simple thing of copying the files to the location where Eclipse was looking for them. They were in /usr/lib/jni

---

