---
title: "Problems installing .tar.gz file"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by Sigmund1 on 2013-07-11
Hi all,

I'm trying to install the RoboCup Soccer Simulation Server, which comes in a .tar.gz file, but I'm not able to complete the installation.
I found out I have to do the following:

```
tar zxf file.tar.gz
./configure
make
make install
```

At the "./configure" step it goes wrong:
First I had the problem that I had no C or C++ compiler installed. This was easily solved by installing it.
But now I get the following error:
```
$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gawk... (cached) mawk
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for cos in -lm... yes
checking for deflate in -lz... no
checking whether the compiler implements namespaces... yes
checking whether the compiler has stringstream... yes
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
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for ANSI C header files... (cached) yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for inttypes.h... (cached) yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for libintl.h... (cached) yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for sys/types.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for int16_t... yes
checking for int32_t... yes
checking for int8_t... yes
checking for size_t... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for uint16_t... yes
checking for uint32_t... yes
checking for uint8_t... yes
checking for socklen_t... yes
checking for size_t... (cached) yes
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking return type of signal handlers... void
checking for strftime... yes
checking for memset... yes
checking for floor... yes
checking for gethostbyname... yes
checking for gettimeofday... yes
checking for inet_ntoa... yes
checking for memset... (cached) yes
checking for mkdir... yes
checking for pow... yes
checking for rint... yes
checking for socket... yes
checking for sqrt... yes
checking for strdup... yes
checking for strerror... yes
checking for flex... flex
checking lex output file root... lex.yy
checking lex library... -lfl
checking whether yytext is a pointer... yes
checking if flex is the lexer generator... yes
checking for bison... bison -y
checking if bison is the parser generator... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
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
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for boostlib >= 1.32.0... yes
checking whether the Boost::System library is available... yes
configure: error: Could not find a version of the library!

```

I found some threats that it might be something with the 'libboost', but according to the code above, it says that boostlib is installed.

So I'm really stuck here.


Thanks in advance,

Sigmund

PS: I use Ubuntu 12.04
PPS: I'm fairly new to Ubuntu. I only know the basic commands (ls, cd, mkdir, vim, ...)

---

### Post by Sigmund1 on 2013-07-11
Oke, I solved my problem.
It still was a problem with the libboost.
I had to type in the following in my command window:
```
[COLOR=#000000][FONT=Consolas]sudo apt[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]-[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]get install libboost[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]-[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]all[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]-[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]dev[/FONT][/COLOR]
```

Next I had some restriction problems when doing make install, but that was again easily solved with sudo:
```
sudo make install
```

---

### Post by Sigmund1 on 2013-07-11
Now I'm trying to install a second program (the robocup soccer monitor).
Again, it comes in a .tar.gz file, and again I'm stuck at the "./configure" part:

```
$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for cos in -lm... yes
checking for deflate in -lz... yes
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
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for inline... inline
checking for an ANSI C-conforming const... yes
checking for int16_t... yes
checking for int32_t... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for uint16_t... yes
checking for uint32_t... yes
checking for error_at_line... yes
checking for memset... yes
checking for rint... yes
checking for strtol... yes
checking for pow... yes
checking for sqrt... yes
checking for boostlib >= 1.32.0... yes
checking build system type... i686-pc-linux-gnu
checking whether the Boost::System library is available... yes
checking for exit in -lboost_system-mt... yes
checking whether the Boost::Program_Options library is available... yes
checking for exit in -lboost_program_options-mt... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
configure: set QT4_REQUIRED_VERSION... 4.3.0
configure: set QT4_REQUIRED_MODULES... QtCore QtGui QtNetwork
checking for pkg-config... /usr/bin/pkg-config
configure: check QtCore >= 4.3.0
checking for Qt4... no
configure: error: The QtCore library >= 4.3.0 could not be found.
```

So I guess I need to install some sort of Qt4 package? What exactly do I have to install?

---

### Post by Sigmund1 on 2013-07-11
And yet again, Google is my friend. This solved my problem:
```
sudo apt-get install libqt4-dev
```

---

