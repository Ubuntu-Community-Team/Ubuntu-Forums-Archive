---
title: "How can I compile a xorg-driver?"
date: 2006-01-27
forum: Programming Talk
---

### Post by luopio on 2006-01-27
Hi. I've been trying to get my aiptektablet to work for years.. first with gentoo and now running ubuntu 5.10. I'm quite confident that compiling the newest xserver-driver from CVS would solve the rest of my problems with the tablet. 

.. But I can't get it compiled. From CVS I get one c-file, one header-file and an Imakefile. Just figured out how to construct the Makefile with Imake. I did it like this in the driver directory: ```
$ imake -I/etc/X11/config/cf/
```

The result was a makefile. Then feeling optimistic I tried ```
make
```
And got ```
$ make
rm -f xf86Aiptek.o
gcc -m32 -g -O2 -fno-strict-aliasing -ansi -pedantic -Wall -Wpointer-arith -Wstrict-prototypes  -Wmissing-prototypes -Wmissing-declarations                      -Wredundant-decls -Wnested-externs -Wundef     -I. -I./programs/Xserver/hw/xfree86/common -I./programs/Xserver/hw/xfree86/loader -I./programs/Xserver/hw/xfree86/os-support      -I./programs/Xserver/include -I./programs/Xserver/mi -I/usr/include/X11 -I./include/extensions  -I. -I./exports/include   -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                          -D_POSIX_SOURCE -D_XOPEN_SOURCE                          -D_BSD_SOURCE -D_SVID_SOURCE -D_GNU_SOURCE                            -DSHAPE -DXINPUT -DXKB -DLBX -DXAPPGROUP       -DXCSECURITY -DTOGCUP        -DXF86BIGFONT -DDPMSExtension    -DPIXPRIV -DPANORAMIX   -DRENDER -DRANDR       -DXFIXES -DDAMAGE -DCOMPOSITE -DXEVIE         -DGCCUSESGAS -DAVOID_GLYPHBLT -DPIXPRIV -DSINGLEDEPTH                          -DXFreeXDGA -DXvExtension                            -DXFree86LOADER  -DXFree86Server                            -DXF86VIDMODE                            -DXvMCExtension                                 -DSMART_SCHEDULE    -DBUILDDEBUG -DXResExtension                             -DX_BYTE_ORDER=X_LITTLE_ENDIAN                      -DXORG_VERSION_CURRENT="(((6) * 10000000) + ((8) * 100000) + ((2) * 1000) + 0)" -DNDEBUG   -DFUNCPROTO=15 -DNARROWPROTO  -DIN_MODULE -DXFree86Module    -c xf86Aiptek.c
In file included from xf86Aiptek.c:163:
xf86Aiptek.h:57:25: error: xf86Version.h: No such file or directory
xf86Aiptek.h:59:18: error: misc.h: No such file or directory
xf86Aiptek.h:60:18: error: xf86.h: No such file or directory
xf86Aiptek.h:61:24: error: xf86_ansic.h: No such file or directory
xf86Aiptek.h:62:18: error: xisb.h: No such file or directory
xf86Aiptek.h:64:25: error: xf86_OSproc.h: No such file or directory
[...... continues like this for pages.....]

```

Couldn't find the needed header-files with locate and couldn't find an appropriate package through synaptic. Where are they? Anything else I need to do to get this driver compiled?

---

