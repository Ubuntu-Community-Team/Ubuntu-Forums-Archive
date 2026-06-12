---
title: "SDL 1.3 compile problem"
date: 2011-02-09
forum: Programming Talk
---

### Post by dosh on 2011-02-09
I have set SDL 1.3 up on my computer in the folder sdl within my home folder and having problems compiling testGl.c which I copied over to my home folder. gcc is having problems finding the correct folder and I am after the correct gcc arguments to get this compiled. Not sure if I need to put the GL and SDL after the folder locations or what?

---

### Post by slooksterpsv on 2011-02-09
To point it to includes you do:

gcc -I/path/to/includes

To point it to libraries you do:

gcc -L/path/to/libraries

Try that, it uses what you specify in -I or -L first before continuing with the other "search paths"

---

### Post by dosh on 2011-02-09
With gcc testgl.c -o testgl -I/home/joe/sdl/include -L/home/joe/sdl/lib -L/home/joe/sdl/include/sdl/GL

I get it to compile but when I try to run it I get
"No OpenGL support on this system"

However I thought sdl 1.3 came with it plus I have OpenGl installed and have compiled programs with SDL 1.2 and OpenGL.

---

### Post by fct on 2011-02-09
The SDL libraries normally build also an utility, sdl-config, that provides the necessary flags for compilation. Sample usage:

$ gcc `sdl-config --libs --cflags` -o something something.cpp

Now, I don't know what's the path where it's built by default.

---

### Post by dosh on 2011-02-09
I think the problem is in the paths it is looking at. I have extracted and installed it into a sdl folder inside my home folder. that is /home/joe/sdl . The folder for OpenGl files I presume is the one it is having problems with. For SDL 1.2 which is in the default area no problems I would put (if file was test.c)
"gcc test.c -o test -lSDL -lGL"

and it would compile. Yet having problems when I have SDL 1.3 as well in another folder not the default one.

---

### Post by Zugzwang on 2011-02-10
@OP: Could you copy&paste the output when running the configure-script of the SDL library before you compile it?

---

### Post by fct on 2011-02-10
Using sdl-config is worth a try. Really.

---

### Post by dosh on 2011-02-10
fct I have tryed the sdl-config with the same result. I it is just not recognising the openGL directory. The sdl seems OK I was able to run a program that shows the version and it came back as 1.3 The problem seems to be the openGL directory. Do I need to set the library directory for that? And how?

Zugzwang not understanding what you mean. Do you want a copy of the sdl-config file?

---

### Post by Zugzwang on 2011-02-11
> **dosh said:**
> Zugzwang not understanding what you mean. Do you want a copy of the sdl-config file?

