---
title: "[SOLVED] Eclipse 3.2 Fails to launch"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by openium on 2008-09-23
Hello, I used Eclipse very successfully for my first project, however as of today I can't get the program to open.  It reports the following:

An error has occurred, see the log:

```
!ENTRY org.eclipse.osgi 4 0 2008-09-22 23:49:42.509
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org.eclipse.ui.internal.ide.IDEWorkbenchAdvisor
   at java.lang.Class.initializeClass(libgcj.so.81)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IContainer
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   ...11 more
```

I am using a gateway MT3707 laptop with dual boot of xp and ubuntu 8.0.4.1  I used synaptics to install the c++ package.  Can anyone please suggest where to start to fix this problem?  Thanks

---

### Post by Sef on 2008-09-23
Moved to Absolute Beginner.

---

### Post by openium on 2008-09-23
Well I figured out my own problem.  Something had been corrupted with my workspace directory.  Execute the following code in the terminal and restart eclipse:

```
mv workspace tempwork
```

It should be noted that you can restore your saved projects after eclipse boots successfully.

---

