---
title: "Maple &amp; Compiz display problem"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by browny254 on 2008-05-30
Hi, i recently installed Compiz and have just gone to run Maple 11 (a maths program) and it is not displaying correctly. The whole window appears as a blank box, but you can still right click in certain areas and the correct menu comes up, so its just the display isn't working.

I found this [http://schlort.net/2008/03/maple-11-and-compiz-fusion/](http://schlort.net/2008/03/maple-11-and-compiz-fusion/) which describes how to fix the problem, but it is for gnome and I have kde so I was hoping someone would know what the corresponding fix would be.

Cheers.

---

### Post by schlort on 2008-06-19
I hope you've been successful in getting it working.  If you haven't, you might try adding the 

AWT_TOOLKIT=MToolkit
export AWT_TOOLKIT

to ~/.kderc rather than ~/.gnomerc. (I do not use KDE and have not tried this.)

---

### Post by browny254 on 2008-06-19
yeah i got it working,

i just added "export AWT_TOOLKIT=MToolkit" to the boot command in the K Menu editor, so it works pretty well except if starting from terminal.

---

### Post by Rasheeke on 2008-12-02
*

---

### Post by natacho on 2009-03-29
I'm trying to run maple 12 with compiz active but...
```
laptop:~$ export AWT_TOOLKIT=MToolkit && xmaple
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f64028919fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7f6402891ab4]
#2 /usr/lib/libX11.so.6(_XReply+0x268) [0x7f640330e698]
#3 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so [0x7f6403ce9d66]
#4 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so [0x7f6403c9897b]
#5 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so [0x7f6403c98c4d]
#6 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x12) [0x7f6403c98ec2]
#7 [0x7f642706e563]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f64028919fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7f6402891b77]
#2 /usr/lib/libX11.so.6 [0x7f640330d8c0]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x2e) [0x7f640330408e]
#4 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so [0x7f6403c97ca5]
#5 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so [0x7f6403c97ef9]
#6 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so [0x7f6403c98cef]
#7 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x12) [0x7f6403c98ec2]
#8 [0x7f642706e563]
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f642ba975ef, pid=30392, tid=1113889104
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x315ef]  catgets+0x1f
#
# An error report file with more information is saved as hs_err_pid30392.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted

```
Thanks for the help

---

### Post by calsaverini on 2009-07-16
I got the following problem trying to use this in my .bashrc:

```

export AWT_TOOLKIT=MToolkit

```

I got this error message with Maple 12 64bits on a Ubuntu 9.04 x86_64. 


```

[pcmec43] ~ > xmaple
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f7122bfa58f, pid=2950, tid=140123173812560
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x3158f]  catgets+0x1f
#
# An error report file with more information is saved as hs_err_pid2950.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted


```

---

