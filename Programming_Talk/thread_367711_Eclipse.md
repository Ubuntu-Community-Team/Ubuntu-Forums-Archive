---
title: "Eclipse"
date: 2007-02-22
forum: Programming Talk
---

### Post by LinkRJH on 2007-02-22
I apologize in advance if this is not the correct folder for this post, but am unable to get Eclipse running.  I'm currently in a beginning programming class at school, and we use Windows and Eclipse in class...but I can't get it to run on Ubuntu for the life of me.

I used apt-get to install both java and eclipse, but when trying to run eclipse I get an error messaged sent to a log file.

The log file is as follows:
```
!SESSION 2007-02-21 20:57:02.667
-----------------------------------------------
eclipse.buildId=M20060921-0945
java.fullversion=GNU libgcj 4.1.2 20060928 (prerelease) (Ubuntu
4.1.1-14ubuntu7)
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2007-02-21 20:57:10.214
!MESSAGE NLS missing message: initializer_error in:
org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-21 20:57:10.224
!MESSAGE NLS missing message: fileInitializer_fileNotFound in:
org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-21 20:57:10.224
!MESSAGE NLS missing message: fileInitializer_IOError in:
org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-21 20:57:10.224
!MESSAGE NLS missing message: fileInitializer_missingFileName in:
org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-02-21 20:57:12.104
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: memmove
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
   at org.eclipse.swt.widgets.Display.(Display.java:126)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
   at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
   at
org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
   at
org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at
org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at
org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at
org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at
org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
```

Thank you in advance for any assistance with this problem,

Richard Hertzog

---

### Post by kaamos on 2007-02-22
If you are having problems with the apt version, you could just download the newer version from eclipse.org and use that. Just make sure you have installed Suns java and set it as default.

---

### Post by Colonel Kilkenny on 2007-02-22
There's a fixed Eclipse at the edgy-proposed repository. 
Newer version from eclipse.org is still better. Too bad you can't install it easily.

---

### Post by phossal on 2007-02-23
> **Colonel Kilkenny said:**
> Newer version from eclipse.org is still better. Too bad you can't install it easily.

What could be easier than downloading it and extracting it?

---

### Post by Colonel Kilkenny on 2007-02-23
> **phossal said:**
> What could be easier than downloading it and extracting it?

Working version from repository?

---

### Post by phossal on 2007-02-23
> **Colonel Kilkenny said:**
> **Working** version from repository?
Well, Colonel, have it any way you like it, sir. I much prefer to be current, and to avoid the *extra* security risks associated with grabbing packages from the backports, for example. You know, like Java 6, which is just a packaged version of the same .bin file I might install from SUN anyway? As for being easier to grab it from the repos, have you ever diagnosed a failed package install for one of the beginners on this site? Unpleasant. What about "download, right-click, extract"? To each his own.

I know people are in love with out-of-date software because it's *almost* as easy as just downloading the current version, but I can't quite make sense of it.

---

### Post by hod139 on 2007-02-23
I think we have had this discussion before, haven't we......

I prefer to be (slighty) out of date to let someone else manage my installed software so I don't have to worry about it.  Other people prefer to have the latest and greatest software and more control.  Who's right?  I say both (or maybe neither!)

---

### Post by phossal on 2007-02-23
> **hod139 said:**
> I prefer to be (slighty) out of date to let someone else manage my installed software so I don't have to worry about it.
Typical hod style. ;) Have you tried grabbing the new Adobe Reader right from Adobe? If you download the .tar.gz file for linux, you only have to cd into the extracted directory and run *sudo INSTALL*. The performance of it over the packaged version, and especially evince, is.. well, noticeable isn't the word.

---

