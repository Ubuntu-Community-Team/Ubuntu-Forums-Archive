---
title: "Cross Compilig Issue of udev-151 for MIPS Little Endain Architecture"
date: 2013-01-24
forum: Packaging and Compiling Programs
---

### Post by bsreeram on 2013-01-24
Hi All, 
I am trying to cross compile udev-151 for MIPS little endian architecture. 

I am configuring like this: 

```
./configure --prefix=$PWD/sree --host=mips-linux-gnu 

configure: WARNING: If you wanted to set the --build type, don't use --host. 
If a cross compiler is detected then cross compile mode will be used. 
checking for a BSD-compatible install... /usr/bin/install -c 
checking whether build environment is sane... yes 
checking for mips-linux-gnu-strip... mips-linux-gnu-strip 
checking for a thread-safe mkdir -p... /bin/mkdir -p 
checking for gawk... gawk 
checking whether make sets $(MAKE)... yes 
checking for style of include used by make... GNU 
checking for mips-linux-gnu-gcc... mips-linux-gnu-gcc 
checking for C compiler default output file name... a.out 
checking whether the C compiler works... yes 
checking whether we are cross compiling... yes 
checking for suffix of executables... 
checking for suffix of object files... o 
checking whether we are using the GNU C compiler... yes 
checking whether mips-linux-gnu-gcc accepts -g... yes 
checking for mips-linux-gnu-gcc option to accept ISO C89... none needed 
checking dependency style of mips-linux-gnu-gcc... gcc3 
checking how to run the C preprocessor... mips-linux-gnu-gcc -E 
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
checking minix/config.h usability... no 
checking minix/config.h presence... no 
checking for minix/config.h... no 
checking whether it is safe to define __EXTENSIONS__... yes 
checking for special C compiler options needed for large files... no 
checking for _FILE_OFFSET_BITS value needed for large files... 64 
checking build system type... x86_64-unknown-linux-gnu 
checking host system type... mips-unknown-linux-gnu 
checking for a sed that does not truncate output... /bin/sed 
checking for fgrep... /bin/grep -F 
checking for ld used by mips-linux-gnu-gcc... /home/intel/mips-4.3/mips-linux-gnu/bin/ld 
checking if the linker (/home/intel/mips-4.3/mips-linux-gnu/bin/ld) is GNU ld... yes 
checking for BSD- or MS-compatible name lister (nm)... /home/intel/mips-4.3/bin/mips-linux-gnu-nm -B 
checking the name lister (/home/intel/mips-4.3/bin/mips-linux-gnu-nm -B) interface... BSD nm 
checking whether ln -s works... yes 
checking the maximum length of command line arguments... 1572864 
checking whether the shell understands some XSI constructs... yes 
checking whether the shell understands "+="... yes 
checking for /home/intel/mips-4.3/mips-linux-gnu/bin/ld option to reload object files... -r 
checking for mips-linux-gnu-objdump... mips-linux-gnu-objdump 
checking how to recognize dependent libraries... pass_all 
checking for mips-linux-gnu-ar... mips-linux-gnu-ar 
checking for mips-linux-gnu-strip... (cached) mips-linux-gnu-strip 
checking for mips-linux-gnu-ranlib... mips-linux-gnu-ranlib 
checking command to parse /home/intel/mips-4.3/bin/mips-linux-gnu-nm -B output from mips-linux-gnu-gcc object... ok 
checking for dlfcn.h... yes 
checking for objdir... .libs 
checking if mips-linux-gnu-gcc supports -fno-rtti -fno-exceptions... no 
checking for mips-linux-gnu-gcc option to produce PIC... -fPIC -DPIC 
checking if mips-linux-gnu-gcc PIC flag -fPIC -DPIC works... yes 
checking if mips-linux-gnu-gcc static flag -static works... yes 
checking if mips-linux-gnu-gcc supports -c -o file.o... yes 
checking if mips-linux-gnu-gcc supports -c -o file.o... (cached) yes 
checking whether the mips-linux-gnu-gcc linker (/home/intel/mips-4.3/mips-linux-gnu/bin/ld) supports shared libraries... yes 
checking whether -lc should be explicitly linked in... no 
checking dynamic linker characteristics... GNU/Linux ld.so 
checking how to hardcode library paths into programs... immediate 
checking whether stripping libraries is possible... yes 
checking if libtool supports shared libraries... yes 
checking whether to build shared libraries... yes 
checking whether to build static libraries... no 
checking for gawk... (cached) gawk 
checking for mips-linux-gnu-pkg-config... no 
checking for pkg-config... /usr/bin/pkg-config 
configure: WARNING: using cross tools not prefixed with host triplet 
checking pkg-config is at least version 0.9.0... yes 
checking for gtkdoc-check... no 
checking for gtkdoc-rebase... no 
checking for gtkdoc-mkpdf... no 
checking whether to build gtk-doc documentation... no 
checking for xsltproc... /usr/bin/xsltproc 
checking for gperf... /usr/bin/gperf 
checking for GLIB... yes 
checking for acl_init in -lacl... no 
configure: error: libacl not found
``` 

Please guide me to fix this error. I also have installed libacl using sudo -apt-get install command. yet it throws error while configuring it.

---

### Post by oldos2er on 2013-01-24
Moved to Packaging and Compiling Programs.

---

