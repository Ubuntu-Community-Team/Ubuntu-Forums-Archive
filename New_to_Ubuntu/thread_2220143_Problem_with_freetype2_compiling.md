---
title: "Problem with freetype2 compiling"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by abel4 on 2014-04-26
Hello, I am trying to compile freetype2 from the source package but when I run ./configure I get this in the command line and no makefile:

```
abel@Lenovo-G560:~/freetype-2.5.2/freetype-2.5.2/builds/unix$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for rmdir... rmdir
checking for a BSD-compatible install... /usr/bin/install -c
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking size of int... 4
checking size of long... 8
checking whether cpp computation of bit length in ftconfig.in works... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether munmap is declared... yes
checking for munmap's first parameter type... void *
checking for memcpy... yes
checking for memmove... yes
checking gcc compiler flag -pedantic to assure ANSI C works correctly... ok, add it to XX_ANSIFLAGS
checking gcc compiler flag -ansi to assure ANSI C works correctly... ok, add it to XX_ANSIFLAGS
checking for gzsetparams in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for BZ2_bzDecompress in -lbz2... no
checking for libpng... -L/usr/lib/x86_64-linux-gnu -lpng12
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking for gawk... gawk
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating ./config.status
config.status: creating unix-cc.mk
config.status: creating unix-def.mk
config.status: creating ftconfig.h
config.status: executing libtool commands
```

I also get a config.log (wich I guess may contain information about the problem).

I'm sorry if I didn't post this in the correct subforum and my bad english. I'm new here and english isn't my first lenguage.

---

