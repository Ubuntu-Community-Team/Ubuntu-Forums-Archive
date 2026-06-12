---
title: "Minecraft crashes after login"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by spikeyseth on 2011-09-11
well i installed ubuntu 11.04 today as a complete novice to the world of linux OS's, all im really using the Ubuntu installation for is to play minecraft, but when i try to play it, i after i login it crashes, every time. no mojang logo or anything. here is the error.

--- BEGIN ERROR REPORT a1dce528 --------
Generated 11/09/11 18:16
Minecraft: Minecraft Beta 1.7.3
OS: Linux (i386) version 2.6.38-11-generic
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]
java.lang.IllegalStateException: Only one LWJGL context may be instantiated
at any one time.
at org.lwjgl.opengl.Display.create(Display.java:846)
at org.lwjgl.opengl.Display.create(Display.java:784)
at org.lwjgl.opengl.Display.create(Display.java:765)
at net.minecraft.client.Minecraft.a(SourceFile:294)
at net.minecraft.client.Minecraft.run(SourceFile:716)
at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 55818c5b ----------


all i have done is installed java and flash player. the computer is old and as such only has the intel chipset for graphics, so idk if that  is an issue. please help, im at my wits end :(

---

### Post by terrykiwi83 on 2011-09-11
have you tried removing minecraft and re-installing a stable release and not the beta?

---

### Post by spikeyseth on 2011-09-11
im guessing you arent familier with minecraft. it is only in a beta stage of release and is normaly very stable. according to other sources the problem may be my gpu, as i need openGL 3d enabled but it isnt enabled by default, perhaps you can help with that.

this is my output of 
```

lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'

```
the output is 
```

 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
direct rendering: Yes
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20
OpenGL extensions:

```

any ideas?

---

### Post by anewguy on 2011-09-11
While it's always possible something has been updated, the 845 graphics normally haven't done very well in Linux.  People have had varying degrees of problems.  Try putting i915.modeset=0 in the boot line and see if that helps.  If not, do the reverse:  i915.modeset=1 and try it.  These help to override some of the kernel mode setting.

Dave ;)

---

### Post by jm2003uk on 2011-09-15
I'm having a similar issue now when trying out the 1.8 release (previous version worked ok). Looking around the web it seems a lot of macs are having this problem but only really found one post from a Linux user, with no replies as of yet.


```
lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'

01:05.0 VGA compatible controller: ATI Technologies Inc 760G [Radeon 3000]
direct rendering: Yes
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 3000 Graphics
OpenGL version string: 3.2.9756 Compatibility Profile Context
OpenGL shading language version string: 1.50
OpenGL extensions:
```

Guess it's probably gonna be a case of just waiting for the game to be patched.

--------

And all of a sudden 1.8 is now working...

---

