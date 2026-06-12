---
title: "Install a driver for X server keyboard"
date: 2010-04-28
forum: Programming Talk
---

### Post by DBQ on 2010-04-28
Hi, I would like to replace my current X server keyboard driver with the following: [http://xorg.freedesktop.org/archive/individual/driver/xf86-input-keyboard-1.3.1.tar.bz2](http://xorg.freedesktop.org/archive/individual/driver/xf86-input-keyboard-1.3.1.tar.bz2)

I want to do this so I can modify the code, build it, and experiment on it. However, I am having trouble compiling (output below). Any suggestions?

Also, please let me know if you are aware of a better way to mess with the keyboard driver code of the X-server. Thank You!

.
.
.
kbd.c:31:24: error: atKeynames.h: No such file or directory
kbd.c: In function 'InitKBD':
kbd.c:493: error: 'KEY_CapsLock' undeclared (first use in this function)
kbd.c:493: error: (Each undeclared identifier is reported only once
kbd.c:493: error: for each function it appears in.)
kbd.c:498: error: 'KEY_NumLock' undeclared (first use in this function)
kbd.c: In function 'PostKbdEvent':
kbd.c:657: error: 'KEY_BackSpace' undeclared (first use in this function)
kbd.c:677: error: 'AltMask' undeclared (first use in this function)
kbd.c:677: error: 'KEY_SysReqest' undeclared (first use in this function)
kbd.c:678: error: 'KEY_Print' undeclared (first use in this function)
kbd.c:679: error: 'KEY_Break' undeclared (first use in this function)
.
.
.

---

