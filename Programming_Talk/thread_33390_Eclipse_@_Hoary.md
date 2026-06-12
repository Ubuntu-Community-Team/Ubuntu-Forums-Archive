---
title: "Eclipse @ Hoary"
date: 2005-05-10
forum: Programming Talk
---

### Post by Badcel on 2005-05-10
Hi, 

I installed eclipse, like its explained in the Wiki (for global use)

But I get this error in a logfile:

```
!SESSION Mai 10, 2005 22:41:08.126 ---------------------------------------------
eclipse.buildId=M200503110845
java.version=1.5.0_02
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=de_DE

!ENTRY org.eclipse.core.runtime Mai 10, 2005 22:41:08.127
!MESSAGE Product org.eclipse.platform.ide could not be found.

!ENTRY org.eclipse.osgi Mai 10, 2005 22:41:08.151
!MESSAGE Application error
!STACK 1
java.lang.RuntimeException: No application id has been found.
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:313)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:273)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:129)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:185)
	at org.eclipse.core.launcher.Main.run(Main.java:704)
	at org.eclipse.core.launcher.Main.main(Main.java:688)

!ENTRY org.eclipse.osgi Mai 10, 2005 22:41:08.158
!MESSAGE Bundle update@/opt/eclipse/plugins/org.eclipse.help.ide_3.0.0/ [3] was not resolved.
!SUBENTRY 1 org.eclipse.osgi Mai 10, 2005 22:41:08.158
!MESSAGE Missing required bundle org.eclipse.help.base_0.0.0.
!SUBENTRY 1 org.eclipse.osgi Mai 10, 2005 22:41:08.158
!MESSAGE Missing required bundle org.eclipse.help.ui_0.0.0.
!SUBENTRY 1 org.eclipse.osgi Mai 10, 2005 22:41:08.158
!MESSAGE Missing required bundle org.eclipse.search_0.0.0.
!SUBENTRY 1 org.eclipse.osgi Mai 10, 2005 22:41:08.159
!MESSAGE Missing required bundle org.eclipse.ui_0.0.0.
!SUBENTRY 1 org.eclipse.osgi Mai 10, 2005 22:41:08.160
!MESSAGE Missing required bundle org.eclipse.ui.ide_0.0.0.
.....

```

Someone else had an error in his log too, but I think I have another problem, but cant find it  ](*,)

---

### Post by jerome bettis on 2005-05-10
damn that's weird

i would just go to [www.eclipse.org](www.eclipse.org) download the tarball or zip file whatever it is, extract it and just run it there.  there's really no need to 'install' it.  you could move the eclipse folder to /usr/share and put a script called eclipse in /usr/bin that just calls /uisr/share/eclipse/eclipse (or whatever the executable is).

---

### Post by Badcel on 2005-05-11
yeah

when I wrote 'install' I mean, that I have extracted the zip - file and copied it into the /opt folder and created a link in /usr/bin, like its explained in the Wiki.

[http://www.ubuntulinux.org/wiki/EclipseIDE](http://www.ubuntulinux.org/wiki/EclipseIDE)

---

### Post by defkewl on 2005-05-11
Why do you have put a link in /usr/bin?

Just click the eclipse icon or type: /opt/eclipse/eclipse from the command line

---

### Post by Badcel on 2005-05-11
I put it in /usr/bin, so that I can easily start eclipse by typing eclipse, but this is not the point. 

It is always the same, no matter if I click the Eclipse icon or start it in the shell. There ist always an error that refers to the log file and eclipse is not starting.

EDIT: It Works, after I recopied it  :roll:

---

### Post by amohanty on 2005-11-26
I think you will need to launch it from the eclipse folder to which you unzipped the package, because it needs startup.jar and other jars in the folder. Unfortunately symbolic links dont seem to work.

HTH
AM

---

### Post by haocheng on 2005-11-26
This is the command I use to start Eclipse:

```

/home/robin/develop/eclipse/eclipse  -vm /usr/local/src/jdk1.5.0/bin/java  -data /home/robin/develop/projects/workspace

```

Remember to replace the path with your setup.
Hope this helps!

---

