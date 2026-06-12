---
title: "C++BuilderX install problem"
date: 2005-02-21
forum: Programming Talk
---

### Post by Pierre Maurette on 2005-02-21
Hi,
I own C++BuilderX. It is roughly a Windows/Linux/Solaris IDE, a C/C++ JBuilderX, Java written et finaly close from Eclipse as an IDE.
It is supported for installing under Red Hat, but I installed without any problem on a Debian 3.0r1.
I can't install on Ubuntu4.10, 64bits.
Here is the output from my attemp:

root@ubuntu:/media/cdrom0/Linux # sh ./install.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

current locale is not supported in X11, locale is set to CX locale modifiers are not supported, using defaultInvocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.InternalError: Current locale is not supported
        at sun.awt.motif.MWindowPeer.pSetTitle(Native Method)
        at sun.awt.motif.MWindowPeer.init(Unknown Source)
        at sun.awt.motif.MFramePeer.<init>(Unknown Source)
        at sun.awt.motif.MToolkit.createFrame(Unknown Source)
        at java.awt.Frame.addNotify(Unknown Source)
        at com.zerog.ia.installer.Main.d(DashoA8113)
        at com.zerog.ia.installer.Main.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
GUI-
root@ubuntu:/media/cdrom0/Linux #

Any idea ?
Thx in advance
-- 
Pierre

---

### Post by defkewl on 2005-02-27
I never knew that they made cpp builder for linux. hehe

---

### Post by manstrike on 2005-03-08
you may need to try a different java vm

---

