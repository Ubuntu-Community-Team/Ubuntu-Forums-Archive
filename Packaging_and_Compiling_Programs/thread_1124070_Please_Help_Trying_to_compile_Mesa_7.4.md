---
title: "Please Help: Trying to compile Mesa 7.4"
date: 2009-04-13
forum: Packaging and Compiling Programs
---

### Post by WalmartSniperLX on 2009-04-13
After downloading the source package from sourceforge, I extracted the contents and followed the directions on [http://mesa3d.org/](http://mesa3d.org/) 

According to the page that describes how to compile/install it says to issue make and select the 'linux-dri' build.
When trying to run 'make linux-dri' I get this output:

```
patrick@patrick-laptop:~/Desktop/Mesa-7.4$ make linux-dri
(cd configs && rm -f current && ln -s linux-dri current)
make default
make[1]: Entering directory `/home/patrick/Desktop/Mesa-7.4'
make[2]: Entering directory `/home/patrick/Desktop/Mesa-7.4/src'
Making sources for linux-dri
make[3]: Entering directory `/home/patrick/Desktop/Mesa-7.4/src/glx/x11'
touch depend
makedepend -fdepend -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include glcontextmodes.c clientattrib.c compsize.c eval.c glxcmds.c glxcurrent.c glxext.c glxextensions.c indirect.c indirect_init.c indirect_size.c indirect_window_pos.c indirect_texture_compression.c indirect_transpose_matrix.c indirect_vertex_array.c indirect_vertex_program.c pixel.c pixelstore.c render2.c renderpix.c single2.c singlepix.c vertarr.c xfont.c glx_pbuffer.c glx_query.c drisw_glx.c dri_common.c dri_glx.c XF86dri.c glxhash.c dri2_glx.c dri2.c \
		../../../src/mesa/main/dispatch.c ../../../src/mesa/glapi/glapi.c ../../../src/mesa/glapi/glapi_getproc.c ../../../src/mesa/glapi/glthread.c  
makedepend: warning:  glcontextmodes.c (reading /usr/include/sys/types.h, line 147): cannot find include file "stddef.h"
	not in ./stddef.h
	not in ../../../include/stddef.h
	not in ../../../include/GL/internal/stddef.h
	not in ../../../src/mesa/stddef.h
	not in ../../../src/mesa/glapi/stddef.h
	not in /usr/include/drm/stddef.h
	not in /usr/X11R6/include/stddef.h
	not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/X11/Xlib.h, line 75): cannot find include file "stddef.h"
	not in ./stddef.h
	not in ../../../include/stddef.h
	not in ../../../include/GL/internal/stddef.h
	not in ../../../src/mesa/stddef.h
	not in ../../../src/mesa/glapi/stddef.h
	not in /usr/include/drm/stddef.h
	not in /usr/X11R6/include/stddef.h
	not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading ../../../include/GL/glext.h, line 3904): cannot find include file "stddef.h"
	not in ./stddef.h
	not in ../../../include/stddef.h
	not in ../../../include/GL/internal/stddef.h
	not in ../../../src/mesa/stddef.h
	not in ../../../src/mesa/glapi/stddef.h
	not in /usr/include/drm/stddef.h
	not in /usr/X11R6/include/stddef.h
	not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/inttypes.h, line 38): cannot find include file "stddef.h"
	not in ./stddef.h
	not in ../../../include/stddef.h
	not in ../../../include/GL/internal/stddef.h
	not in ../../../src/mesa/stddef.h
	not in ../../../src/mesa/glapi/stddef.h
	not in /usr/include/drm/stddef.h
	not in /usr/X11R6/include/stddef.h
	not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c, line 42: cannot find include file "GL/glxint.h"
	not in GL/glxint.h
	not in GL/glxint.h
	not in ./GL/glxint.h
	not in ../../../include/GL/glxint.h
	not in ../../../include/GL/internal/GL/glxint.h
	not in ../../../src/mesa/GL/glxint.h
	not in ../../../src/mesa/glapi/GL/glxint.h
	not in /usr/include/drm/GL/glxint.h
	not in /usr/X11R6/include/GL/glxint.h
	not in /usr/include/GL/glxint.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/string.h, line 33): cannot find include file "stddef.h"
	not in ./stddef.h
	not in ../../../include/stddef.h
	not in ../../../include/GL/internal/stddef.h
	not in ../../../src/mesa/stddef.h
	not in ../../../src/mesa/glapi/stddef.h
	not in /usr/include/drm/stddef.h
	not in /usr/X11R6/include/stddef.h
	not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/stdlib.h, line 33): cannot find include file "stddef.h"
	not in ./stddef.h
	not in ../../../include/stddef.h
	not in ../../../include/GL/internal/stddef.h
	not in ../../../src/mesa/stddef.h
	not in ../../../src/mesa/glapi/stddef.h
	not in /usr/include/drm/stddef.h
	not in /usr/X11R6/include/stddef.h
	not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/alloca.h, line 25): cannot find include file "stddef.h"
	not in ./stddef.h
	not in ../../../include/stddef.h
	not in ../../../include/GL/internal/stddef.h
	not in ../../../src/mesa/stddef.h
	not in ../../../src/mesa/glapi/stddef.h
	not in /usr/include/drm/stddef.h
	not in /usr/X11R6/include/stddef.h
	not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/X11/Xlibint.h, line 347): cannot find include file "stddef.h"
	not in ./stddef.h
	not in ../../../include/stddef.h
	not in ../../../include/GL/internal/stddef.h
	not in ../../../src/mesa/stddef.h
	not in ../../../src/mesa/glapi/stddef.h
	not in /usr/include/drm/stddef.h
	not in /usr/X11R6/include/stddef.h
	not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/stdio.h, line 34): cannot find include file "stddef.h"
	not in ./stddef.h
	not in ../../../include/stddef.h
	not in ../../../include/GL/internal/stddef.h
	not in ../../../src/mesa/stddef.h
	not in ../../../src/mesa/glapi/stddef.h
	not in /usr/include/drm/stddef.h
	not in /usr/X11R6/include/stddef.h
	not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/_G_config.h, line 15): cannot find include file "stddef.h"
	not in ./stddef.h
	not in ../../../include/stddef.h
	not in ../../../include/GL/internal/stddef.h
	not in ../../../src/mesa/stddef.h
	not in ../../../src/mesa/glapi/stddef.h
	not in /usr/include/drm/stddef.h
	not in /usr/X11R6/include/stddef.h
	not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/wchar.h, line 52): cannot find include file "stddef.h"
	not in ./stddef.h
	not in ../../../include/stddef.h
	not in ../../../include/GL/internal/stddef.h
	not in ../../../src/mesa/stddef.h
	not in ../../../src/mesa/glapi/stddef.h
	not in /usr/include/drm/stddef.h
	not in /usr/X11R6/include/stddef.h
	not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/libio.h, line 53): cannot find include file "stdarg.h"
	not in ./stdarg.h
	not in ../../../include/stdarg.h
	not in ../../../include/GL/internal/stdarg.h
	not in ../../../src/mesa/stdarg.h
	not in ../../../src/mesa/glapi/stdarg.h
	not in /usr/include/drm/stdarg.h
	not in /usr/X11R6/include/stdarg.h
	not in /usr/include/stdarg.h
