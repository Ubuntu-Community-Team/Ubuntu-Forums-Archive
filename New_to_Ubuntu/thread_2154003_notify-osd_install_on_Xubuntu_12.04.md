---
title: "notify-osd install on Xubuntu 12.04"
date: 2013-06-13
forum: New to Ubuntu
---

### Post by robinduncan on 2013-06-13
Hi, I've been trying to install Palaver because I have serious issues with RSI and need something which will transcribe my speech if I am to keep studying. I have followed all the author's instructions, but it's still not functioning properly. I think part of the problem is that I don't have notify-osd, which I believe is not supplied as standard with xubuntu, so I downloaded it. However, when I try to configure it (and I have never done anything like this before...) I get:

robin@robin-Satellite-A50:~/notify-osd-0.9.34$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking whether gcc understands -Wno-sign-compare... yes
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare
checking what language compliance flags to pass to the C compiler... 
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
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
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking whether to build static libraries... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ISO C99... -std=gnu99
checking whether gcc -std=gnu99 and cc understand -c and -o together... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
configure: error: glib-compile-schemas not found.

The next step given in the readme doesn't do anything at all.
As I say, I've never "configured" or installed anything from the terminal before, so I'm really pretty clueless. Can anyone tell me what the problem is?

Thanks a lot,
Robin

---

### Post by slickymaster on 2013-06-13
I think you need the header files. In Ubuntu and other Debian-based operating systems, header files are provided by -dev packages. If you install **libglib2.0-dev** you should be OK.
To install it, run the following command:```
sudo apt-get update && sudo apt-get install libglib2.0-dev
```

If that doesn't manage to fix your problem, there's a tutorial on how to install and configure NotifyOSD, [here]("http://www.webupd8.org/2012/11/patched-notifyosd-with-close-on-click.html").

---

### Post by Cheesemill on 2013-06-13
Why are you trying to compile notify-osd from source when you can just do...
```
sudo apt-get install notify-osd
```

---

