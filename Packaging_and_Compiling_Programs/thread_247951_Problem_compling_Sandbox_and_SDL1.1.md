---
title: "Problem compling Sandbox and SDL1.1"
date: 2006-08-31
forum: Packaging and Compiling Programs
---

### Post by recon69 on 2006-08-31
I am trying to compile the Artificial Terrain Generation app from 

[http://sponeil.org/downloads.htm](http://sponeil.org/downloads.htm)

and i hit a problem with SDL lib.
Seem that it want to link libSDL1.1 instead of libSDL1.2 
but not sure, here is the output from the ./configure and make 

```

> ./configure ./configure CPPFLAGS="-I/usr/include/SDL/ -I/usr/local/include -I/usr/X11R6/include -I/usr/local/include/SDL11 -I/home/mec/development/models/SPO_Sandbox-0.1/src/GLs/ -I./usr/include/SDL/SDL_syswm.h" LDFLAGS="-L/usr/local/lib -L/usr/X11R6/lib"


checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for ./configure-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ./configure-g++... no
checking for ./configure-c++... no
checking for ./configure-gpp... no
checking for ./configure-aCC... no
checking for ./configure-CC... no
checking for ./configure-cxx... no
checking for ./configure-cc++... no
checking for ./configure-cl... no
checking for ./configure-FCC... no
checking for ./configure-KCC... no
checking for ./configure-RCC... no
checking for ./configure-xlC_r... no
checking for ./configure-xlC... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ./configure-ranlib... no
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking GL/glew.h usability... yes
checking GL/glew.h presence... yes
checking for GL/glew.h... yes
checking SDL.h usability... yes
checking SDL.h presence... yes
checking for SDL.h... yes
checking for pthread_create in -lpthread... yes
checking for glBegin in -lGL... yes
checking for glewInit in -lGLEW... yes
checking for SDL_InitSubSystem in -lSDL-1.1... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/EngineCore/Makefile
config.status: creating src/TestApp/Makefile
config.status: creating src/GLCloud1/Makefile
config.status: creating src/GLCloud2/Makefile
config.status: creating src/GLCloud3/Makefile
config.status: creating src/ScatterCPU/Makefile
config.status: creating src/ScatterGPU/Makefile
config.status: creating src/Planet_Quad/Makefile
config.status: creating src/bin/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

> make
....
...
..
make[3]: Entering directory `/home/mec/development/models/SPO_Sandbox-0.1/src/EngineCore'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mec/development/models/SPO_Sandbox-0.1/src/EngineCore'
Making all in TestApp
make[3]: Entering directory `/home/mec/development/models/SPO_Sandbox-0.1/src/TestApp'
g++  -g -O2  -L/usr/local/lib -L/usr/X11R6/lib -o TestApp  TestApp.o -lpthread -lpng -lGL -lGLEW -lSDL-1.1 ../../src/EngineCore/libEngineCore.a -lGLEW -lGL -lpthread
/usr/bin/ld: cannot find -lSDL-1.1
collect2: ld returned 1 exit status
make[3]: *** [TestApp] Error 1



```


Anyone have any ideas, I'm at a bit of a loss as SDL1.2 is installed but it seems to want SDL1.1?

Regards

---

### Post by recon69 on 2006-08-31
OK, got it to work.

In the configure file it was trying to link -lSDL-1.1 
after doing 

mec@mec-desktop:/$ ldconfig -v | grep SDL
ldconfig: Can't open configuration file /etc/ld.so.conf: No such file or directory
        libSDL_console.so.1 -> libSDL_console.so.1.3
        libSDL_image-1.2.so.0 -> libSDL_image.so
        libSDL_gfx.so.4 -> libSDL_gfx.so.4.9.0
        libSDL_mixer-1.2.so.0 -> libSDL_mixer.so
        libSDL-1.2.so.0 -> libSDL.so

I could see that the lib should be called -lSDL

so i went into the configure and makefile's and changed it. 
everything working now :)

---

