---
title: "unable to compile MESA on ubuntu 10.04"
date: 2010-08-26
forum: Packaging and Compiling Programs
---

### Post by k210in on 2010-08-26
Hi,

     Am trying to compile MESA 7.8.2 on ubuntu 10.04. i am using the steps mentioned at [http://www.mesa3d.org/install.html](http://www.mesa3d.org/install.html)

Every time i do "make linux-x86" i see a different error log... Below is the description of the errors. Can someone point out what i am missing here? 

Thx
K

When i do "make linux-86" the first time, this is what i get:

[COLOR=Red]~/work/Mesa-7.8.2$ make linux-x86 
make default
make[1]: Entering directory `/home/lalitha/work/Mesa-7.8.2'
make[2]: Entering directory `/home/lalitha/work/Mesa-7.8.2/src'
Making sources for linux-x86
make[3]: Entering directory `/home/lalitha/work/Mesa-7.8.2/src/glsl'
make[4]: Entering directory `/home/lalitha/work/Mesa-7.8.2/src/glsl/pp'
rm -f depend
touch depend
makedepend -fdepend -I.  sl_pp_context.c sl_pp_define.c sl_pp_dict.c sl_pp_error.c sl_pp_expression.c sl_pp_extension.c sl_pp_if.c sl_pp_line.c sl_pp_macro.c sl_pp_pragma.c sl_pp_process.c sl_pp_purify.c sl_pp_token.c sl_pp_token_util.c sl_pp_version.c 2> /dev/null
make[4]: *** No rule to make target `depend', needed by `default'.  Stop.
make[4]: Leaving directory `/home/lalitha/work/Mesa-7.8.2/src/glsl/pp'
make[3]: *** [default] Error 1
make[3]: Leaving directory `/home/lalitha/work/Mesa-7.8.2/src/glsl'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/lalitha/work/Mesa-7.8.2/src'
make[1]: *** [default] Error 1
make[1]: Leaving directory `/home/lalitha/work/Mesa-7.8.2'
make: *** [linux-x86] Error 2
[/COLOR]
i try the same command the second time and this is what i get:

[COLOR=Red]gcc -c -I.  -Wall -Wmissing-prototypes -Wdeclaration-after-statement -Wpointer-arith -O3 -g -fPIC -m32 -mmmx -msse -m
sse2 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_XSHM -DHAV
E_POSIX_MEMALIGN -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM -I/usr/X11R6/include -std=c99 -ffast-math 
-fno-strict-aliasing  sl_pp_version.c -o sl_pp_version.o
/bin/sh ../../../bin/mklib -o glslpp -static sl_pp_context.o sl_pp_define.o sl_pp_dict.o sl_pp_error.o sl_pp_expressi
on.o sl_pp_extension.o sl_pp_if.o sl_pp_line.o sl_pp_macro.o sl_pp_pragma.o sl_pp_process.o sl_pp_purify.o sl_pp_toke
n.o sl_pp_token_util.o sl_pp_version.o
mklib: Making Linux static library:  libglslpp.a
ar: creating libglslpp.a
make[4]: Leaving directory `/home/lalitha/work/Mesa-7.8.2/src/glsl/pp'
make[4]: Entering directory `/home/lalitha/work/Mesa-7.8.2/src/glsl/cl'
rm -f depend
touch depend
makedepend -fdepend -I.  sl_cl_parse.c 2> /dev/null
make[4]: *** No rule to make target `depend', needed by `default'.  Stop.
make[4]: Leaving directory `/home/lalitha/work/Mesa-7.8.2/src/glsl/cl'
make[3]: *** [default] Error 1
make[3]: Leaving directory `/home/lalitha/work/Mesa-7.8.2/src/glsl'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/lalitha/work/Mesa-7.8.2/src'
make[1]: *** [default] Error 1
make[1]: Leaving directory `/home/lalitha/work/Mesa-7.8.2'
make: *** [linux-x86] Error 2

[/COLOR]Dont know whats going on. Help.

---

### Post by k210in on 2010-08-26
And when i do ./configure, this is what i see:

(error in [COLOR=Red]red[/COLOR] below)

~/work/Mesa-7.8.2$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
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
checking for a BSD-compatible install... /usr/bin/install -c
checking whether gcc version is sufficient... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether gcc supports -fvisibility=hidden... yes
checking whether to enable assembly... yes, x86
checking for gcc option to produce PIC... -fPIC
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for posix_memalign... yes
[COLOR=Red]checking pkg-config files for X11 are available... no
checking for X... no
configure: error: X11 development libraries needed for dri driver
[/COLOR]

Thx
K

---

### Post by k210in on 2010-08-26
And BTW, i am trying to build a stand-alone MESA as mentioned at [http://www.mesa3d.org/install.html](http://www.mesa3d.org/install.html).

i.e.
**1.3 Building with traditional Makefiles**

   The traditional Mesa build system is based on a  collection of pre-defined system configurations. 
  To see the list of configurations, just type make. Then choose a configuration from the list and type make *configname*. 
   Mesa may be built in several different ways using  the predefined configurations: 
 
[LIST]
[*]***Stand-alone/Xlib mode*** - Mesa  will be compiled as a software renderer using Xlib to do all rendering. The libGL.so library will be a self-contained rendering library that  will allow you to run OpenGL/GLX applications on any X server (regardless of whether it supports the GLX X server extension). You will *not* be able to use hardware 3D acceleration.  To compile stand-alone Mesa type make  in the top-level directory. You'll see a list of supported system configurations. Choose one from the list (such as linux-x86), and type: 
     make linux-x86
 This will produce libGL.so and several other  libraries
[/LIST]


Thx
K

---

### Post by k210in on 2010-08-26
alright. Got it working... 

The command "sudo apt-get install xorg-dev"  helped.

Thanks anyways.

Thx
K

---

