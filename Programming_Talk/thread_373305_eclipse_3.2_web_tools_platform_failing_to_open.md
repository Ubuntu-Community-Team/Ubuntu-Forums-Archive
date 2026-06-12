---
title: "eclipse 3.2 web tools platform failing to open"
date: 2007-03-01
forum: Programming Talk
---

### Post by dd1403 on 2007-03-01
Hi, 
I have installed the eclipse 3.2 from (wtp web tools platform) from eclipse.org site and currently having sun java6 installed when I am trying to start the eclipse I am getting the strange error and it is not getting open.

COuld you please let me know what's wrong?

SESSION 2007-02-28 22:28:39.058 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.version=1.6.0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_IN
Command-line arguments: -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2007-02-28 22:28:45.362
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/devendra/eclipse/configuration/org.eclipse.osgi/bundles/98/1/.cp/libswt-pi-gtk-3235.so: /home/devendra/eclipse/configuration/org.eclipse.osgi/bundles/98/1/.cp/libswt-pi-gtk-3235.so: cannot open shared object file: No such file or directory
at java.lang.ClassLoader$NativeLibrary.load(Native Method)
at java.lang.ClassLoader.loadLibrary0(ClassLoader.jav a:1751)
at java.lang.ClassLoader.loadLibrary(ClassLoader.java :1660)
at java.lang.Runtime.loadLibrary0(Runtime.java:823)
at java.lang.System.loadLibrary(System.java:1030)
at org.eclipse.swt.internal.Library.loadLibrary(Libra ry.java:123)
at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:2 2)
at org.eclipse.swt.internal.Converter.wcsToMbcs(Conve rter.java:63)
at org.eclipse.swt.internal.Converter.wcsToMbcs(Conve rter.java:54)
at org.eclipse.swt.widgets.Display.<clinit>(Display.j ava:126)
at org.eclipse.ui.internal.Workbench.createDisplay(Wo rkbench.java:433)
at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI .java:161)
at org.eclipse.ui.internal.ide.IDEApplication.createD isplay(IDEApplication.java:122)
at org.eclipse.ui.internal.ide.IDEApplication.run(IDE Application.java:75)
at org.eclipse.core.internal.runtime.PlatformActivato r$1.run(PlatformActivator.java:7
at org.eclipse.core.runtime.internal.adaptor.EclipseA ppLauncher.runApplication(EclipseAppLauncher.java: 92)
at org.eclipse.core.runtime.internal.adaptor.EclipseA ppLauncher.start(EclipseAppLauncher.java:6
at org.eclipse.core.runtime.adaptor.EclipseStarter.ru n(EclipseStarter.java:400)
at org.eclipse.core.runtime.adaptor.EclipseStarter.ru n(EclipseStarter.java:177)
at sun.reflect.NativeMethodAccessorImpl.invoke0(Nativ e Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(Native MethodAccessorImpl.java:39)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(De legatingMethodAccessorImpl.java:25)
at java.lang.reflect.Method.invoke(Method.java:597)
at org.eclipse.core.launcher.Main.invokeFramework(Mai n.java:336)
at org.eclipse.core.launcher.Main.basicRun(Main.java: 280)
at org.eclipse.core.launcher.Main.run(Main.java:977)
at org.eclipse.core.launcher.Main.main(Main.java:952)

-------------------------
Machine Details

devendra@devendra-galaxy:~$ uname -a
Linux devendra-galaxy 2.6.15-26-amd64-generic #1 SMP PREEMPT Thu Aug 3 02:52:35 UTC 2006 x86_64 GNU/Linux


devendra@devendra-galaxy:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)
devendra@devendra-galaxy:~$

---

### Post by dd1403 on 2007-03-02
Can any body give me the solutions for this. 

Waiting from two days :(

---

### Post by hod139 on 2007-03-02
How did you install java?  You probably need to set Eclipse's java_home configuration file if you haven't set up the alternatives correctly.  I'm not sure where  you installed eclipse, but the file is called java_home (using the repository version of eclipse the file is located at /etc/eclipse/java_home) and put the location that you installed java to the top of that file.

---

### Post by dd1403 on 2007-03-02
Hi, 
Thanks for the reply. I have installed the sun's java and it is properly set. Also, I installed eclipse from eclipse.org. It is wtp (webtools platform). 

I haven't used ubuntu repository as eclipse with WTP  is not available .

Could u please let me know what I did wrong?

---

### Post by hod139 on 2007-03-04
My guess is that you have to edit Eclipse's java_home file.  Since you installed eclipse from a jar file, it is probably in the directory that you extracted eclipse in.

You can also try running 
```

update-java-alternatives -l

```
and selecting the version of java you want used.  On my machine the output of the above command looks like:

```

java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-sun 63 /usr/lib/jvm/java-6-sun

``` 

and if I want to use Sun's java 6, I would type:

```

sudo update-java-alternatives -s java-6-sun

```

---

