---
title: "Java installer (SPSS) blank screen"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Mpemba on 2008-11-01
Hello,

I'm trying to install SPSS onto my 8.04 ubuntu install. 

Everything works fine until I get to the java installer. Instead of the correct buttons being displayed, I get a blank screen. If i click the bottom right corner of the installer box, it asks if i want to quit; i assume therefore that the buttons are there, I just can't see them.

Can anybody tell me why this is? Am i missing some things?

Thanks so much!

---

### Post by Mpemba on 2008-12-01
Major bump but I have decided to give this another go.

Any help anybody? Would be much appreciated!

---

### Post by Mpemba on 2008-12-01
/media/spss16linux$ ./setup.bin








          Initializing Wizard........
          Launching InstallShield Wizard........









          
          






Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb2571767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb25718b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0x94fc31bd]
#3 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/xawt/libmawt.so [0x950a3d3e]
#4 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/xawt/libmawt.so [0x9508dd47]
#5 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/xawt/libmawt.so [0x9508dec3]
#6 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0x9508e106]
#7 [0xb25fec4b]
#8 [0xb25f8b3b]
#9 [0xb25f8b3b]
#10 [0xb25f6217]
#11 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/client/libjvm.so [0xb7795d8c]
#12 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/client/libjvm.so [0xb78a9fd8]
#13 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/client/libjvm.so [0xb7795bbf]
#14 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb77f334d]
#15 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75912cd]
#16 [0xb25fe4eb]
#17 [0xb25f8a64]
#18 [0xb25f6217]
#19 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/client/libjvm.so [0xb7795d8c]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb2571767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb257181e]
#2 /usr/lib/libX11.so.6 [0x94fc2518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0x94fb90a6]
#4 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/xawt/libmawt.so [0x9508d089]
#5 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/xawt/libmawt.so [0x9508d2d3]
#6 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/xawt/libmawt.so [0x9508df71]
#7 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0x9508e106]
#8 [0xb25fec4b]
#9 [0xb25f8b3b]
#10 [0xb25f8b3b]
#11 [0xb25f6217]
#12 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/client/libjvm.so [0xb7795d8c]
#13 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/client/libjvm.so [0xb78a9fd8]
#14 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/client/libjvm.so [0xb7795bbf]
#15 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb77f334d]
#16 /tmp/istemp15971336100502/_bundledJRE_/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75912cd]
#17 [0xb25fe4eb]
#18 [0xb25f8a64]
#19 [0xb25f6217]
/usr/share/themes/Crux/gtk-2.0/gtkrc:37: error: lexical error or unexpected token, expected valid token


This is the terminal output for when i rub the installer!

---

### Post by jbtito03 on 2008-12-18
Do you have compiz running? Try to turn it off.

Cheers 

J.B.

---

### Post by vehka on 2009-11-11
Thank you, turning Compiz off worked (System/Preferences/Appearance/Visual Effects/None).

Using Ubuntu 9.10 and SPSS 17.0.

---

