---
title: "pkg-config-0.28 configure error"
date: 2014-01-30
forum: New to Ubuntu
---

### Post by hunkmilkman on 2014-01-30
Hi!

SOLUTION:
```
sudo apt-get install pkg-config
```
It chose 0.26 but it seemed to work since it didn't give an error message and the last line said SETTING UP


---



I just switched from Windows so please don't overlook steps that most users take for granted. I know how to open terminal though.
So I did downloaded and extracted pkg-config-0.28




then I
~ cd source/pkg-config-0.28
~ ./configure

And a lot of text ended with 

checking whether to list both direct and indirect dependencies... no
checking for Win32... no
checking if internal glib should be used... no
checking for pkg-config... no
checking for GLIB... no
configure: error: Either a previously installed pkg-config or "glib-2.0 >= 2.16" could not be found. Please set GLIB_CFLAGS and GLIB_LIBS to the correct values or pass --with-internal-glib to configure to use the bundled copy.


All of it:

```
adsi@adsi:~$ source/pkg-config-0.28
bash: source/pkg-config-0.28: Is a directory
adsi@adsi:~$ cd source/pkg-config-0.28
adsi@adsi:~/source/pkg-config-0.28$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
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
checking whether to build static libraries... yes
checking whether make supports nested variables... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ln... ln
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking for unistd.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for bash... /bin/bash
checking for default search path for .pc files... ${libdir}/pkgconfig:${datadir}/pkgconfig:/usr/lib/pkgconfig:/usr/share/pkgconfig
checking for system include path to avoid -I flags... /usr/include
checking for system library path to avoid -L flags... /usr/lib:/lib
configure: creating ./config.lt
config.lt: creating libtool
checking whether to list both direct and indirect dependencies... no
checking for Win32... no
checking if internal glib should be used... no
checking for pkg-config... no
checking for GLIB... no
configure: error: Either a previously installed pkg-config or "glib-2.0 >= 2.16" could not be found. Please set GLIB_CFLAGS and GLIB_LIBS to the correct values or pass --with-internal-glib to configure to use the bundled copy.
```

I am using Lubuntu 13.10.

---

