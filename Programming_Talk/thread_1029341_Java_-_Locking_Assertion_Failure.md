---
title: "Java - Locking Assertion Failure ???"
date: 2009-01-03
forum: Programming Talk
---

### Post by PaulM1985 on 2009-01-03
Hi all

I have been trying to run a program that has been given to me from my University to study but every time I run it, it comes up with a "Locking assertion failure".

I am using Netbeans 4.1 and Java version 1.5.0_04.  I have been told by uni that I have to use these versions.

Is there any way that I can fix this problem?  The full output I get when running the program is shown in the next post.


Paul

---

### Post by PaulM1985 on 2009-01-03
```
init:
deps-jar:
compile:
run:
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb1dee767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb1dee8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb1e331bd]
#3 /home/paul/jdk1.5.0_04/jre/lib/i386/xawt/libmawt.so [0xb1f2ba76]
#4 /home/paul/jdk1.5.0_04/jre/lib/i386/xawt/libmawt.so [0xb1f1180a]
#5 /home/paul/jdk1.5.0_04/jre/lib/i386/xawt/libmawt.so [0xb1f11a51]
#6 /home/paul/jdk1.5.0_04/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xb1f11c5c]
#7 [0xb2697b7a]
#8 [0xb2691a7b]
#9 [0xb2691a7b]
#10 [0xb268f157]
#11 /home/paul/jdk1.5.0_04/jre/lib/i386/client/libjvm.so [0xb77bdf8c]
#12 /home/paul/jdk1.5.0_04/jre/lib/i386/client/libjvm.so [0xb78b05f8]
#13 /home/paul/jdk1.5.0_04/jre/lib/i386/client/libjvm.so [0xb77bddbf]
#14 /home/paul/jdk1.5.0_04/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x2dd) [0xb780d03d]
#15 /home/paul/jdk1.5.0_04/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75cc2cd]
#16 [0xb269742b]
#17 [0xb26919a4]
#18 [0xb268f157]
#19 /home/paul/jdk1.5.0_04/jre/lib/i386/client/libjvm.so [0xb77bdf8c]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb1dee767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb1dee81e]
#2 /usr/lib/libX11.so.6 [0xb1e32518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb1e290a6]
#4 /home/paul/jdk1.5.0_04/jre/lib/i386/xawt/libmawt.so [0xb1f106df]
#5 /home/paul/jdk1.5.0_04/jre/lib/i386/xawt/libmawt.so [0xb1f10970]
#6 /home/paul/jdk1.5.0_04/jre/lib/i386/xawt/libmawt.so [0xb1f11b98]
#7 /home/paul/jdk1.5.0_04/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xb1f11c5c]
#8 [0xb2697b7a]
#9 [0xb2691a7b]
#10 [0xb2691a7b]
#11 [0xb268f157]
#12 /home/paul/jdk1.5.0_04/jre/lib/i386/client/libjvm.so [0xb77bdf8c]
#13 /home/paul/jdk1.5.0_04/jre/lib/i386/client/libjvm.so [0xb78b05f8]
#14 /home/paul/jdk1.5.0_04/jre/lib/i386/client/libjvm.so [0xb77bddbf]
#15 /home/paul/jdk1.5.0_04/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x2dd) [0xb780d03d]
#16 /home/paul/jdk1.5.0_04/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75cc2cd]
#17 [0xb269742b]
#18 [0xb26919a4]
#19 [0xb268f157]
BUILD SUCCESSFUL (total time: 11 seconds)
```

---

### Post by CptPicard on 2009-01-03
Google Is Your Friend:

[http://ubuntuforums.org/showthread.php?t=610457](http://ubuntuforums.org/showthread.php?t=610457)

---

