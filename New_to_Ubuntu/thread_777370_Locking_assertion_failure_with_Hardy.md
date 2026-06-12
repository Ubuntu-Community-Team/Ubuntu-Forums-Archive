---
title: "Locking assertion failure with Hardy"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by incen on 2008-05-01
Hi, I just installed Hardy two days ago. Well, due to many reasons, I had to forget 7.10 and did this. However, there is a weird problem I have with Hardy.

I need MATLAB for research. However, the installation worked just fine as before. But when I tried to launch MATLAB, here came the error message:

```
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f8a7d2db97c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7f8a7d2dba84]
#2 /usr/lib/libX11.so.6(_XReply+0x10f) [0x7f8a7ebc4f4f]
#3 /usr/local/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so [0x7f8a609e5416]
#4 /usr/local/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so [0x7f8a609c81db]
#5 /usr/local/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so [0x7f8a609c84ad]
#6 /usr/local/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x12) [0x7f8a609c8722]
#7 [0x7f8a75cd0563]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f8a7d2db97c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f8a7d2dba15]
#2 /usr/lib/libX11.so.6 [0x7f8a7ebc4323]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x2c) [0x7f8a7ebbb72c]
#4 /usr/local/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so [0x7f8a609c7575]
#5 /usr/local/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so [0x7f8a609c77c9]
#6 /usr/local/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so [0x7f8a609c854f]
#7 /usr/local/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x12) [0x7f8a609c8722]
#8 [0x7f8a75cd0563]
```

Can anyone help me to solve this? Thanks!

---

