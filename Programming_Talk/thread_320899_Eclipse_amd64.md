---
title: "Eclipse amd64"
date: 2006-12-18
forum: Programming Talk
---

### Post by thidranki on 2006-12-18
Hi all,

I'm not new to Linux, but I'm new to Ubuntu. I have an amd64 computer and I am a [beginner] Java programmer. I am wondering how to get Eclipse working on Ubuntu? I keep getting the error 
“A Java Runtime Environment (JRE) or Java Development Kit (JDK) must be available in order to run Eclipse. No Java virtual machine was found after searching the following locations:
/usr/lib/j2sdk1.4-sun/bin/java”

I tried to install the JDK from Sun's website (JDK 1.6.0 for amd64) and I thought I installed it correctly, but I guess not.

Thanks.

---

### Post by bmhm on 2006-12-30
[FONT="Verdana"]Well I'd try to create a symbolic link - obviosly eclipse searches the wrong path.

I don't even get that far. Eclipse has startup problems:
> !SESSION 2006-12-30 23:54:42.005 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.fullversion=GNU libgcj 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=de_DE
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2006-12-30 23:54:50.605
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-12-30 23:54:50.619
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-12-30 23:54:50.619
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-12-30 23:54:50.619
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2006-12-30 23:54:51.758
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: memmove
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
   at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
   at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
   at org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
!SESSION 2006-12-30 23:55:08.786 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.fullversion=GNU libgcj 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=de_DE
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2006-12-30 23:55:12.187
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-12-30 23:55:12.187
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-12-30 23:55:12.187
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-12-30 23:55:12.187
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2006-12-30 23:55:12.624
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: memmove
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
   at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
   at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
   at org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
!SESSION 2006-12-31 00:03:47.159 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.fullversion=GNU libgcj 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=de_DE
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2006-12-31 00:03:50.725
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-12-31 00:03:50.725
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-12-31 00:03:50.726
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-12-31 00:03:50.726
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2006-12-31 00:03:51.358
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: memmove
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
   at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
   at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
   at org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

[/FONT]

---

### Post by phossal on 2006-12-31
Two tips...

1. Download the 32-bit version of both Java and Eclipse from the respective websites. You'll appreciate the improvement in performance. 

For Java, download the current .bin file, jdk-<version>-linux-i586.bin, from [http://java.sun.com](http://java.sun.com). Save it to your desktop. Make it executable, and run it: 
```

sudo chmod +x  *.bin
sudo sh *.bin  

```

For eclipse, download the 32bit version from [http://eclipse.org](http://eclipse.org) to your desktop. The website might 'test' for your environment and offer the wrong file by default. Look for something like: eclipse-SDK-3.2.1-linux-gtk.tar.gz. Save it to your desktop. Right-click it, and extract it.


2. Set the JAVA_HOME variable in .bashrc and export it.  Like this...
```

 sudo gedit ~/.bashrc

```

Copy and paste this at the bottom. Save it. Close it.
```

# Copy and Paste into .bashrc
export JAVA_HOME='/home/<user>/Desktop/JDK<version>'
PATH=.:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
alias eclipse='java -jar /home/<user>/Desktop/eclipse/startup.jar'

```

Close your terminal windows. Reopen one and type eclipse. It should launch. In this manner, neither Java nor Eclipse is managed by the package managers, which can be good or bad depending on your needs. This is simply a way to get started.


Notes:
1. I've used the 32bit and 64bit versions of the JDK and eclipse in both 32bit and 64bit Ubuntu. Stick with the 32bit packages for now.
2. Installing Java programs this way allows you to use multiple version and configurations. You can have multiple JDKs. 
3. You can install Tomcat in a very similar way to eclipse, once JAVA_HOME is set. This allows you to run multiple Tomcat servers, etc.

---

### Post by phossal on 2006-12-31
One more thing...

Eclipse may default to the 1.4 compiler and/or you may need to manually add the appropriate JRE. Configure eclipse via the toolbar: 

Window>Preferences>Java>Compiler (or) Installed JRE's

---

### Post by tog on 2007-01-03
I have the same error, but I think it might have to do with how Ubuntu is packaging Eclipse. I downloaded  a copy of Eclipse SDK from the eclipse site, and also install sun-java5 from apt-get. That combination works fine on amd64.

Tog

---

### Post by noobaholic on 2007-01-16
sudo apt-get install sun-java5-jdk

---

### Post by nielz on 2007-01-16
The simplest solution is to just grab an Eclipse package from eclipse.org. This works, as opposed to Ubuntu's package. Isn't there some mechanism to mark packages as defunct, like masked packages in Gentoo?

---

### Post by phossal on 2007-01-16
Really, if you're going to use eclipse for anything important, [install JDK6 and eclipse using this tutorial]("http://ubuntuforums.org/showthread.php?t=332674"). It's simple, fast, and works better than other candidate methods.

---

### Post by bmhm on 2008-10-01
```
sudo aptitude reinstall libswt3.2-gtk-java
```

did the trick. thanks.

---