makedepend: warning:  clientattrib.c (reading glxclient.h, line 53): cannot find include file "GL/glxint.h"
	not in GL/glxint.h
	not in GL/glxint.h
	not in ./GL/glxint.h
	not in ../../../include/GL/glxint.h
	not in ../../../include/GL/internal/GL/glxint.h
	not in ../../../src/mesa/GL/glxint.h
	not in ../../../src/mesa/glapi/GL/glxint.h
	not in /usr/include/drm/GL/glxint.h
	not in /usr/X11R6/include/GL/glxint.h
	not in /usr/include/GL/glxint.h
makedepend: warning:  clientattrib.c (reading glxclient.h, line 54): cannot find include file "GL/glxproto.h"
	not in GL/glxproto.h
	not in GL/glxproto.h
	not in ./GL/glxproto.h
	not in ../../../include/GL/glxproto.h
	not in ../../../include/GL/internal/GL/glxproto.h
	not in ../../../src/mesa/GL/glxproto.h
	not in ../../../src/mesa/glapi/GL/glxproto.h
	not in /usr/include/drm/GL/glxproto.h
	not in /usr/X11R6/include/GL/glxproto.h
	not in /usr/include/GL/glxproto.h
makedepend: warning:  indirect.c, line 36: cannot find include file "GL/glxproto.h"
	not in ./GL/glxproto.h
	not in ../../../include/GL/glxproto.h
	not in ../../../include/GL/internal/GL/glxproto.h
	not in ../../../src/mesa/GL/glxproto.h
	not in ../../../src/mesa/glapi/GL/glxproto.h
	not in /usr/include/drm/GL/glxproto.h
	not in /usr/X11R6/include/GL/glxproto.h
	not in /usr/include/GL/glxproto.h
