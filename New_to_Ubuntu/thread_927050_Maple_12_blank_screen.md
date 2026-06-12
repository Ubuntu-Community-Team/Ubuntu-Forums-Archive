---
title: "Maple 12 blank screen"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by crowhill on 2008-09-22
Hi there

I just installed Maple 12 on my brand new laptop that runs Ubuntu 8.04. Everything worked fine except for when I start the program I get a blank window and the terminal says (after typing bash xmaple (see below)):
> $ bash xmaple
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x97202767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0x972028b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0x96aab1bd]
#3 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x96b8a22e]
#4 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x96b68ed7]
#5 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x96b69188]
#6 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0x96b6948f]
#7 [0xb4c8eb5b]
#8 [0xb4c86ecd]
#9 [0xb4c86ecd]
#10 [0xb4c84207]
#11 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0x62b521d]
#12 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0x643d9a8]
#13 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0x62b50b0]
#14 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x34b) [0x630af2b]
#15 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7c9f96d]
#16 [0xb4c8eb5b]
#17 [0xb4c86d67]
#18 [0xb4c84207]
#19 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0x62b521d]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x97202767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0x9720281e]
#2 /usr/lib/libX11.so.6 [0x96aaa518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0x96aa10a6]
#4 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x96b68189]
#5 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x96b683d5]
#6 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so [0x96b69239]
#7 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0x96b6948f]
#8 [0xb4c8eb5b]
#9 [0xb4c86ecd]
#10 [0xb4c86ecd]
#11 [0xb4c84207]
#12 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0x62b521d]
#13 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0x643d9a8]
#14 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so [0x62b50b0]
#15 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x34b) [0x630af2b]
#16 /home/a/installed/maple12/jre.IBM_INTEL_LINUX/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7c9f96d]
#17 [0xb4c8eb5b]
#18 [0xb4c86d67]
#19 [0xb4c84207]

What is going on here? Is my Java badly behaving? What can I do? Does it have to do with my Nvidia graphics card? Does it have to do with Compiz? I'm lost.

Some help would be extremely appreciated.

Cheers,
crowhill.

---

### Post by Nepherte on 2008-09-22
Try disabling compiz fusion effects (system > preferences > appearance > special effects). I've had similar issues and that seemed to help.

---

### Post by crowhill on 2008-09-22
hi there!

this works for me too :) unfortunately, i loose all my nice compiz settings :(

well, i guess, i have to reset my preferences :)

cheers,
thanks again,
crowhill.

---

### Post by matyasfalvi on 2008-09-26
And thank you sooooooooooooooooo much!!!

---

### Post by Seinfeld on 2009-03-30
Hi .. Well it happened with me in both Matlab and Maple. I have no cmpiz on. So I get both running however I still have the Java warnings.  
In Matlab I just added the following line to the .bashrc file.

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.10/jre
 so problem solved for Matlab.. 
Any clue what to do with Maple?? Why this happens??  It began when I upgraded from Ubuntu 7.10 to 8.04 and after .. Is it a Java bug ?? I appreciate some detailed explanation..

Thanks a lot..

---

### Post by gleedadswell on 2010-04-21
Another option is to use "Classic Worksheet" Maple, which seems to have no issue with compiz settings.  In my (limited) experience, most long-time users of Maple find the interface on non-classic Maple to get in the way more than it helps anyway.  If you're not familiar with it then, under linux you run it with: 

maple -cw

---

