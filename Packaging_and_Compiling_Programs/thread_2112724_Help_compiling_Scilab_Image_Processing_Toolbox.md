---
title: "Help compiling Scilab Image Processing Toolbox"
date: 2013-02-05
forum: Packaging and Compiling Programs
---

### Post by satyamM on 2013-02-05
Hello,

I am trying to install Scilab Image Processing Toolbox in my existing installation of Scilab.

I downloaded, unzipped it and then I tried to do **./configure** as this is first command in completion of installation.

But **./configure** ran fine for most of its execution time but at last it shows some problem. 
[B]
The whole output of ./configure is below::
[/B]

```

satyam@ubuntu:~/Desktop/sip-0.5.6$ ./configure
configuring SIP 0.5.6
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
[B]checking whether to build static libraries... no
./configure: line 10824: ./libtool: No such file or directory
checking for scilab... yes
Scilab version is 5
checking for animal-config... no
checking for animal - version >= 0.14.0... no
*** The $ac_path_lib_animal_config script installed by animal could not be found.
*** If animal was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the ANIMAL_CONFIG environment variable to the
*** full path to $ac_path_lib_animal_config.
configure: error: Either AnImaL version >= 0.13.0 was not found or a compile test failed.
satyam@ubuntu:~/Desktop/sip-0.5.6$ [/B]


```
I have bold marked the lines(scroll down in above code to see the lines) which I think might have created problems..

Please help someone...

---

### Post by satyamM on 2013-02-05
@[jwbrase]("http://ubuntuforums.org/member.php?u=766828") and others...

I see only two files

[HTML]Makefile.am
Makefile.in[/HTML][B]
No Makefile


.
[/B]

---

### Post by oldos2er on 2013-02-05
Posts moved to their own thread.

---