makedepend: warning:  indirect_vertex_array.c, line 32: cannot find include file "GL/glxproto.h"
	not in ./GL/glxproto.h
	not in ../../../include/GL/glxproto.h
	not in ../../../include/GL/internal/GL/glxproto.h
	not in ../../../src/mesa/GL/glxproto.h
	not in ../../../src/mesa/glapi/GL/glxproto.h
	not in /usr/include/drm/GL/glxproto.h
	not in /usr/X11R6/include/GL/glxproto.h
	not in /usr/include/GL/glxproto.h
makedepend: warning:  indirect_vertex_array.c (reading indirect_vertex_array_priv.h, line 39): cannot find include file "GL/glxproto.h"
	not in ./GL/glxproto.h
	not in ../../../include/GL/glxproto.h
	not in ../../../include/GL/internal/GL/glxproto.h
	not in ../../../src/mesa/GL/glxproto.h
	not in ../../../src/mesa/glapi/GL/glxproto.h
	not in /usr/include/drm/GL/glxproto.h
	not in /usr/X11R6/include/GL/glxproto.h
	not in /usr/include/GL/glxproto.h
makedepend: warning:  indirect_vertex_program.c, line 31: cannot find include file "GL/glxproto.h"
	not in ./GL/glxproto.h
	not in ../../../include/GL/glxproto.h
	not in ../../../include/GL/internal/GL/glxproto.h
	not in ../../../src/mesa/GL/glxproto.h
	not in ../../../src/mesa/glapi/GL/glxproto.h
	not in /usr/include/drm/GL/glxproto.h
	not in /usr/X11R6/include/GL/glxproto.h
	not in /usr/include/GL/glxproto.h
makedepend: warning:  singlepix.c, line 37: cannot find include file "GL/glxproto.h"
	not in ./GL/glxproto.h
	not in ../../../include/GL/glxproto.h
	not in ../../../include/GL/internal/GL/glxproto.h
	not in ../../../src/mesa/GL/glxproto.h
	not in ../../../src/mesa/glapi/GL/glxproto.h
	not in /usr/include/drm/GL/glxproto.h
	not in /usr/X11R6/include/GL/glxproto.h
	not in /usr/include/GL/glxproto.h
makedepend: warning:  dri2.c (reading /usr/include/xf86drm.h, line 37): cannot find include file "stdarg.h"
	not in ./stdarg.h
	not in ../../../include/stdarg.h
	not in ../../../include/GL/internal/stdarg.h
	not in ../../../src/mesa/stdarg.h
	not in ../../../src/mesa/glapi/stdarg.h
	not in /usr/include/drm/stdarg.h
	not in /usr/X11R6/include/stdarg.h
	not in /usr/include/stdarg.h
makedepend: warning:  dri2.c (reading /usr/include/drm/drm.h), line 172: # warning "__SIZE_TYPE__ not defined.  Assuming sizeof(size_t) == sizeof(unsigned long)!"
makedepend: warning:  dri2.c (reading dri2.h, line 37): cannot find include file "X11/extensions/dri2tokens.h"
	not in ./X11/extensions/dri2tokens.h
	not in ../../../include/X11/extensions/dri2tokens.h
	not in ../../../include/GL/internal/X11/extensions/dri2tokens.h
	not in ../../../src/mesa/X11/extensions/dri2tokens.h
	not in ../../../src/mesa/glapi/X11/extensions/dri2tokens.h
	not in /usr/include/drm/X11/extensions/dri2tokens.h
	not in /usr/X11R6/include/X11/extensions/dri2tokens.h
	not in /usr/include/X11/extensions/dri2tokens.h
makedepend: warning:  ../../../src/mesa/main/dispatch.c (reading /usr/include/limits.h, line 125): cannot find include file "limits.h"
makedepend: warning:  ../../../src/mesa/main/dispatch.c (reading ../../../src/mesa/main/glheader.h, line 63): cannot find include file "float.h"
	not in ./float.h
	not in ../../../include/float.h
	not in ../../../include/GL/internal/float.h
	not in ../../../src/mesa/float.h
	not in ../../../src/mesa/glapi/float.h
	not in /usr/include/drm/float.h
	not in /usr/X11R6/include/float.h
	not in /usr/include/float.h