You said that you have set up SDL 1.3 on your computer. Since version 1.3 is not part of Ubuntu, this means that you have extracted the SDL .tar.gz file of the libsdl into some directory and ran "./configure" to build it (because that's a required part of the installation process unless you install it as a Ubuntu package). When doing so, the "./configure" script generates a lot of messages. Please copy&paste them here.

---

### Post by dosh on 2011-02-11
Zugzwang does it create a file or you talking about the messeages received in the terminal when I ran ./config , if they don't make a file they are gone and I would need to rebuild to get them.

---

### Post by Zugzwang on 2011-02-11
> **dosh said:**
> Zugzwang does it create a file or you talking about the messeages received in the terminal when I ran ./config , if they don't make a file they are gone and I would need to rebuild to get them.

I don't know if they are stored in a file. I would propose that you just rerun "./configure" and just copy&paste what you get an output here. Rebuilding is however probably not needed. Please also tell us which options you pass to the configure script.

---

### Post by dosh on 2011-02-12
here it is Zugzwang

$ ./configure --prefix=/home/joe/sdl
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking for windres... no
checking for linux-gnu-windres... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for working volatile... yes
checking for GCC -MMD -MT option... yes
checking for ANSI C header files... (cached) yes
checking for sys/types.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for stdlib.h... (cached) yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking iconv.h usability... yes
checking iconv.h presence... yes
checking for iconv.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for size_t... yes
checking for int64_t... yes
checking for M_PI in math.h... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for working memcmp... yes
checking for working strtod... yes
checking for mprotect... yes
checking for malloc... yes
checking for calloc... yes
checking for realloc... yes
checking for free... yes
checking for getenv... yes
checking for setenv... yes
checking for putenv... yes
checking for unsetenv... yes
checking for qsort... yes
checking for abs... yes
checking for bcopy... yes
checking for memset... yes
checking for memcpy... yes
checking for memmove... yes
checking for strlen... yes
checking for strlcpy... no
checking for strlcat... no
checking for strdup... yes
checking for _strrev... no
checking for _strupr... no
checking for _strlwr... no
checking for strchr... yes
checking for strrchr... yes
checking for strstr... yes
checking for itoa... no
checking for _ltoa... no
checking for _uitoa... no
checking for _ultoa... no
checking for strtol... yes
checking for strtoul... yes
checking for _i64toa... no
checking for _ui64toa... no
checking for strtoll... yes
checking for strtoull... yes
checking for atoi... yes
checking for atof... yes
checking for strcmp... yes
checking for strncmp... yes
checking for _stricmp... no
checking for strcasecmp... yes
checking for _strnicmp... no
checking for strncasecmp... yes
checking for sscanf... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for sigaction... yes
checking for setjmp... yes
checking for nanosleep... yes
checking for sysconf... yes
checking for sysctlbyname... no
checking for pow in -lm... yes
checking for atan... yes
checking for atan2... yes
checking for ceil... yes
checking for copysign... yes
checking for cos... yes
checking for cosf... yes
checking for fabs... yes
checking for floor... yes
checking for log... yes
checking for pow... yes
checking for scalbn... yes
checking for sin... yes
checking for sinf... yes
checking for sqrt... yes
checking for iconv_open in -liconv... no
checking for iconv... yes
checking for void*... yes
checking size of void*... 4
checking for GCC builtin atomic operations... yes
checking for GCC -mmmx option... yes
checking for GCC -m3dnow option... yes
checking for GCC -msse option... yes
checking for Altivec with GCC altivec.h and -maltivec option... no
checking for Altivec with GCC -maltivec option... no
checking for Altivec with GCC altivec.h and -faltivec option... no
checking for Altivec with GCC -faltivec option... no
checking for GCC -fvisibility=hidden option... yes
checking for dlopen... yes
checking for dlopen in -lc... no
checking for dlopen in -ldl... yes
checking for OSS audio support... yes
checking for dmedia audio support... no
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 0.9.0... found.
checking for snd_ctl_open in -lasound... yes
-- dynamic libasound -> libasound.so.2
checking for pkg-config... /usr/bin/pkg-config
checking for PulseAudio 0.9 support... yes
-- dynamic libpulse-simple -> libpulse-simple.so.0
checking for artsc-config... no
checking for esd-config... /usr/bin/esd-config
checking for ESD - version >= 0.2.8... yes
-- dynamic libesd -> libesd.so.0
checking audio/audiolib.h usability... yes
checking audio/audiolib.h presence... yes
checking for audio/audiolib.h... yes
checking for AuOpenServer in -laudio... yes
checking for NAS audio support... yes
-- dynamic libaudio -> libaudio.so.2
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
-- dynamic libX11 -> libX11.so.6
-- dynamic libX11ext -> libXext.so.6
checking for X11/extensions/shape.h... yes
checking for X11/extensions/Xrandr.h... yes
-- dynamic libXrandr -> libXrandr.so.2
checking for X11/extensions/XInput.h... yes
-- dynamic libXi -> libXi.so.6
checking for X11/extensions/scrnsaver.h... no
checking for OpenGL (GLX) support... yes
checking for Linux 2.4 unified input interface... yes
checking for Touchscreen library support... no
checking for hid_init in -lusbhid... no
checking usb.h usability... no
checking usb.h presence... no
checking for usb.h... no
checking libusb.h usability... no
checking libusb.h presence... no
checking for libusb.h... no
checking for hid_init in -lusb... no
checking for usbhid... no
checking for pthreads... yes
checking for recursive mutexes... yes
checking for pthread semaphores... yes
checking linux/version.h usability... yes
checking linux/version.h presence... yes
checking for linux/version.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating sdl-config
config.status: creating SDL.spec
config.status: creating sdl.pc
config.status: creating include/SDL_config.h
config.status: include/SDL_config.h is unchanged
config.status: executing libtool commands
config.status: executing default commands

---

### Post by Zugzwang on 2011-02-13
> **dosh said:**
> here it is Zugzwang


Hmm, looks OK. I was hoping that for some reason, OpenGL support was not included in your compilation, but apparently it is. 

Perhaps it is of help for you to see a full working compilation process using SDL-1.3. Try to repeat it and see if you still have problems.

First, I downloaded SDL 1.3 from [here]("http://www.libsdl.org/hg.php") and extracted it to "/tmp/" (I'm only testing this for you, so no need to keep the files).

Then, I ran "./configure --prefix=/tmp/sdlinstall" from the newly made SDL-1.3.0-5285 directory, followed my "make" and "make install" (no SUDO necessary here since I'm just working in /tmp/).

Then, I extracted some example source code (openGL-Intro-1.1 from [http://www.libsdl.org/opengl/index.php](http://www.libsdl.org/opengl/index.php)) to /tmp/ again.

From the newly made directory, I tried to compile one example using the command line "gcc -o something -I /tmp/sdlinstall/include/SDL -L /tmp/sdlinstall/lib -lSDL -lGLU -lGL lesson02.c"

Then, I tried to run the generated "something" executable. That didn't work due to the error message "./something: error while loading shared libraries: libSDL-1.3.so.0: cannot open shared object file: No such file or directory".

So we need to tell the runtime linker where to find that file. So I tried starting the program with some environment variable telling where to find additional library files. "LD_LIBRARY_PATH=/tmp/sdlinstall/lib;./something"

Now it worked. I get a window with a square and a triangle. Can you try the same steps and see where this process first breaks down?

---

### Post by dosh on 2011-02-14
Zugzwang one thing with the . "LD_LIBRARY_PATH=/tmp/sdlinstall/lib;./something"
you have written as the something file is the final executable file created by the compiler the line above does not make sense as the Library path can not point to something that has not been created as yet, so I presume that ./something is for something else? lesson02.c? the directory lesson02 is in?

---

### Post by dosh on 2011-02-15
I decided to do exactly what you did tmp folder etc. 
this is the results at different places.
1st I got $ LD_LIBRARY_PATH=/tmp/sdlinstall/lib;./something
bash: ./something: No such file or directory

so tried just $ LD_LIBRARY_PATH=/tmp/sdlinstall/lib;
$ '/tmp/something' 
/tmp/something: error while loading shared libraries: libSDL-1.3.so.0: cannot open shared object file: No such file or directory

and again 
$ LD_LIBRARY_PATH=/tmp/sdlinstall/lib;./something
./something: error while loading shared libraries: libSDL-1.3.so.0: cannot open shared object file: No such file or directory

---

### Post by Zugzwang on 2011-02-15
> **dosh said:**
> I decided to do exactly what you did tmp folder etc. 
this is the results at different places.
1st I got $ LD_LIBRARY_PATH=/tmp/sdlinstall/lib;./something
bash: ./something: No such file or directory


Note that in the example command list, I ran the command "gcc -o something -I /tmp/sdlinstall/include/SDL -L /tmp/sdlinstall/lib -lSDL -lGLU -lGL lesson02.c" from the directory in which the tutorial C code resides. This creates the executable "something", which I've just used as an example name. The directory "/tmp/sdlinstall" must have been created by the "make install" command executed from the directory into I've extracted the SDL-1.3 sources.

Then, the command "LD_LIBRARY_PATH=/tmp/sdlinstall/lib;./something" should work if executed from the path in which the example source codes are.

---

### Post by pbrane on 2011-02-15
Did you run **./autogen.sh** before you ran ./configure? You need to do that first. It looks like the only way to get SDL 1.3 is with Mercurial (hg). It's the development version.

---

### Post by dosh on 2011-02-15
Thanks pbrain I think I missed that step when installing it in the temp folder. And thanks again Zugzwang I'll give it another go.

---

### Post by dosh on 2011-02-16
Same problem.

/tmp$ '/tmp/something' 
/tmp/something: error while loading shared libraries: libSDL-1.3.so.0: cannot open shared object file: No such file or directory
philip@philip-laptop:/tmp$ LD_LIBRARY_PATH=/tmp/sdlinstall/lib;./something
./something: error while loading shared libraries: libSDL-1.3.so.0: cannot open shared object file: No such file or directory

---

### Post by Zugzwang on 2011-02-16
> **dosh said:**
> Same problem.


It seems as if you are somewhat mixing up the paths. The fact that you try to execute "/tmp/something" tells me that. I'll copy&paste a *complete* example below:
```

me@my-computer:/tmp$ wget http://www.libsdl.org/tmp/SDL-1.3.tar.gz
[...]
me@my-computer:/tmp$ tar xzf SDL-1.3.tar.gz 
me@my-computer:/tmp$ cd SDL-1.3.0-5313/
me@my-computer:/tmp/SDL-1.3.0-5313$ ./configure --prefix=/tmp/sdlinstall
[...]
me@my-computer:/tmp/SDL-1.3.0-5313$ make
[...]
me@my-computer:/tmp/SDL-1.3.0-5313$ make install
[...]
me@my-computer:/tmp/SDL-1.3.0-5313$ cd ..
me@my-computer:/tmp$ wget http://www.libsdl.org/opengl/OpenGL-intro-1.1.1.zip
[...]
me@my-computer:/tmp$ unzip OpenGL-intro-1.1.1.zip 
[...]
me@my-computer:/tmp$ cd OpenGL-intro-1.1.1/
me@my-computer:/tmp/OpenGL-intro-1.1.1$ gcc -o something -I /tmp/sdlinstall/include/SDL -L /tmp/sdlinstall/lib -lSDL -lGLU -lGL lesson02.c
me@my-computer:/tmp/OpenGL-intro-1.1.1$ ./something 
./something: error while loading shared libraries: libSDL-1.3.so.0: cannot open shared object file: No such file or directory
me@my-computer:/tmp/OpenGL-intro-1.1.1$ LD_LIBRARY_PATH=/tmp/sdlinstall/lib;./something

```

After the last step the window should pop up. Check that you always in the correct directories when trying to compile and/or execute.  The "..." above represent lines of output that I skipped. For the SDL-1.3 distribution zip-file that I've chosen for this example, unlike pbrane wrote, running autogen.sh is not necessary, the configure script is already in place.

If it still does not work, verify that in the directory "/tmp/sdlinstall/lib", the file "libSDL-1.3.so.0" actually exists. If not, check if running "make" in the SDL-1.3 directory resulted in an error in the first place.

---

