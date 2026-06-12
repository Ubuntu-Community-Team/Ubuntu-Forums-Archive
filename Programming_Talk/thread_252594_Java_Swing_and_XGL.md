---
title: "Java Swing and XGL?"
date: 2006-09-07
forum: Programming Talk
---

### Post by Seine on 2006-09-07
G'day

I've recently enabled XGL. Sweet. But this has stopped my otherwise super-performing NetBeans IDE (a Java Swing application) to render as a solid grey box. :(

Does anyone know of issues/tricks regarding getting Swing apps to render under XGL?

Cheers
Jem

---

### Post by machaval on 2006-10-26
There is a path to the XGL that will fix your problem. I'm trying to mage beryl guys to include it on the edgy repositoy.

---

### Post by boban on 2006-10-27
> **machaval said:**
> There is a path to the XGL that will fix your problem. I'm trying to mage beryl guys to include it on the edgy repositoy.

Hi!

I have the same problem... Just let us know when patch will be available...

---

### Post by boban on 2006-10-30
> **Seine said:**
> G'day
Does anyone know of issues/tricks regarding getting Swing apps to render under XGL?



I've searched beryl forums and I think I found solution... Edit file /etc/environment and add line 

```

AWT_TOOLKIT="MToolkit"

```

then reboot... Don't know if it will help with NetBeans, but it helped me in other apps (e.g. JUDE)

---

### Post by kaz_greece on 2006-11-02
worked for me!!! Netbeans 5.5 Thanks man:)

---

### Post by boban on 2006-11-02
> **kaz_greece said:**
> worked for me!!! Netbeans 5.5 Thanks man:)

Cool! :)

You are welcome:)

---

### Post by littledeer1974 on 2007-01-29
Hi, Everyone.
 Actually I have the same problem but not about Netbeans.
 I am using Eclipse 3.2 to develop a certain swing application, when I'm using Beryl, Eclipse is fine, but my Swing application won't show anything, but that solid gray wall.

 And I also tried the /etc/environment thing as mentioned in previous post, but it's still not working for me,  (while My Splash Window is OK, using JWindow Class):confused: Is there any further tips?
 Thanks in advance.

*PROBLEM SOLVED*
sorry everyone, I forgot to reboot, it works perfect, thanks!!

---

### Post by Ramses de Norre on 2007-01-29
I installed beryl from deb **[http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main** and have java6 installed with ```
export _JAVA_OPTIONS="-Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel"
```
set and beryl and xgl render all my swing applications fine.

---

### Post by buzzler on 2007-05-11
hi
im using feisty, netbeans 5.5 and jdk6
ive tried editing /etc/environment with AWT_TOOLKIT="MToolkit" but failed
i got the following msg

> java.lang.UnsatisfiedLinkError: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/motif21/libmawt.so: libXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
        at java.lang.Runtime.load0(Runtime.java:770)
        at java.lang.System.load(System.java:1005)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.loadLibraries(Toolkit.java:1594)
        at java.awt.Toolkit.<clinit>(Toolkit.java:1616)
        at java.awt.Color.<clinit>(Color.java:263)
        at javax.swing.plaf.metal.MetalTheme.<clinit>(MetalTheme.java:59)
        at javax.swing.plaf.metal.MetalLookAndFeel.getCurrentTheme(MetalLookAndFeel.java:1673)
        at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(MetalLookAndFeel.java:1568)
        at javax.swing.plaf.metal.MetalLookAndFeel.getDefaults(MetalLookAndFeel.java:1590)
        at javax.swing.UIManager.setLookAndFeel(UIManager.java:537)
        at javax.swing.UIManager.setLookAndFeel(UIManager.java:577)
        at javax.swing.UIManager.initializeDefaultLAF(UIManager.java:1331)
        at javax.swing.UIManager.initialize(UIManager.java:1418)
        at javax.swing.UIManager.maybeInitialize(UIManager.java:1406)
        at javax.swing.UIManager.getDefaults(UIManager.java:656)
        at javax.swing.filechooser.FileSystemView.getFileSystemView(FileSystemView.java:63)
        at org.openide.filesystems.FileUtil.<clinit>(FileUtil.java:64)
        at org.netbeans.core.startup.TopLogging.printSystemInfo(TopLogging.java:187)
        at org.netbeans.core.startup.TopLogging.<init>(TopLogging.java:112)
        at org.netbeans.core.startup.CLIOptions.initialize(CLIOptions.java:205)
        at org.netbeans.core.startup.Main.start(Main.java:294)
        at org.netbeans.core.startup.TopThreadGroup.run(TopThreadGroup.java:96)
        at java.lang.Thread.run(Thread.java:619)
java.lang.UnsatisfiedLinkError: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/motif21/libmawt.so: libXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
        at java.lang.Runtime.load0(Runtime.java:770)
        at java.lang.System.load(System.java:1005)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.loadLibraries(Toolkit.java:1594)
        at java.awt.Toolkit.<clinit>(Toolkit.java:1616)
        at java.awt.Color.<clinit>(Color.java:263)
        at javax.swing.plaf.metal.MetalTheme.<clinit>(MetalTheme.java:59)
        at javax.swing.plaf.metal.MetalLookAndFeel.getCurrentTheme(MetalLookAndFeel.java:1673)
        at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(MetalLookAndFeel.java:1568)
        at javax.swing.plaf.metal.MetalLookAndFeel.getDefaults(MetalLookAndFeel.java:1590)
        at javax.swing.UIManager.setLookAndFeel(UIManager.java:537)
        at javax.swing.UIManager.setLookAndFeel(UIManager.java:577)
        at javax.swing.UIManager.initializeDefaultLAF(UIManager.java:1331)
        at javax.swing.UIManager.initialize(UIManager.java:1418)
        at javax.swing.UIManager.maybeInitialize(UIManager.java:1406)
        at javax.swing.UIManager.getDefaults(UIManager.java:656)
        at javax.swing.filechooser.FileSystemView.getFileSystemView(FileSystemView.java:63)
        at org.openide.filesystems.FileUtil.<clinit>(FileUtil.java:64)
        at org.netbeans.core.startup.TopLogging.printSystemInfo(TopLogging.java:187)
        at org.netbeans.core.startup.TopLogging.<init>(TopLogging.java:112)
        at org.netbeans.core.startup.CLIOptions.initialize(CLIOptions.java:205)
        at org.netbeans.core.startup.Main.start(Main.java:294)
        at org.netbeans.core.startup.TopThreadGroup.run(TopThreadGroup.java:96)
        at java.lang.Thread.run(Thread.java:619)


pls help me ..

---

### Post by xcesarfrancox on 2007-10-22
Hi, I'm using Gutsy and Compiz Fusion and it has a plugin in the CCSM named "Workarounds" and there it can be enabled a fix for java apps and other stuff, it works just fine for me

---

