---
title: "building gtk+-3.0.5"
date: 2011-03-25
forum: Packaging and Compiling Programs
---

### Post by cjejuni on 2011-03-25
error:

make[4]: Entering directory `/home/nes/Downloads/gtk+-3.0.5/gdk/x11'
  CC     gdkapplaunchcontext-x11.lo
  CC     gdkasync.lo
  CC     gdkcursor-x11.lo
  CC     gdkdevice-core-x11.lo
  CC     gdkdevice-xi.lo
In file included from gdkdevice-xi.c:24:
gdkdeviceprivate-xi.h:28: fatal error: X11/extensions/XInput.h: No such file or directory
compilation terminated.

what do i need to install? 
thanks.

---

### Post by MadCow108 on 2011-03-25
$ apt-file search XInput.h
libxi-dev: /usr/include/X11/extensions/XInput.h

---

