---
title: "Got a problem when using Eclipse"
date: 2012-10-08
forum: Programming Talk
---

### Post by ki4jgt on 2012-10-08
I can't use Eclipse every time I start it, it refers me to an error log which says: 
```
!SESSION 2012-10-08 15:39:47.761 -----------------------------------------------
eclipse.buildId=I20110613-1736
java.version=1.7.0_07
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 4 0 2012-10-08 15:39:48.710
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons: 
	no swt-gtk-3740 in java.library.path
	no swt-gtk in java.library.path
	Can't load library: /home/jesse/.swt/lib/linux/x86_64/libswt-gtk-3740.so
	Can't load library: /home/jesse/.swt/lib/linux/x86_64/libswt-gtk.so

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
```

---

### Post by spjackson on 2012-10-08
This sounds familiar. [http://ubuntuforums.org/showthread.php?t=2066917]("http://ubuntuforums.org/showthread.php?t=2066917")

---

### Post by ki4jgt on 2012-10-08
> **spjackson said:**
> This sounds familiar. [http://ubuntuforums.org/showthread.php?t=2066917]("http://ubuntuforums.org/showthread.php?t=2066917")

Thanks :) Wow, 2 days and I wouldv'e had my answer :)

---