makedepend: warning:  ../../../src/mesa/main/dispatch.c (reading ../../../src/mesa/main/glheader.h, line 64): cannot find include file "stdarg.h"
	not in ./stdarg.h
	not in ../../../include/stdarg.h
	not in ../../../include/GL/internal/stdarg.h
	not in ../../../src/mesa/stdarg.h
	not in ../../../src/mesa/glapi/stdarg.h
	not in /usr/include/drm/stdarg.h
	not in /usr/X11R6/include/stdarg.h
	not in /usr/include/stdarg.h
make[3]: Leaving directory `/home/patrick/Desktop/Mesa-7.4/src/glx/x11'
make[3]: Entering directory `/home/patrick/Desktop/Mesa-7.4/src/glx/x11'
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" glcontextmodes.c -o glcontextmodes.o
glcontextmodes.c:42:23: error: GL/glxint.h: No such file or directory
In file included from glcontextmodes.c:67:
glcontextmodes.h:39: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;__GLXvisualConfig&#8217;
glcontextmodes.h:39: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;*&#8217; token
glcontextmodes.c:132: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;__GLXvisualConfig&#8217;
glcontextmodes.c:132: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;*&#8217; token
make[3]: *** [glcontextmodes.o] Error 1
make[3]: Leaving directory `/home/patrick/Desktop/Mesa-7.4/src/glx/x11'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/patrick/Desktop/Mesa-7.4/src'
make[1]: *** [default] Error 1
make[1]: Leaving directory `/home/patrick/Desktop/Mesa-7.4'
make: *** [linux-dri] Error 2

```

Am I missing any steps?

---

### Post by stumbleUpon on 2009-04-13
Mesa is available in the ubuntu repos. Why try to compile and then install it?
Open synaptic or aptittude and install it. If you want to write your own applications, install the corresoponding development files in addition to the library files.

---

### Post by WalmartSniperLX on 2009-04-13
I want to install Mesa 7.4 and corresponding updated opensource drivers. All I can find in the ubuntu repos are based on build 7.2.

```
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.2

```

---

### Post by WalmartSniperLX on 2009-04-13
Running the configure script gives me this output. Looking at it, Im guessing im missing a dependency. Maybe this is the root of my problem on original post? 

```

patrick@patrick-laptop:~/Desktop/Mesa-7.4$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gmake... no
checking for make... make
checking for makedepend... /usr/bin/makedepend
checking for sed... /bin/sed
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether to enable assembly... yes, x86
checking for gcc option to produce PIC... -fPIC
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for posix_memalign... yes
checking pkg-config files for X11 are available... yes
checking for LIBDRM... configure: error: Package requirements (libdrm >= 2.4.3) were not met:

Requested 'libdrm >= 2.4.3' but version of libdrm is 2.3.1

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBDRM_CFLAGS
and LIBDRM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Edit: I have downloaded and extracted libdrm 2.4.7 onto the desktop. Is there a way to point to the directory?

---

### Post by ssam on 2009-04-13
you probably need to install the new libdrm.

there are some instructions at the bottom of [http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon) that look like ubuntu/debian style.

---

### Post by nagual2 on 2012-02-04
[http://joostlek.nl/vmware-linux-guest-with-3d-accelerated-graphics#comment-10](http://joostlek.nl/vmware-linux-guest-with-3d-accelerated-graphics#comment-10)

 # dpkg -l |grep libdrm
ii  libdrm-dev                             2.4.26-1ubuntu1                         Userspace interface to kernel DRM services -- development files
ii  libdrm-intel1                          2.4.26-1ubuntu1                         Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau1a                       2.4.26-1ubuntu1                         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1                         2.4.26-1ubuntu1                         Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm2                                2.4.26-1ubuntu1                         Userspace interface to kernel DRM services -- runtime

problems from mesa ...

---

### Post by Yellow Pasque on 2012-02-06
> **nagual2 said:**
> [http://joostlek.nl/vmware-linux-guest-with-3d-accelerated-graphics#comment-10](http://joostlek.nl/vmware-linux-guest-with-3d-accelerated-graphics#comment-10)

 # dpkg -l |grep libdrm
ii  libdrm-dev                             2.4.26-1ubuntu1                         Userspace interface to kernel DRM services -- development files
ii  libdrm-intel1                          2.4.26-1ubuntu1                         Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau1a                       2.4.26-1ubuntu1                         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1                         2.4.26-1ubuntu1                         Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm2                                2.4.26-1ubuntu1                         Userspace interface to kernel DRM services -- runtime

problems from mesa ...
It is not clear what your issue is or how it relates to this thread. If you need a newer version of mesa, use the xorg-edgers ppa: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

