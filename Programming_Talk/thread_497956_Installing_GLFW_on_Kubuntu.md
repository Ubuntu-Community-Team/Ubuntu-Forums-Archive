---
title: "Installing GLFW on Kubuntu"
date: 2007-07-10
forum: Programming Talk
---

### Post by T1Oracle on 2007-07-10
I initially had Ubuntu and then I installed KDE over it so I have GNOME too I just don't use it.

Anyway, I have been trying to install GLFW on Ubuntu but when I tried it could not find glu.h.  Then I ran into some random message forum posts that suggest I install Mesa, so I downloaded Mesa 7.0 from the same site the Ubuntu site links.  Then Mesa's instructions claim that I need libdrm and glproto "if you get any errors about _GLXvop_BindTexImageEXT."  So I installed libdrm and tried to install Mesa and I got errors.  Decided to I try to install glproto but I could not find it until I googled it and found some link on a random message board.  No intructions where to be found anywhere and I have no idea what to do with it.

I have the nVidia 9755 driver for my GeForce 8800GLX, I plan on using the Code::Blocks IDE.

Here is the terminal output from my attempt at installing Mesa 7.0:
> user1@user1-desktop:~/Development_Tools/Libs/Mesa-7.0$ sudo make linux-dri
(cd configs && rm -f current && ln -s linux-dri current)
make default
make[1]: Entering directory `/home/user1/Development_Tools/Libs/Mesa-7.0'
make[2]: Entering directory `/home/user1/Development_Tools/Libs/Mesa-7.0/src'
Making sources for linux-dri
mkdir ../lib
make[3]: Entering directory `/home/user1/Development_Tools/Libs/Mesa-7.0/src/glx/x11'
Makefile:91: depend: No such file or directory
touch depend
makedepend -fdepend -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include glcontextmodes.c clientattrib.c compsize.c eval.c glxcmds.c glxext.c glxextensions.c indirect.c indirect_init.c indirect_size.c indirect_window_pos.c indirect_transpose_matrix.c indirect_vertex_array.c indirect_vertex_program.c pixel.c pixelstore.c render2.c renderpix.c single2.c singlepix.c vertarr.c xfont.c glx_pbuffer.c glx_query.c glx_texture_compression.c dri_glx.c XF86dri.c \
                ../../../src/mesa/main/dispatch.c ../../../src/mesa/glapi/glapi.c ../../../src/mesa/glapi/glthread.c
makedepend: warning:  glcontextmodes.c (reading /usr/include/bits/types.h, line 31): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/local/include/stddef.h
        not in /usr/local/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/sys/types.h, line 147): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/local/include/stddef.h
        not in /usr/local/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/X11/Xlib.h, line 75): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/local/include/stddef.h
        not in /usr/local/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading ../../../include/GL/glext.h, line 3385): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/local/include/stddef.h
        not in /usr/local/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/inttypes.h, line 38): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/local/include/stddef.h
        not in /usr/local/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/string.h, line 33): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/local/include/stddef.h
        not in /usr/local/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/stdlib.h, line 33): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/local/include/stddef.h
        not in /usr/local/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/alloca.h, line 25): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/local/include/stddef.h
        not in /usr/local/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/X11/Xlibint.h, line 347): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/local/include/stddef.h
        not in /usr/local/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/stdio.h, line 34): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/local/include/stddef.h
        not in /usr/local/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/_G_config.h, line 14): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/local/include/stddef.h
        not in /usr/local/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/wchar.h, line 48): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/local/include/stddef.h
        not in /usr/local/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/gconv.h, line 31): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/local/include/stddef.h
        not in /usr/local/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/libio.h, line 53): cannot find include file "stdarg.h"
        not in ./stdarg.h
        not in ../../../include/stdarg.h
        not in ../../../include/GL/internal/stdarg.h
        not in ../../../src/mesa/main/stdarg.h
        not in ../../../src/mesa/glapi/stdarg.h
        not in /usr/local/include/stdarg.h
        not in /usr/local/include/drm/stdarg.h
        not in /usr/X11R6/include/stdarg.h
        not in /usr/include/stdarg.h
makedepend: warning:  glxcmds.c (reading /usr/include/limits.h, line 125): cannot find include file "limits.h"
makedepend: warning:  glxcmds.c (reading ../../../src/mesa/main/glheader.h, line 68): cannot find include file "float.h"
        not in ./float.h
        not in ../../../include/float.h
        not in ../../../include/GL/internal/float.h
        not in ../../../src/mesa/main/float.h
        not in ../../../src/mesa/glapi/float.h
        not in /usr/local/include/float.h
        not in /usr/local/include/drm/float.h
        not in /usr/X11R6/include/float.h
        not in /usr/include/float.h
makedepend: warning:  glxcmds.c (reading ../../../src/mesa/main/glheader.h, line 69): cannot find include file "stdarg.h"
        not in ./stdarg.h
        not in ../../../include/stdarg.h
        not in ../../../include/GL/internal/stdarg.h
        not in ../../../src/mesa/main/stdarg.h
        not in ../../../src/mesa/glapi/stdarg.h
        not in /usr/local/include/stdarg.h
        not in /usr/local/include/drm/stdarg.h
        not in /usr/X11R6/include/stdarg.h
        not in /usr/include/stdarg.h
makedepend: warning:  glxext.c, line 51: cannot find include file "X11/extensions/Xfixes.h"
        not in ./X11/extensions/Xfixes.h
        not in ../../../include/X11/extensions/Xfixes.h
        not in ../../../include/GL/internal/X11/extensions/Xfixes.h
        not in ../../../src/mesa/main/X11/extensions/Xfixes.h
        not in ../../../src/mesa/glapi/X11/extensions/Xfixes.h
        not in /usr/local/include/X11/extensions/Xfixes.h
        not in /usr/local/include/drm/X11/extensions/Xfixes.h
        not in /usr/X11R6/include/X11/extensions/Xfixes.h
        not in /usr/include/X11/extensions/Xfixes.h
makedepend: warning:  glxext.c, line 52: cannot find include file "X11/extensions/Xdamage.h"
        not in ./X11/extensions/Xdamage.h
        not in ../../../include/X11/extensions/Xdamage.h
        not in ../../../include/GL/internal/X11/extensions/Xdamage.h
        not in ../../../src/mesa/main/X11/extensions/Xdamage.h
        not in ../../../src/mesa/glapi/X11/extensions/Xdamage.h
        not in /usr/local/include/X11/extensions/Xdamage.h
        not in /usr/local/include/drm/X11/extensions/Xdamage.h
        not in /usr/X11R6/include/X11/extensions/Xdamage.h
        not in /usr/include/X11/extensions/Xdamage.h
make[3]: Leaving directory `/home/user1/Development_Tools/Libs/Mesa-7.0/src/glx/x11'
make[3]: Entering directory `/home/user1/Development_Tools/Libs/Mesa-7.0/src/glx/x11'
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/X11R6/lib/modules/dri\" glcontextmodes.c -o glcontextmodes.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/X11R6/lib/modules/dri\" clientattrib.c -o clientattrib.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/X11R6/lib/modules/dri\" compsize.c -o compsize.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/X11R6/lib/modules/dri\" eval.c -o eval.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/X11R6/lib/modules/dri\" glxcmds.c -o glxcmds.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/X11R6/lib/modules/dri\" glxext.c -o glxext.o
glxext.c:51:35: error: X11/extensions/Xfixes.h: No such file or directory
glxext.c:52:36: error: X11/extensions/Xdamage.h: No such file or directory
glxext.c:781: warning: initialization from incompatible pointer type
glxext.c:783: warning: initialization from incompatible pointer type
glxext.c:788: warning: initialization from incompatible pointer type
glxext.c:791: warning: initialization from incompatible pointer type
glxext.c:793: warning: initialization from incompatible pointer type
make[3]: *** [glxext.o] Error 1
make[3]: Leaving directory `/home/user1/Development_Tools/Libs/Mesa-7.0/src/glx/x11'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/user1/Development_Tools/Libs/Mesa-7.0/src'
make[1]: *** [default] Error 1
make[1]: Leaving directory `/home/user1/Development_Tools/Libs/Mesa-7.0'
make: *** [linux-dri] Error 2
user1@user1-desktop:~/Development_Tools/Libs/Mesa-7.0$

I'm out of ideas on this one, please help me install GLFW so I can get back to OpenGL development.

---

### Post by T1Oracle on 2007-07-10
Nevermind, I solved it.

---

### Post by djheadley on 2007-07-11
How?

---

### Post by T1Oracle on 2007-07-25
I had to install "freeglut3-dev" using apt-get.

---

