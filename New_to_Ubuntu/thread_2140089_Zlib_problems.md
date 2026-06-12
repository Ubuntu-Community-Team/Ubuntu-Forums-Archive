---
title: "Zlib problems"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by ralphonzo on 2013-04-28
I'm trying to install an app (mixmaster) that requires several libraries, including zlib. I've downloaded these libraries & extracted them to the required directory.

Yet when I run install, it won't recognize some of the necessary libraries - specifically libcrypto.a. Clearly I'm a newbie, & the few attempted solutions I found were either overly specific or went around in circles. There are instructions for "installation problems" in the mixmaster ReadMe, but these either don't apply or don't work.

Here's what I got after running the install script. Thanks for any help!


```
Looking for libz.a...
Found source directory zlib-1.2.7.
Configuring...
Checking for gcc...
Checking for shared library support...
Building shared library libz.so.1.2.7 with gcc.
Checking for off64_t... Yes.
Checking for fseeko... Yes.
Checking for strerror... Yes.
Checking for unistd.h... Yes.
Checking for stdarg.h... Yes.
Checking whether to use vs[n]printf() or s[n]printf()... using vs[n]printf().
Checking for vsnprintf() in stdio.h... Yes.
Checking for return value of vsnprintf()... Yes.
Checking for attribute(visibility) support... Yes.
Looking for a four-byte integer type... Found.
Looking for libpcre.a...
Found source directory pcre-8.32.
Configuring...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
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
checking for int64_t... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... dlltool
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
checking whether to build static libraries... yes
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
checking whether ln -s works... yes
checking whether the -Werror option is usable... yes
checking for simple visibility declarations... yes
checking for ANSI C header files... (cached) yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
checking for alias support in the linker... no
checking for alias support in the linker... no
checking string usability... yes
checking string presence... yes
checking for string... yes
checking bits/type_traits.h usability... no
checking bits/type_traits.h presence... no
checking for bits/type_traits.h... no
checking type_traits.h usability... no
checking type_traits.h presence... no
checking for type_traits.h... no
checking for strtoq... yes
checking for long long... yes
checking for unsigned long long... yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking for bcopy... yes
checking for memmove... yes
checking for strerror... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for gzopen in -lz... yes
checking bzlib.h usability... no
checking bzlib.h presence... no
checking for bzlib.h... no
checking for libbz2... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libpcre.pc
config.status: creating libpcre16.pc
config.status: creating libpcre32.pc
config.status: creating libpcreposix.pc
config.status: creating libpcrecpp.pc
config.status: creating pcre-config
config.status: creating pcre.h
config.status: creating pcre_stringpiece.h
config.status: creating pcrecpparg.h
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing script-chmod commands
config.status: executing delete-old-chartables commands

pcre-8.32 configuration summary:

Install prefix .................. : /usr/local
C preprocessor .................. : gcc -E
C compiler ...................... : gcc
C++ preprocessor ................ : g++ -E
C++ compiler .................... : g++
Linker .......................... : /usr/bin/ld
C preprocessor flags ............ :
C compiler flags ................ : -O2 -fvisibility=hidden
C++ compiler flags .............. : -O2 -fvisibility=hidden -fvisibility-inlines-hidden
Linker flags .................... :
Extra libraries ................. :

Build 8 bit pcre library ........ : yes
Build 16 bit pcre library ....... : no
Build 32 bit pcre library ....... : no
Build C++ library ............... : yes
Enable JIT compiling support .... : no
Enable UTF-8/16/32 support ...... : no
Unicode properties .............. : no
Newline char/sequence ........... : lf
\R matches only ANYCRLF ......... : no
EBCDIC coding ................... : no
EBCDIC code for NL .............. : n/a
Rebuild char tables ............. : no
Use stack recursion ............. : yes
POSIX mem threshold ............. : 10
Internal link size .............. : 2
Match limit ..................... : 10000000
Match limit recursion ........... : MATCH_LIMIT
Build shared libs ............... : yes
Build static libs ............... : yes
Use JIT in pcregrep ............. : no
Buffer size for pcregrep ........ : 20480
Link pcregrep with libz ......... : no
Link pcregrep with libbz2 ....... : no
Link pcretest with libedit ...... : no
Link pcretest with libreadline .. : no
Valgrind support ................ : no
Code coverage ................... : no

Looking for libcrypto.a...
Not found.
```

---

### Post by schragge on 2013-04-28
*libcrypto.a* is in package *libssl-dev*, you also didn't have to download *zlib* and *pcre* as they are provided by packages *zlib1g-dev* and *libpcre3-dev*, respectively. Just run ```
sudo apt-get install {zlib1g,libpcre3,libssl}-dev
```

I'd also recommend installing [apt-file](http://manpages.ubuntu.com/manpages/raring/en/man1/apt-file.1.html) as it will help you to find out what package provides which library.

---

### Post by ralphonzo on 2013-04-28
Yes, all three of these -dev libraries were previously installed ("libssl-dev is already the newest version," etc.). And you're right: apt-file tells me libcrypto.a belongs to libssl-dev. So why it's not finding it, I'm at a loss.

---

### Post by schragge on 2013-04-28
Well, [mixmaster](http://manpages.ubuntu.com/manpages/raring/en/man1/mixmaster.1.html) is also in Ubuntu repository. Is there a specific reason why you wouldn't install the package from *universe*?

---

### Post by ralphonzo on 2013-04-28
Voila! I could swear I searched for it previously with no luck, but I do have a tendency to take the long road. Now I'm trying to figure out how to send messages. Do I need sendmail to do this, or some other server app (again, I know this is ridiculous newbie stuff)? I'm using 12.04.

---

### Post by schragge on 2013-04-28
As stated [here](http://wiki.ubuntuusers.de/Mixmaster) (in German), mixmaster uses Postfix by default to send messages, but configuring it to use a remote SMTP server is also possible.

---

### Post by ralphonzo on 2013-04-29
Thanks! Meant to respond earlier, but I couldn't load this page for several hours.

---

