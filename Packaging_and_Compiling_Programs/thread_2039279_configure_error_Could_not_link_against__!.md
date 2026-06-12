---
title: "configure: error: Could not link against  !"
date: 2012-08-08
forum: Packaging and Compiling Programs
---

### Post by ssuave on 2012-08-08
Hi, on Ubuntu 12.04   64 bit, I am getting this configure error. 
I post the full message below, kindly help to get rid of it. 


```
 ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for main in -lpthread... yes
checking for XML_Parse in -lexpat... yes
checking for svnversion... yes
checking for pthread_create in -lpthread... yes
checking for main in -lm... yes
checking for main in -lz... yes
checking for main in -lbz2... yes
checking for main in -lx264... yes
checking for main in -lvpx... yes
checking for main in -lvorbisenc... yes
checking for main in -lvorbis... yes
checking for main in -ltheoradec... yes
checking for main in -ltheoraenc... yes
checking for main in -lopencore-amrwb... yes
checking for main in -lopencore-amrnb... yes
checking for main in -lfaac... yes
checking for main in -lmp3lame... yes
checking for clock_gettime in -lrt... yes
checking for boostlib >= 1.40... yes
checking whether the Boost::System library is available... yes
checking whether the Boost::Filesystem library is available... yes
configure: error: Could not link against  !
```

---

### Post by oldos2er on 2012-08-08
Moved to Packaging and Compiling Programs.

It would help if you would mention what program you're trying to compile, and where you downloaded the source code from.

---

### Post by Bachstelze on 2012-08-08
Paste config.log. It's large so if the forum doesn't let you post it, you can gzip and attach it.

---

### Post by ssuave on 2012-08-08
> **oldos2er said:**
> Moved to Packaging and Compiling Programs.

It would help if you would mention what program you're trying to compile, and where you downloaded the source code from.

I am at the step './configure' as given in the 'installation' file of Sirannon:
[http://sirannon.atlantis.ugent.be/](http://sirannon.atlantis.ugent.be/)

---

### Post by ssuave on 2012-08-08
> **Bachstelze said:**
> Paste config.log. It's large so if the forum doesn't let you post it, you can gzip and attach it.

Hi,

plz view the attached zip file. thanks!

---

### Post by Bachstelze on 2012-08-09
I asked for config.log, not for configure.

---

### Post by ssuave on 2012-08-09
> **Bachstelze said:**
> I asked for config.log, not for configure.
uh sorry, its attached now

---

### Post by Bachstelze on 2012-08-09
The log doesn't give any info so I'm just guessing here. Do you have libboost-filesystem-dev and libboost-regex-dev installed?

---

### Post by SevenMachines on 2012-08-09
Seems that this is configuring itself to look for libraries in lib64/ if it finds itself on x86-64, hence the linking issue. You can change it with...
```
# libsubdir is setup in m4 scripts
$ grep -r lib64 m4/
m4/ax_boost_base.m4:        libsubdir="lib64"

# Change from lib64->lib
$ sed -i 's/libsubdir="lib64"/libsubdir="lib"/g' m4/ax_boost_base.m4 

# ok
$ grep -r libsubdir= m4/
m4/ax_boost_base.m4:    libsubdir="lib"
m4/ax_boost_base.m4:        libsubdir="lib"

# Will need to update configure now too
$ grep -r libsubdir= configure
    libsubdir="lib"
        libsubdir="lib64"
    libsubdir="lib"
        libsubdir="lib64"

$ autoconf

# ok
$ grep -r libsubdir= configure
    libsubdir="lib"
        libsubdir="lib"
    libsubdir="lib"
        libsubdir="lib"

# Might/should work now
$ ./configure

```

Note though, if configure is broken, usually the code tends to be broken too :) There is probably a better way of setting up autotools too if you have the time and inclination

---

