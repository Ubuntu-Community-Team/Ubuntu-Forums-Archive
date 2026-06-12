---
title: "Problems with Java programs"
date: 2006-11-05
forum: Programming Talk
---

### Post by jc750kwak on 2006-11-05
I have two java programs that don't work on my system

I have Sun's java 1.5.0 installed:

john@athlon:$ java -version java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

john@athlon:$ sudo update-alternatives --config java
There is only 1 program which provides java
(/usr/lib/jvm/java-1.5.0-sun/jre/bin/java). Nothing to configure.

The first program is a jar file that communicates with my Rio Karma MP3 player across ethernet. The output from this is: 

john@athlon:~/Deb_files$ java -jar /home/john/Desktop/rmmlite.jar
Exception in thread "main" java.lang.UnsatisfiedLinkError: XKeysymToKeycode
	at sun.awt.X11.XlibWrapper.XKeysymToKeycode(Native Method)
	at sun.awt.X11.XToolkit.keysymToPrimaryKeycode(XToolkit.java:1139)
	at sun.awt.X11.XToolkit.setupModifierMap(XToolkit.java:1155)
	at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:103)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:164)
	at java.awt.Toolkit$2.run(Toolkit.java:821)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
	at java.awt.Window.getToolkit(Window.java:759)
	at java.awt.Window.init(Window.java:285)
	at java.awt.Window.<init>(Window.java:318)
	at java.awt.Frame.<init>(Frame.java:419)
	at javax.swing.JFrame.<init>(JFrame.java:194)
	at com.rio.rmmlite.ChooseRmmlOrTaxi.main(ChooseRmmlOrTaxi.java:22)

The second program is Limewire, the P2P sharing program. The output from this is:

john@athlon:~/Deb_files$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]
Configuring environment...
Loading LimeWire:

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:

java.lang.UnsatisfiedLinkError: XKeysymToKeycode
	at sun.awt.X11.XlibWrapper.XKeysymToKeycode(Native Method)
	at sun.awt.X11.XToolkit.keysymToPrimaryKeycode(XToolkit.java:1139)
	at sun.awt.X11.XToolkit.setupModifierMap(XToolkit.java:1155)
	at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:103)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:164)
	at java.awt.Toolkit$2.run(Toolkit.java:821)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
	at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
	at com.limegroup.gnutella.gui.Main.main(Main.java:39)
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

So whatever my problem is it seems to be consistent for these two.

Can anybody help me please ?

John

---

### Post by McLoud on 2006-11-05
That is very weird, both programs are trying to use XKeysymToKeycode, which is a xlib function and seems to be use by a lot of programs (including gtk). Do you have the base Xorg libraries properly installed?  I did a quick test with limeware here and seems to work fine.

---

### Post by jc750kwak on 2006-11-05
Do you know which xlib ?

I have searched for xorg in synaptic and there are loads of libraries listed so I have done ldconfig -p and piped the output to a text file but I need to know which library to look for

Thanks for the quick reply btw

John

---

### Post by McLoud on 2006-11-06
I think it's inside libX11 (package libX11-6)

---

### Post by jc750kwak on 2006-11-17
I've got that properly installed. In fact I reinstalled xorg just to be sure but I get the same errors.

On my sons Mandriva 2005 PC Limewire runs fine.

Looks like I'll have to do a full reinstall

Bugger !

---

### Post by patrick295767 on 2006-11-17
```
apt-get -f install sun-java5-bin
```
can be maybe a better solution for having java installed

---

### Post by jc750kwak on 2006-11-22
> **patrick295767 said:**
> ```
apt-get -f install sun-java5-bin
```
can be maybe a better solution for having java installed

Tried that but got message that 0 packages were installed because sun-java5-bin was already installed

I think perhaps upgrading tp Nvidia's drivers for my GeForce2 nd installing XGL and Compiz  might have caused this so I'm gonna do a clean reinstall

Thanks for the help

---

