---
title: "problem on staring matlab r2008a"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by d_messiah on 2008-06-20
hi,

i'v just installed ubuntu 8.04 64-bit edition on hp xw9300 workstation. while, when starting matlab r2008a from terminal window, it has the following error

[PHP]Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f0e62e7197c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7f0e62e71a84]
#2 /usr/lib/libX11.so.6(_XReply+0x10f) [0x7f0e64848f4f]
#3 /home/dongxch/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so [0x7f0e4645d486]
#4 /home/dongxch/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so [0x7f0e464401db]
#5 /home/dongxch/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so [0x7f0e464404ad]
#6 /home/dongxch/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x12) [0x7f0e46440722]
#7 [0x7f0e5b88b563]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f0e62e7197c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f0e62e71a15]
#2 /usr/lib/libX11.so.6 [0x7f0e64848323]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x2c) [0x7f0e6483f72c]
#4 /home/dongxch/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so [0x7f0e4643f575]
#5 /home/dongxch/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so [0x7f0e4643f7c9]
#6 /home/dongxch/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so [0x7f0e4644054f]
#7 /home/dongxch/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x12) [0x7f0e46440722]
#8 [0x7f0e5b88b563][/PHP]


i am an absolutely new user, can anyone help me? many thx!

---

### Post by jpkotta on 2008-06-22
I have r2007a, and it works fine for me.  I also get the lock assertion failures, so it's probably something else.

Try the -nojvm and/or -nodesktop options.

---

