---
title: "Compile Issues - pthread"
date: 2007-06-12
forum: Programming Talk
---

### Post by Loprete on 2007-06-12
Hi,

I'm trying to compile JIAXClient @ Kubuntu.

```
JIAXClient v0.0.5
=================

Java IAXClient Library


Build Requirements
------------------
C++ compiler (G++ 3.3 tested)
Java compiler tools (javac, javah and jar) (GCJ 3.3 tested)
POSIX Threads (pthread) (POSIX Threads for Win32 [1]
  release 2.6.0 tested on Windows)
IAXClient [2] (cvs 20050503 tested)
jarsigner from J2SE SDK (for signing) (J2SE v 1.4 SDK [3] tested)

[1] http://sources.redhat.com/pthreads-win32/
[2] http://iaxclient.sourceforge.net/
[3] http://java.sun.com/j2se/1.4.2/download.html
```

All build requirements are installed.


Then I try this:

```
./configure JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun CPPLAGS="-I/usr/lib" LDFLAGS="-L/usr/lib" --with-pthreads-path="/usr/lib"
```

And it returns:

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for gawk... (cached) mawk
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for kaffe... no
checking for java... /usr/lib/jvm/java-1.5.0-sun/bin/java
checking for dlltool... dlltool
checking for gcj... no
checking for javacc... no
checking for HtmlConverter... /usr/lib/jvm/java-1.5.0-sun/bin/HtmlConverter
checking for jar... /usr/lib/jvm/java-1.5.0-sun/bin/jar
checking for gcj-wrapper... no
checking for gcj... no
checking for guavac... no
checking for jikes... no
checking for javac... /usr/lib/jvm/java-1.5.0-sun/bin/javac
checking if /usr/lib/jvm/java-1.5.0-sun/bin/javac works... yes
checking for javah... /usr/lib/jvm/java-1.5.0-sun/bin/javah
path
checking for jarsigner... /usr/lib/jvm/java-1.5.0-sun/bin/jarsigner
checking for javadoc... /usr/lib/jvm/java-1.5.0-sun/bin/javadoc
checking for /usr/lib/jvm/java-1.5.0-sun/bin/javac... /usr/lib/jvm/java-1.5.0-sun/bin/javac
/usr/lib/jvm/java-1.5.0-sun/bin/javac
/usr/lib/jvm/java-1.5.0-sun/bin
/usr/lib/jvm/java-1.5.0-sun/bin/include
/usr/lib/jvm/java-1.5.0-sun/include /usr/lib/jvm/java-1.5.0-sun/include/linux
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for cc_r... gcc
checking for log10 in -lm... yes
checking for speex_encoder_init in -lspeex... no
checking for gsm_create in -lgsm... yes
checking for Pa_Initialize in -lportaudio... yes
checking for iaxc_initialize in -liaxclient... no
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking for inttypes.h... (cached) yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking pthread.h usability... no
checking pthread.h presence... yes
configure: WARNING: pthread.h: present but cannot be compiled
configure: WARNING: pthread.h:     check for missing prerequisite headers?
configure: WARNING: pthread.h: see the Autoconf documentation
configure: WARNING: pthread.h:     section "Present But Cannot Be Compiled"
configure: WARNING: pthread.h: proceeding with the preprocessor's result
configure: WARNING: pthread.h: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------------------------------- ##
configure: WARNING:     ## Report this to Mikael Magnusson <mikma@users.sourceforge.net> ##
configure: WARNING:     ## ------------------------------------------------------------- ##
checking for pthread.h... yes
checking iaxclient.h usability... yes
checking iaxclient.h presence... yes
checking for iaxclient.h... yes
checking jni.h usability... yes
checking jni.h presence... yes
checking for jni.h... yes
checking for an ANSI C-conforming const... yes
checking for memset... yes
checking for ptw32_processInitialize... no
checking for ptw32_processTerminate... no

Configured jiaxclient 0.0.6 for `i686-pc-linux-gnu'

configure: creating ./config.status
config.status: creating Makefile
config.status: creating utils/Makefile
config.status: creating jni/Makefile
config.status: creating doc/Makefile
config.status: creating ext/Makefile
config.status: creating inifile/Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

```



There is a pthread warning, but I tried to compile (**make**) and it returns:

```
make  all-recursive
make[1]: Entrando no diretório `/home/sctl/jiaxclient/jiaxclient-0.0.6'
Making all in .
make[2]: Entrando no diretório `/home/sctl/jiaxclient/jiaxclient-0.0.6'
test -e javaroot || mkdir javaroot
make[2]: Saindo do diretório `/home/sctl/jiaxclient/jiaxclient-0.0.6'
Making all in utils
make[2]: Entrando no diretório `/home/sctl/jiaxclient/jiaxclient-0.0.6/utils'
make[2]: Nada a ser feito para `all'.
make[2]: Saindo do diretório `/home/sctl/jiaxclient/jiaxclient-0.0.6/utils'
Making all in jni
make[2]: Entrando no diretório `/home/sctl/jiaxclient/jiaxclient-0.0.6/jni'
g++ -fPIC -pthread -g -O2 -DHAVE_CONFIG_H -I. -I.. -I. -I.. -I../include -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread -I/usr/lib/jvm/java-1.5.0-sun/include/  -c -o jiaxclient.o jiaxclient.cc
/usr/include/pthread.h:285: error: conflicting declaration ‘typedef struct pthread_st* pthread_t’
/usr/include/bits/pthreadtypes.h:36: error: ‘pthread_t’ has a previous declaration as ‘typedef long unsigned int pthread_t’
/usr/include/pthread.h:286: error: conflicting declaration ‘typedef struct pthread_attr_st* pthread_attr_t’
/usr/include/bits/pthreadtypes.h:43: error: ‘pthread_attr_t’ has a previous declaration as ‘typedef union pthread_attr_t pthread_attr_t’
/usr/include/pthread.h:287: error: conflicting declaration ‘typedef int pthread_key_t’
/usr/include/bits/pthreadtypes.h:109: error: ‘pthread_key_t’ has a previous declaration as ‘typedef unsigned int pthread_key_t’
/usr/include/pthread.h:289: error: conflicting declaration ‘typedef int pthread_mutexattr_t’
/usr/include/bits/pthreadtypes.h:79: error: ‘pthread_mutexattr_t’ has a previous declaration as ‘typedef union pthread_mutexattr_t pthread_mutexattr_t’
/usr/include/pthread.h:290: error: conflicting declaration ‘typedef struct pthread_mutex_st* pthread_mutex_t’
/usr/include/bits/pthreadtypes.h:73: error: ‘pthread_mutex_t’ has a previous declaration as ‘typedef union pthread_mutex_t pthread_mutex_t’
/usr/include/pthread.h:291: error: conflicting declaration ‘typedef int pthread_condattr_t’
/usr/include/bits/pthreadtypes.h:105: error: ‘pthread_condattr_t’ has a previous declaration as ‘typedef union pthread_condattr_t pthread_condattr_t’
/usr/include/pthread.h:292: error: conflicting declaration ‘typedef struct pthread_cond_st* pthread_cond_t’
/usr/include/bits/pthreadtypes.h:99: error: ‘pthread_cond_t’ has a previous declaration as ‘typedef union pthread_cond_t pthread_cond_t’
/usr/include/pthread.h:293: error: conflicting declaration ‘typedef int pthread_rwlockattr_t’
/usr/include/bits/pthreadtypes.h:142: error: ‘pthread_rwlockattr_t’ has a previous declaration as ‘typedef union pthread_rwlockattr_t pthread_rwlockattr_t’
/usr/include/pthread.h:294: error: conflicting declaration ‘typedef struct pthread_rwlock_st* pthread_rwlock_t’
/usr/include/bits/pthreadtypes.h:136: error: ‘pthread_rwlock_t’ has a previous declaration as ‘typedef union pthread_rwlock_t pthread_rwlock_t’
make[2]: ** [jiaxclient.o] Erro 1
make[2]: Saindo do diretório `/home/sctl/jiaxclient/jiaxclient-0.0.6/jni'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/sctl/jiaxclient/jiaxclient-0.0.6'
make: ** [all] Erro 2

```


What can I do??

---

### Post by Loprete on 2007-06-12
And here is the complete compile log:

```
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by jiaxclient configure 0.0.6, which was
generated by GNU Autoconf 2.59.  Invocation command line was

  $ ./configure JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun CPPLAGS=-I/usr/lib LDFLAGS=-L/usr/lib --with-pthreads-path=/usr/lib

## --------- ##
## Platform. ##
## --------- ##

hostname = sctl-desktop
uname -m = i686
uname -r = 2.6.20-16-generic
uname -s = Linux
uname -v = #2 SMP Wed May 23 01:46:23 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1595: checking build system type
configure:1613: result: i686-pc-linux-gnu
configure:1621: checking host system type
configure:1635: result: i686-pc-linux-gnu
configure:1658: checking for a BSD-compatible install
configure:1713: result: /usr/bin/install -c
configure:1724: checking whether build environment is sane
configure:1767: result: yes
configure:1832: checking for gawk
configure:1861: result: no
configure:1832: checking for mawk
configure:1848: found /usr/bin/mawk
configure:1858: result: mawk
configure:1868: checking whether make sets $(MAKE)
configure:1888: result: yes
configure:2205: checking for g++
configure:2221: found /usr/bin/g++
configure:2231: result: g++
configure:2247: checking for C++ compiler version
configure:2250: g++ --version </dev/null >&5
g++ (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2253: $? = 0
configure:2255: g++ -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:2258: $? = 0
configure:2260: g++ -V </dev/null >&5
g++: '-V' option must have argument
configure:2263: $? = 1
configure:2286: checking for C++ compiler default output file name
configure:2289: g++   -L/usr/lib conftest.cc  >&5
configure:2292: $? = 0
configure:2338: result: a.out
configure:2343: checking whether the C++ compiler works
configure:2349: ./a.out
configure:2352: $? = 0
configure:2369: result: yes
configure:2376: checking whether we are cross compiling
configure:2378: result: no
configure:2381: checking for suffix of executables
configure:2383: g++ -o conftest   -L/usr/lib conftest.cc  >&5
configure:2386: $? = 0
configure:2411: result: 
configure:2417: checking for suffix of object files
configure:2438: g++ -c   conftest.cc >&5
configure:2441: $? = 0
configure:2463: result: o
configure:2467: checking whether we are using the GNU C++ compiler
configure:2491: g++ -c   conftest.cc >&5
configure:2497: $? = 0
configure:2500: test -z 			 || test ! -s conftest.err
configure:2503: $? = 0
configure:2506: test -s conftest.o
configure:2509: $? = 0
configure:2522: result: yes
configure:2528: checking whether g++ accepts -g
configure:2549: g++ -c -g  conftest.cc >&5
configure:2555: $? = 0
configure:2558: test -z 			 || test ! -s conftest.err
configure:2561: $? = 0
configure:2564: test -s conftest.o
configure:2567: $? = 0
configure:2578: result: yes
configure:2620: g++ -c -g -O2  conftest.cc >&5
configure:2626: $? = 0
configure:2629: test -z 			 || test ! -s conftest.err
configure:2632: $? = 0
configure:2635: test -s conftest.o
configure:2638: $? = 0
configure:2664: g++ -c -g -O2  conftest.cc >&5
conftest.cc: In function 'int main()':
conftest.cc:15: error: 'exit' was not declared in this scope
configure:2670: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| exit (42);
|   ;
|   return 0;
| }
configure:2620: g++ -c -g -O2  conftest.cc >&5
configure:2626: $? = 0
configure:2629: test -z 			 || test ! -s conftest.err
configure:2632: $? = 0
configure:2635: test -s conftest.o
configure:2638: $? = 0
configure:2664: g++ -c -g -O2  conftest.cc >&5
configure:2670: $? = 0
configure:2673: test -z 			 || test ! -s conftest.err
configure:2676: $? = 0
configure:2679: test -s conftest.o
configure:2682: $? = 0
configure:2716: checking for style of include used by make
configure:2744: result: GNU
configure:2772: checking dependency style of g++
configure:2862: result: gcc3
configure:2944: checking for gcc
configure:2960: found /usr/bin/gcc
configure:2970: result: gcc
configure:3214: checking for C compiler version
configure:3217: gcc --version </dev/null >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3220: $? = 0
configure:3222: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:3225: $? = 0
configure:3227: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:3230: $? = 1
configure:3233: checking whether we are using the GNU C compiler
configure:3257: gcc -c   conftest.c >&5
configure:3263: $? = 0
configure:3266: test -z 			 || test ! -s conftest.err
configure:3269: $? = 0
configure:3272: test -s conftest.o
configure:3275: $? = 0
configure:3288: result: yes
configure:3294: checking whether gcc accepts -g
configure:3315: gcc -c -g  conftest.c >&5
configure:3321: $? = 0
configure:3324: test -z 			 || test ! -s conftest.err
configure:3327: $? = 0
configure:3330: test -s conftest.o
configure:3333: $? = 0
configure:3344: result: yes
configure:3361: checking for gcc option to accept ANSI C
configure:3431: gcc  -c -g -O2  conftest.c >&5
configure:3437: $? = 0
configure:3440: test -z 			 || test ! -s conftest.err
configure:3443: $? = 0
configure:3446: test -s conftest.o
configure:3449: $? = 0
configure:3467: result: none needed
configure:3485: gcc -c -g -O2  conftest.c >&5
conftest.c:2: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'me'
configure:3491: $? = 1
configure: failed program was:
| #ifndef __cplusplus
|   choke me
| #endif
configure:3623: checking dependency style of gcc
configure:3713: result: gcc3
configure:3734: checking for gawk
configure:3760: result: mawk
configure:3844: checking for a sed that does not truncate output
configure:3898: result: /bin/sed
configure:3901: checking for egrep
configure:3911: result: grep -E
configure:3927: checking for ld used by gcc
configure:3994: result: /usr/bin/ld
configure:4003: checking if the linker (/usr/bin/ld) is GNU ld
configure:4018: result: yes
configure:4023: checking for /usr/bin/ld option to reload object files
configure:4030: result: -r
configure:4048: checking for BSD-compatible nm
configure:4090: result: /usr/bin/nm -B
configure:4094: checking whether ln -s works
configure:4098: result: yes
configure:4105: checking how to recognise dependent libraries
configure:4277: result: pass_all
configure:4732: checking how to run the C preprocessor
configure:4767: gcc -E  conftest.c
configure:4773: $? = 0
configure:4805: gcc -E  conftest.c
conftest.c:14:28: error: ac_nonexistent.h: No such file or directory
configure:4811: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:4850: result: gcc -E
configure:4874: gcc -E  conftest.c
configure:4880: $? = 0
configure:4912: gcc -E  conftest.c
conftest.c:14:28: error: ac_nonexistent.h: No such file or directory
configure:4918: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:4962: checking for ANSI C header files
configure:4987: gcc -c -g -O2  conftest.c >&5
configure:4993: $? = 0
configure:4996: test -z 			 || test ! -s conftest.err
configure:4999: $? = 0
configure:5002: test -s conftest.o
configure:5005: $? = 0
configure:5094: gcc -o conftest -g -O2  -L/usr/lib conftest.c  >&5
conftest.c: In function 'main':
conftest.c:31: warning: incompatible implicit declaration of built-in function 'exit'
configure:5097: $? = 0
configure:5099: ./conftest
configure:5102: $? = 0
configure:5117: result: yes
configure:5141: checking for sys/types.h
configure:5157: gcc -c -g -O2  conftest.c >&5
configure:5163: $? = 0
configure:5166: test -z 			 || test ! -s conftest.err
configure:5169: $? = 0
configure:5172: test -s conftest.o
configure:5175: $? = 0
configure:5186: result: yes
configure:5141: checking for sys/stat.h
configure:5157: gcc -c -g -O2  conftest.c >&5
configure:5163: $? = 0
configure:5166: test -z 			 || test ! -s conftest.err
configure:5169: $? = 0
configure:5172: test -s conftest.o
configure:5175: $? = 0
configure:5186: result: yes
configure:5141: checking for stdlib.h
configure:5157: gcc -c -g -O2  conftest.c >&5
configure:5163: $? = 0
configure:5166: test -z 			 || test ! -s conftest.err
configure:5169: $? = 0
configure:5172: test -s conftest.o
configure:5175: $? = 0
configure:5186: result: yes
configure:5141: checking for string.h
configure:5157: gcc -c -g -O2  conftest.c >&5
configure:5163: $? = 0
configure:5166: test -z 			 || test ! -s conftest.err
configure:5169: $? = 0
configure:5172: test -s conftest.o
configure:5175: $? = 0
configure:5186: result: yes
configure:5141: checking for memory.h
configure:5157: gcc -c -g -O2  conftest.c >&5
configure:5163: $? = 0
configure:5166: test -z 			 || test ! -s conftest.err
configure:5169: $? = 0
configure:5172: test -s conftest.o
configure:5175: $? = 0
configure:5186: result: yes
configure:5141: checking for strings.h
configure:5157: gcc -c -g -O2  conftest.c >&5
configure:5163: $? = 0
configure:5166: test -z 			 || test ! -s conftest.err
configure:5169: $? = 0
configure:5172: test -s conftest.o
configure:5175: $? = 0
configure:5186: result: yes
configure:5141: checking for inttypes.h
configure:5157: gcc -c -g -O2  conftest.c >&5
configure:5163: $? = 0
configure:5166: test -z 			 || test ! -s conftest.err
configure:5169: $? = 0
configure:5172: test -s conftest.o
configure:5175: $? = 0
configure:5186: result: yes
configure:5141: checking for stdint.h
configure:5157: gcc -c -g -O2  conftest.c >&5
configure:5163: $? = 0
configure:5166: test -z 			 || test ! -s conftest.err
configure:5169: $? = 0
configure:5172: test -s conftest.o
configure:5175: $? = 0
configure:5186: result: yes
configure:5141: checking for unistd.h
configure:5157: gcc -c -g -O2  conftest.c >&5
configure:5163: $? = 0
configure:5166: test -z 			 || test ! -s conftest.err
configure:5169: $? = 0
configure:5172: test -s conftest.o
configure:5175: $? = 0
configure:5186: result: yes
configure:5212: checking dlfcn.h usability
configure:5224: gcc -c -g -O2  conftest.c >&5
configure:5230: $? = 0
configure:5233: test -z 			 || test ! -s conftest.err
configure:5236: $? = 0
configure:5239: test -s conftest.o
configure:5242: $? = 0
configure:5252: result: yes
configure:5256: checking dlfcn.h presence
configure:5266: gcc -E  conftest.c
configure:5272: $? = 0
configure:5292: result: yes
configure:5327: checking for dlfcn.h
configure:5334: result: yes
configure:5357: checking how to run the C++ preprocessor
configure:5388: g++ -E  conftest.cc
configure:5394: $? = 0
configure:5426: g++ -E  conftest.cc
conftest.cc:25:28: error: ac_nonexistent.h: No such file or directory
configure:5432: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:5471: result: g++ -E
configure:5495: g++ -E  conftest.cc
configure:5501: $? = 0
configure:5533: g++ -E  conftest.cc
conftest.cc:25:28: error: ac_nonexistent.h: No such file or directory
configure:5539: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:5636: checking for g77
configure:5665: result: no
configure:5636: checking for f77
configure:5665: result: no
configure:5636: checking for xlf
configure:5665: result: no
configure:5636: checking for frt
configure:5665: result: no
configure:5636: checking for pgf77
configure:5665: result: no
configure:5636: checking for fort77
configure:5665: result: no
configure:5636: checking for fl32
configure:5665: result: no
configure:5636: checking for af77
configure:5665: result: no
configure:5636: checking for f90
configure:5665: result: no
configure:5636: checking for xlf90
configure:5665: result: no
configure:5636: checking for pgf90
configure:5665: result: no
configure:5636: checking for epcf90
configure:5665: result: no
configure:5636: checking for f95
configure:5665: result: no
configure:5636: checking for fort
configure:5665: result: no
configure:5636: checking for xlf95
configure:5665: result: no
configure:5636: checking for ifc
configure:5665: result: no
configure:5636: checking for efc
configure:5665: result: no
configure:5636: checking for pgf95
configure:5665: result: no
configure:5636: checking for lf95
configure:5665: result: no
configure:5636: checking for gfortran
configure:5665: result: no
configure:5677: checking for Fortran 77 compiler version
configure:5680:  --version </dev/null >&5
./configure: line 5681: --version: command not found
configure:5683: $? = 127
configure:5685:  -v </dev/null >&5
./configure: line 5686: -v: command not found
configure:5688: $? = 127
configure:5690:  -V </dev/null >&5
./configure: line 5691: -V: command not found
configure:5693: $? = 127
configure:5701: checking whether we are using the GNU Fortran 77 compiler
configure:5715:  -c  conftest.F >&5
./configure: line 5716: -c: command not found
configure:5721: $? = 127
configure: failed program was:
|       program main
| #ifndef __GNUC__
|        choke me
| #endif
| 
|       end
configure:5746: result: no
configure:5752: checking whether  accepts -g
configure:5764:  -c -g conftest.f >&5
./configure: line 5765: -c: command not found
configure:5770: $? = 127
configure: failed program was:
|       program main
| 
|       end
configure:5794: result: no
configure:5824: checking the maximum length of command line arguments
configure:5916: result: 32768
configure:5927: checking command to parse /usr/bin/nm -B output from gcc object
configure:6023: gcc -c -g -O2  conftest.c >&5
configure:6026: $? = 0
configure:6030: /usr/bin/nm -B conftest.o \| sed -n -e 's/^.*[ 	]\([ABCDGIRSTW][ABCDGIRSTW]*\)[ 	][ 	]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p' \> conftest.nm
configure:6033: $? = 0
configure:6085: gcc -o conftest -g -O2  -L/usr/lib conftest.c conftstm.o >&5
configure:6088: $? = 0
configure:6126: result: ok
configure:6130: checking for objdir
configure:6145: result: .libs
configure:6235: checking for ar
configure:6251: found /usr/bin/ar
configure:6262: result: ar
configure:6315: checking for ranlib
configure:6331: found /usr/bin/ranlib
configure:6342: result: ranlib
configure:6395: checking for strip
configure:6411: found /usr/bin/strip
configure:6422: result: strip
configure:6709: checking if gcc static flag  works
configure:6737: result: yes
configure:6755: checking if gcc supports -fno-rtti -fno-exceptions
configure:6773: gcc -c -g -O2  -fno-rtti -fno-exceptions conftest.c >&5
cc1: warning: command line option "-fno-rtti" is valid for C++/ObjC++ but not for C
configure:6777: $? = 0
configure:6790: result: no
configure:6805: checking for gcc option to produce PIC
configure:7009: result: -fPIC
configure:7017: checking if gcc PIC flag -fPIC works
configure:7035: gcc -c -g -O2  -fPIC -DPIC conftest.c >&5
configure:7039: $? = 0
configure:7052: result: yes
configure:7076: checking if gcc supports -c -o file.o
configure:7097: gcc -c -g -O2  -o out/conftest2.o conftest.c >&5
configure:7101: $? = 0
configure:7123: result: yes
configure:7149: checking whether the gcc linker (/usr/bin/ld) supports shared libraries
configure:8044: result: yes
configure:8070: checking whether -lc should be explicitly linked in
configure:8075: gcc -c -g -O2  conftest.c >&5
configure:8078: $? = 0
configure:8092: gcc -shared conftest.o  -v -Wl,-soname -Wl,conftest -o conftest 2\>\&1 \| grep  -lc  \>/dev/null 2\>\&1
configure:8095: $? = 0
configure:8107: result: no
configure:8115: checking dynamic linker characteristics
configure:8681: result: GNU/Linux ld.so
configure:8685: checking how to hardcode library paths into programs
configure:8710: result: immediate
configure:8724: checking whether stripping libraries is possible
configure:8729: result: yes
configure:9552: checking if libtool supports shared libraries
configure:9554: result: yes
configure:9557: checking whether to build shared libraries
configure:9578: result: yes
configure:9581: checking whether to build static libraries
configure:9585: result: yes
configure:9677: creating libtool
configure:10255: checking for ld used by g++
configure:10322: result: /usr/bin/ld
configure:10331: checking if the linker (/usr/bin/ld) is GNU ld
configure:10346: result: yes
configure:10397: checking whether the g++ linker (/usr/bin/ld) supports shared libraries
configure:11275: result: yes
configure:11293: g++ -c -g -O2  conftest.cpp >&5
configure:11296: $? = 0
configure:11406: checking for g++ option to produce PIC
configure:11674: result: -fPIC
configure:11682: checking if g++ PIC flag -fPIC works
configure:11700: g++ -c -g -O2  -fPIC -DPIC conftest.cpp >&5
configure:11704: $? = 0
configure:11717: result: yes
configure:11741: checking if g++ supports -c -o file.o
configure:11762: g++ -c -g -O2  -o out/conftest2.o conftest.cpp >&5
configure:11766: $? = 0
configure:11788: result: yes
configure:11814: checking whether the g++ linker (/usr/bin/ld) supports shared libraries
configure:11842: result: yes
configure:11913: checking dynamic linker characteristics
configure:12479: result: GNU/Linux ld.so
configure:12483: checking how to hardcode library paths into programs
configure:12508: result: immediate
configure:12522: checking whether stripping libraries is possible
configure:12527: result: yes
configure:20070: checking for a BSD-compatible install
configure:20125: result: /usr/bin/install -c
configure:20136: checking whether ln -s works
configure:20140: result: yes
configure:20195: checking for kaffe
configure:20228: result: no
configure:20195: checking for java
configure:20213: found /usr/lib/jvm/java-1.5.0-sun/bin/java
configure:20225: result: /usr/lib/jvm/java-1.5.0-sun/bin/java
configure:20286: checking for dlltool
configure:20312: result: dlltool
configure:20365: checking for gcj
configure:20394: result: no
configure:20405: checking for javacc
configure:20434: result: no
configure:20443: checking for HtmlConverter
configure:20461: found /usr/lib/jvm/java-1.5.0-sun/bin/HtmlConverter
configure:20473: result: /usr/lib/jvm/java-1.5.0-sun/bin/HtmlConverter
configure:20531: checking for jar
configure:20549: found /usr/lib/jvm/java-1.5.0-sun/bin/jar
configure:20561: result: /usr/lib/jvm/java-1.5.0-sun/bin/jar
configure:20623: checking for gcj-wrapper
configure:20656: result: no
configure:20623: checking for gcj
configure:20656: result: no
configure:20623: checking for guavac
configure:20656: result: no
configure:20623: checking for jikes
configure:20656: result: no
configure:20623: checking for javac
configure:20641: found /usr/lib/jvm/java-1.5.0-sun/bin/javac
configure:20653: result: /usr/lib/jvm/java-1.5.0-sun/bin/javac
configure:20668: checking if /usr/lib/jvm/java-1.5.0-sun/bin/javac works
configure:20682: /usr/lib/jvm/java-1.5.0-sun/bin/javac  Test.java
configure:20685: $? = 0
configure:20698: result: yes
configure:20753: checking for javah
configure:20771: found /usr/lib/jvm/java-1.5.0-sun/bin/javah
configure:20783: result: /usr/lib/jvm/java-1.5.0-sun/bin/javah
configure:20804: gcc -E  conftest.c
conftest.c:25:17: error: jni.h: No such file or directory
configure:20810: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| #include <jni.h>
configure:20840: gcc -E  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux conftest.c
configure:20846: $? = 0
configure:20918: checking for jarsigner
configure:20936: found /usr/lib/jvm/java-1.5.0-sun/bin/jarsigner
configure:20948: result: /usr/lib/jvm/java-1.5.0-sun/bin/jarsigner
configure:21012: checking for javadoc
configure:21030: found /usr/lib/jvm/java-1.5.0-sun/bin/javadoc
configure:21042: result: /usr/lib/jvm/java-1.5.0-sun/bin/javadoc
configure:21070: checking for /usr/lib/jvm/java-1.5.0-sun/bin/javac
configure:21101: result: /usr/lib/jvm/java-1.5.0-sun/bin/javac
configure:21673: checking for the pthreads library -lpthreads
configure:21711: gcc -o conftest -g -O2   -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -L/usr/lib conftest.c -lpthreads  >&5
/usr/bin/ld: cannot find -lpthreads
collect2: ld returned 1 exit status
configure:21717: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| #include <pthread.h>
| int
| main ()
| {
| pthread_t th; pthread_join(th, 0);
|                      pthread_attr_init(0); pthread_cleanup_push(0, 0);
|                      pthread_create(0,0,0,0); pthread_cleanup_pop(0);
|   ;
|   return 0;
| }
configure:21743: result: no
configure:21620: checking whether pthreads work without any flags
configure:21711: gcc -o conftest -g -O2   -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -L/usr/lib conftest.c   >&5
/tmp/ccUX7U6h.o: In function `main':
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:29: undefined reference to `pthread_join'
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:30: undefined reference to `pthread_cleanup_push'
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:31: undefined reference to `pthread_create'
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:31: undefined reference to `pthread_cleanup_pop'
collect2: ld returned 1 exit status
configure:21717: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| #include <pthread.h>
| int
| main ()
| {
| pthread_t th; pthread_join(th, 0);
|                      pthread_attr_init(0); pthread_cleanup_push(0, 0);
|                      pthread_create(0,0,0,0); pthread_cleanup_pop(0);
|   ;
|   return 0;
| }
configure:21743: result: no
configure:21625: checking whether pthreads work with -Kthread
configure:21711: gcc -o conftest -g -O2 -Kthread  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -L/usr/lib conftest.c   >&5
gcc: unrecognized option '-Kthread'
/tmp/cca4CDtB.o: In function `main':
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:29: undefined reference to `pthread_join'
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:30: undefined reference to `pthread_cleanup_push'
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:31: undefined reference to `pthread_create'
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:31: undefined reference to `pthread_cleanup_pop'
collect2: ld returned 1 exit status
configure:21717: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| #include <pthread.h>
| int
| main ()
| {
| pthread_t th; pthread_join(th, 0);
|                      pthread_attr_init(0); pthread_cleanup_push(0, 0);
|                      pthread_create(0,0,0,0); pthread_cleanup_pop(0);
|   ;
|   return 0;
| }
configure:21743: result: no
configure:21625: checking whether pthreads work with -kthread
configure:21711: gcc -o conftest -g -O2 -kthread  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -L/usr/lib conftest.c   >&5
gcc: unrecognized option '-kthread'
/tmp/cca7p573.o: In function `main':
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:29: undefined reference to `pthread_join'
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:30: undefined reference to `pthread_cleanup_push'
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:31: undefined reference to `pthread_create'
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:31: undefined reference to `pthread_cleanup_pop'
collect2: ld returned 1 exit status
configure:21717: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| #include <pthread.h>
| int
| main ()
| {
| pthread_t th; pthread_join(th, 0);
|                      pthread_attr_init(0); pthread_cleanup_push(0, 0);
|                      pthread_create(0,0,0,0); pthread_cleanup_pop(0);
|   ;
|   return 0;
| }
configure:21743: result: no

...

```

---

### Post by Loprete on 2007-06-12
Log part 2:

```
configure:21673: checking for the pthreads library -llthread
configure:21711: gcc -o conftest -g -O2   -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -L/usr/lib conftest.c -llthread  >&5
/usr/bin/ld: cannot find -llthread
collect2: ld returned 1 exit status
configure:21717: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| #include <pthread.h>
| int
| main ()
| {
| pthread_t th; pthread_join(th, 0);
|                      pthread_attr_init(0); pthread_cleanup_push(0, 0);
|                      pthread_create(0,0,0,0); pthread_cleanup_pop(0);
|   ;
|   return 0;
| }
configure:21743: result: no
configure:21625: checking whether pthreads work with -pthread
configure:21711: gcc -o conftest -g -O2 -pthread  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -L/usr/lib conftest.c   >&5
configure:21717: $? = 0
configure:21720: test -z 			 || test ! -s conftest.err
configure:21723: $? = 0
configure:21726: test -s conftest
configure:21729: $? = 0
configure:21743: result: yes
configure:21763: checking for joinable pthread attribute
configure:21781: gcc -o conftest -g -O2 -pthread  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -L/usr/lib conftest.c   >&5
configure:21787: $? = 0
configure:21790: test -z 			 || test ! -s conftest.err
configure:21793: $? = 0
configure:21796: test -s conftest
configure:21799: $? = 0
configure:21864: result: PTHREAD_CREATE_JOINABLE
configure:21871: checking if more special flags are required for pthreads
configure:21878: result: no
configure:21890: checking for cc_r
configure:21917: result: gcc
configure:21957: checking for log10 in -lm
configure:21987: gcc -o conftest -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread -L/usr/lib conftest.c -lm    -lpthread >&5
conftest.c:32: warning: conflicting types for built-in function 'log10'
configure:21993: $? = 0
configure:21996: test -z 			 || test ! -s conftest.err
configure:21999: $? = 0
configure:22002: test -s conftest
configure:22005: $? = 0
configure:22018: result: yes
configure:22033: checking for speex_encoder_init in -lspeex
configure:22063: gcc -o conftest -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread -L/usr/lib conftest.c -lspeex  -Wl,-Bdynamic -lm   -lpthread >&5
/usr/bin/ld: cannot find -lspeex
collect2: ld returned 1 exit status
configure:22069: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| #define HAVE_LIBM 1
| /* end confdefs.h.  */
| 
| /* Override any gcc2 internal prototype to avoid an error.  */
| #ifdef __cplusplus
| extern "C"
| #endif
| /* We use char because int might match the return type of a gcc2
|    builtin and then its argument prototype would still apply.  */
| char speex_encoder_init ();
| int
| main ()
| {
| speex_encoder_init ();
|   ;
|   return 0;
| }
configure:22094: result: no
configure:22106: checking for gsm_create in -lgsm
configure:22136: gcc -o conftest -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread -L/usr/lib conftest.c -lgsm  -Wl,-Bdynamic -lm   -lpthread >&5
configure:22142: $? = 0
configure:22145: test -z 			 || test ! -s conftest.err
configure:22148: $? = 0
configure:22151: test -s conftest
configure:22154: $? = 0
configure:22167: result: yes
configure:22179: checking for Pa_Initialize in -lportaudio
configure:22209: gcc -o conftest -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread -L/usr/lib conftest.c -lportaudio  -lgsm -Wl,-Bdynamic -lm   -lpthread >&5
/usr/bin/ld: warning: libpthread.so.0, needed by /usr/lib/libportaudio.so, may conflict with libpthread.so.20
/usr/bin/ld: warning: libpthread.so.0, needed by /usr/lib/libportaudio.so, may conflict with libpthread.so.20
configure:22215: $? = 0
configure:22218: test -z 			 || test ! -s conftest.err
configure:22221: $? = 0
configure:22224: test -s conftest
configure:22227: $? = 0
configure:22240: result: yes
configure:22252: checking for iaxc_initialize in -liaxclient
configure:22282: gcc -o conftest -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread -L/usr/lib conftest.c -liaxclient  -lportaudio -lgsm -Wl,-Bdynamic -lm   -lpthread >&5
/usr/bin/ld: warning: libpthread.so.0, needed by /usr/lib/libportaudio.so, may conflict with libpthread.so.20
/usr/bin/ld: warning: libpthread.so.0, needed by /usr/lib/libportaudio.so, may conflict with libpthread.so.20
/usr/lib/libiaxclient.a(audio_encode.o): In function `iaxc_set_speex_filters':
(.text+0x3a7): undefined reference to `speex_preprocess_ctl'
/usr/lib/libiaxclient.a(audio_encode.o): In function `iaxc_set_speex_filters':
(.text+0x3cd): undefined reference to `speex_preprocess_ctl'
/usr/lib/libiaxclient.a(audio_encode.o): In function `iaxc_set_speex_filters':
(.text+0x3f1): undefined reference to `speex_preprocess_ctl'
/usr/lib/libiaxclient.a(audio_encode.o): In function `iaxc_set_speex_filters':
(.text+0x411): undefined reference to `speex_preprocess_ctl'
/usr/lib/libiaxclient.a(audio_encode.o): In function `iaxc_set_speex_filters':
(.text+0x431): undefined reference to `speex_preprocess_ctl'
/usr/lib/libiaxclient.a(audio_encode.o): In function `iaxc_input_postprocess':
(.text+0x466): undefined reference to `speex_preprocess_state_destroy'
/usr/lib/libiaxclient.a(audio_encode.o): In function `iaxc_input_postprocess':
(.text+0x472): undefined reference to `speex_preprocess_state_init'
/usr/lib/libiaxclient.a(audio_encode.o): In function `iaxc_input_postprocess':
(.text+0x4d3): undefined reference to `speex_preprocess'
/usr/lib/libiaxclient.a(audio_portaudio.o): In function `iaxc_echo_can':
(.text+0xa12): undefined reference to `speex_echo_state_destroy'
/usr/lib/libiaxclient.a(audio_portaudio.o): In function `iaxc_echo_can':
(.text+0xac8): undefined reference to `speex_echo_cancel'
/usr/lib/libiaxclient.a(audio_portaudio.o): In function `iaxc_echo_can':
(.text+0xb35): undefined reference to `speex_echo_state_init'
/usr/lib/libiaxclient.a(codec_speex.o): In function `iaxc_audio_codec_speex_new':
(.text+0xca): undefined reference to `speex_encoder_init'
/usr/lib/libiaxclient.a(codec_speex.o): In function `iaxc_audio_codec_speex_new':
(.text+0xd7): undefined reference to `speex_decoder_init'
/usr/lib/libiaxclient.a(codec_speex.o): In function `iaxc_audio_codec_speex_new':
(.text+0xed): undefined reference to `speex_bits_init'
/usr/lib/libiaxclient.a(codec_speex.o): In function `iaxc_audio_codec_speex_new':
(.text+0xfb): undefined reference to `speex_bits_init'
/usr/lib/libiaxclient.a(codec_speex.o): In function `iaxc_audio_codec_speex_new':
(.text+0x106): undefined reference to `speex_bits_reset'
/usr/lib/libiaxclient.a(codec_speex.o): In function `iaxc_audio_codec_speex_new':
(.text+0x10e): undefined reference to `speex_bits_reset'
/usr/lib/libiaxclient.a(codec_speex.o): In function `iaxc_audio_codec_speex_new':
(.text+0x12a): undefined reference to `speex_decoder_ctl'
/usr/lib/libiaxclient.a(codec_speex.o): In function `iaxc_audio_codec_speex_new':
(.text+0x149): undefined reference to `speex_encoder_ctl'
/usr/lib/libiaxclient.a(codec_speex.o): In function `iaxc_audio_codec_speex_new':
(.text+0x18a): undefined reference to `speex_encoder_ctl'
/usr/lib/libiaxclient.a(codec_speex.o): In function `iaxc_audio_codec_speex_new':
(.text+0x1b4): undefined reference to `speex_encoder_ctl'
/usr/lib/libiaxclient.a(codec_speex.o): In function `iaxc_audio_codec_speex_new':
(.text+0x1ef): undefined reference to `speex_encoder_ctl'
/usr/lib/libiaxclient.a(codec_speex.o): In function `iaxc_audio_codec_speex_new':
(.text+0x20e): undefined reference to `speex_encoder_ctl'
/usr/lib/libiaxclient.a(codec_speex.o):(.text+0x2c7): more undefined references to `speex_encoder_ctl' follow
/usr/lib/libiaxclient.a(codec_speex.o): In function `iaxc_audio_codec_speex_new':
(.text+0x313): undefined reference to `speex_nb_mode'
/usr/lib/libiaxclient.a(codec_speex.o): In function `destroy':
(.text+0x33b): undefined reference to `speex_bits_destroy'
/usr/lib/libiaxclient.a(codec_speex.o): In function `destroy':
(.text+0x346): undefined reference to `speex_bits_destroy'
/usr/lib/libiaxclient.a(codec_speex.o): In function `destroy':
(.text+0x350): undefined reference to `speex_encoder_destroy'
/usr/lib/libiaxclient.a(codec_speex.o): In function `destroy':
(.text+0x35a): undefined reference to `speex_decoder_destroy'
/usr/lib/libiaxclient.a(codec_speex.o): In function `decode':
(.text+0x3b9): undefined reference to `speex_decode_int'
/usr/lib/libiaxclient.a(codec_speex.o): In function `decode':
(.text+0x3e1): undefined reference to `speex_bits_read_from'
/usr/lib/libiaxclient.a(codec_speex.o): In function `decode':
(.text+0x3f2): undefined reference to `speex_bits_remaining'
/usr/lib/libiaxclient.a(codec_speex.o): In function `decode':
(.text+0x3fa): undefined reference to `speex_bits_remaining'
/usr/lib/libiaxclient.a(codec_speex.o): In function `decode':
(.text+0x41a): undefined reference to `speex_decode_int'
/usr/lib/libiaxclient.a(codec_speex.o): In function `decode':
(.text+0x43b): undefined reference to `speex_bits_remaining'
/usr/lib/libiaxclient.a(codec_speex.o): In function `decode':
(.text+0x458): undefined reference to `speex_bits_remaining'
/usr/lib/libiaxclient.a(codec_speex.o): In function `decode':
(.text+0x479): undefined reference to `speex_bits_advance'
/usr/lib/libiaxclient.a(codec_speex.o): In function `encode':
(.text+0x4dd): undefined reference to `speex_bits_reset'
/usr/lib/libiaxclient.a(codec_speex.o): In function `encode':
(.text+0x4ef): undefined reference to `speex_encode_int'
/usr/lib/libiaxclient.a(codec_speex.o): In function `encode':
(.text+0x50d): undefined reference to `speex_bits_pack'
/usr/lib/libiaxclient.a(codec_speex.o): In function `encode':
(.text+0x525): undefined reference to `speex_bits_write'
/usr/lib/libiaxclient.a(codec_speex.o): In function `encode':
(.text+0x559): undefined reference to `speex_bits_reset'
/usr/lib/libiaxclient.a(codec_speex.o): In function `encode':
(.text+0x575): undefined reference to `speex_encode_int'
/usr/lib/libiaxclient.a(codec_speex.o): In function `encode':
(.text+0x5a3): undefined reference to `speex_bits_pack'
/usr/lib/libiaxclient.a(codec_speex.o): In function `encode':
(.text+0x5bb): undefined reference to `speex_bits_write'
collect2: ld returned 1 exit status
configure:22288: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| #define HAVE_LIBM 1
| #define HAVE_LIBGSM 1
| #define HAVE_LIBPORTAUDIO 1
| /* end confdefs.h.  */
| 
| /* Override any gcc2 internal prototype to avoid an error.  */
| #ifdef __cplusplus
| extern "C"
| #endif
| /* We use char because int might match the return type of a gcc2
|    builtin and then its argument prototype would still apply.  */
| char iaxc_initialize ();
| int
| main ()
| {
| iaxc_initialize ();
|   ;
|   return 0;
| }
configure:22313: result: no
configure:22328: checking for ANSI C header files
configure:22483: result: yes
configure:22493: checking whether time.h and sys/time.h may both be included
configure:22518: gcc -c -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread conftest.c >&5
configure:22524: $? = 0
configure:22527: test -z 			 || test ! -s conftest.err
configure:22530: $? = 0
configure:22533: test -s conftest.o
configure:22536: $? = 0
configure:22547: result: yes
configure:22569: checking for inttypes.h
configure:22574: result: yes
configure:22569: checking for memory.h
configure:22574: result: yes
configure:22569: checking for stdlib.h
configure:22574: result: yes
configure:22569: checking for string.h
configure:22574: result: yes
configure:22569: checking for strings.h
configure:22574: result: yes
configure:22578: checking sys/time.h usability
configure:22590: gcc -c -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread conftest.c >&5
configure:22596: $? = 0
configure:22599: test -z 			 || test ! -s conftest.err
configure:22602: $? = 0
configure:22605: test -s conftest.o
configure:22608: $? = 0
configure:22618: result: yes
configure:22622: checking sys/time.h presence
configure:22632: gcc -E  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread conftest.c
configure:22638: $? = 0
configure:22658: result: yes
configure:22693: checking for sys/time.h
configure:22700: result: yes
configure:22578: checking pthread.h usability
configure:22590: gcc -c -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread conftest.c >&5
In file included from conftest.c:70:
/usr/include/pthread.h:285: error: conflicting types for 'pthread_t'
/usr/include/bits/pthreadtypes.h:36: error: previous declaration of 'pthread_t' was here
/usr/include/pthread.h:286: error: conflicting types for 'pthread_attr_t'
/usr/include/bits/pthreadtypes.h:43: error: previous declaration of 'pthread_attr_t' was here
/usr/include/pthread.h:287: error: conflicting types for 'pthread_key_t'
/usr/include/bits/pthreadtypes.h:109: error: previous declaration of 'pthread_key_t' was here
/usr/include/pthread.h:289: error: conflicting types for 'pthread_mutexattr_t'
/usr/include/bits/pthreadtypes.h:79: error: previous declaration of 'pthread_mutexattr_t' was here
/usr/include/pthread.h:290: error: conflicting types for 'pthread_mutex_t'
/usr/include/bits/pthreadtypes.h:73: error: previous declaration of 'pthread_mutex_t' was here
/usr/include/pthread.h:291: error: conflicting types for 'pthread_condattr_t'
/usr/include/bits/pthreadtypes.h:105: error: previous declaration of 'pthread_condattr_t' was here
/usr/include/pthread.h:292: error: conflicting types for 'pthread_cond_t'
/usr/include/bits/pthreadtypes.h:99: error: previous declaration of 'pthread_cond_t' was here
/usr/include/pthread.h:293: error: conflicting types for 'pthread_rwlockattr_t'
/usr/include/bits/pthreadtypes.h:142: error: previous declaration of 'pthread_rwlockattr_t' was here
/usr/include/pthread.h:294: error: conflicting types for 'pthread_rwlock_t'
/usr/include/bits/pthreadtypes.h:136: error: previous declaration of 'pthread_rwlock_t' was here
configure:22596: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| #define HAVE_LIBM 1
| #define HAVE_LIBGSM 1
| #define HAVE_LIBPORTAUDIO 1
| #define STDC_HEADERS 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_SYS_TIME_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #if HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #if HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #if STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # if HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #if HAVE_STRING_H
| # if !STDC_HEADERS && HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #if HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #if HAVE_INTTYPES_H
| # include <inttypes.h>
| #else
| # if HAVE_STDINT_H
| #  include <stdint.h>
| # endif
| #endif
| #if HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <pthread.h>
configure:22618: result: no
configure:22622: checking pthread.h presence
configure:22632: gcc -E  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread conftest.c
configure:22638: $? = 0
configure:22658: result: yes
configure:22671: WARNING: pthread.h: present but cannot be compiled
configure:22673: WARNING: pthread.h:     check for missing prerequisite headers?
configure:22675: WARNING: pthread.h: see the Autoconf documentation
configure:22677: WARNING: pthread.h:     section "Present But Cannot Be Compiled"
configure:22679: WARNING: pthread.h: proceeding with the preprocessor's result
configure:22681: WARNING: pthread.h: in the future, the compiler will take precedence
configure:22693: checking for pthread.h
configure:22700: result: yes
configure:22578: checking iaxclient.h usability
configure:22590: gcc -c -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread conftest.c >&5
configure:22596: $? = 0
configure:22599: test -z 			 || test ! -s conftest.err
configure:22602: $? = 0
configure:22605: test -s conftest.o
configure:22608: $? = 0
configure:22618: result: yes
configure:22622: checking iaxclient.h presence
configure:22632: gcc -E  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread conftest.c
configure:22638: $? = 0
configure:22658: result: yes
configure:22693: checking for iaxclient.h
configure:22700: result: yes
configure:22729: checking jni.h usability
configure:22741: gcc -c -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread -I/usr/lib/jvm/java-1.5.0-sun/include/ conftest.c >&5
configure:22747: $? = 0
configure:22750: test -z 			 || test ! -s conftest.err
configure:22753: $? = 0
configure:22756: test -s conftest.o
configure:22759: $? = 0
configure:22769: result: yes
configure:22773: checking jni.h presence
configure:22783: gcc -E  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread -I/usr/lib/jvm/java-1.5.0-sun/include/ conftest.c
configure:22789: $? = 0
configure:22809: result: yes
configure:22844: checking for jni.h
configure:22851: result: yes
configure:22864: checking for an ANSI C-conforming const
configure:22931: gcc -c -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread -I/usr/lib/jvm/java-1.5.0-sun/include/ conftest.c >&5
configure:22937: $? = 0
configure:22940: test -z 			 || test ! -s conftest.err
configure:22943: $? = 0
configure:22946: test -s conftest.o
configure:22949: $? = 0
configure:22960: result: yes
configure:22976: checking for memset
configure:23033: gcc -o conftest -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread -I/usr/lib/jvm/java-1.5.0-sun/include/ -L/usr/lib conftest.c -Wl,-Bstatic -lportaudio -lgsm -Wl,-Bdynamic -lm   -lpthread >&5
conftest.c:62: warning: conflicting types for built-in function 'memset'
configure:23039: $? = 0
configure:23042: test -z 			 || test ! -s conftest.err
configure:23045: $? = 0
configure:23048: test -s conftest
configure:23051: $? = 0
configure:23063: result: yes
configure:23078: checking for ptw32_processInitialize
configure:23135: gcc -o conftest -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread -I/usr/lib/jvm/java-1.5.0-sun/include/ -L/usr/lib conftest.c -Wl,-Bstatic -lportaudio -lgsm -Wl,-Bdynamic -lm   -lpthread >&5
/tmp/ccMSatCB.o: In function `main':
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:78: undefined reference to `ptw32_processInitialize'
/tmp/ccMSatCB.o:(.data+0x0): undefined reference to `ptw32_processInitialize'
collect2: ld returned 1 exit status
configure:23141: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| #define HAVE_LIBM 1
| #define HAVE_LIBGSM 1
| #define HAVE_LIBPORTAUDIO 1
| #define STDC_HEADERS 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_SYS_TIME_H 1
| #define HAVE_PTHREAD_H 1
| #define HAVE_IAXCLIENT_H 1
| #define HAVE_MEMSET 1
| /* end confdefs.h.  */
| /* Define ptw32_processInitialize to an innocuous variant, in case <limits.h> declares ptw32_processInitialize.
|    For example, HP-UX 11i <limits.h> declares gettimeofday.  */
| #define ptw32_processInitialize innocuous_ptw32_processInitialize
| 
| /* System header to define __stub macros and hopefully few prototypes,
|     which can conflict with char ptw32_processInitialize (); below.
|     Prefer <limits.h> to <assert.h> if __STDC__ is defined, since
|     <limits.h> exists even on freestanding compilers.  */
| 
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 
| #undef ptw32_processInitialize
| 
| /* Override any gcc2 internal prototype to avoid an error.  */
| #ifdef __cplusplus
| extern "C"
| {
| #endif
| /* We use char because int might match the return type of a gcc2
|    builtin and then its argument prototype would still apply.  */
| char ptw32_processInitialize ();
| /* The GNU C library defines this for functions which it implements
|     to always fail with ENOSYS.  Some functions are actually named
|     something starting with __ and the normal name is an alias.  */
| #if defined (__stub_ptw32_processInitialize) || defined (__stub___ptw32_processInitialize)
| choke me
| #else
| char (*f) () = ptw32_processInitialize;
| #endif
| #ifdef __cplusplus
| }
| #endif
| 
| int
| main ()
| {
| return f != ptw32_processInitialize;
|   ;
|   return 0;
| }
configure:23165: result: no
configure:23078: checking for ptw32_processTerminate
configure:23135: gcc -o conftest -g -O2  -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread -I/usr/lib/jvm/java-1.5.0-sun/include/ -L/usr/lib conftest.c -Wl,-Bstatic -lportaudio -lgsm -Wl,-Bdynamic -lm   -lpthread >&5
/tmp/ccGBrTgY.o: In function `main':
/home/sctl/jiaxclient/jiaxclient-0.0.6/conftest.c:78: undefined reference to `ptw32_processTerminate'
/tmp/ccGBrTgY.o:(.data+0x0): undefined reference to `ptw32_processTerminate'
collect2: ld returned 1 exit status
configure:23141: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "jiaxclient"
| #define PACKAGE_TARNAME "jiaxclient"
| #define PACKAGE_VERSION "0.0.6"
| #define PACKAGE_STRING "jiaxclient 0.0.6"
| #define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
| #define PACKAGE "jiaxclient"
| #define VERSION "0.0.6"
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| #define HAVE_LIBM 1
| #define HAVE_LIBGSM 1
| #define HAVE_LIBPORTAUDIO 1
| #define STDC_HEADERS 1
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_SYS_TIME_H 1
| #define HAVE_PTHREAD_H 1
| #define HAVE_IAXCLIENT_H 1
| #define HAVE_MEMSET 1
| /* end confdefs.h.  */
| /* Define ptw32_processTerminate to an innocuous variant, in case <limits.h> declares ptw32_processTerminate.
|    For example, HP-UX 11i <limits.h> declares gettimeofday.  */
| #define ptw32_processTerminate innocuous_ptw32_processTerminate
| 
| /* System header to define __stub macros and hopefully few prototypes,
|     which can conflict with char ptw32_processTerminate (); below.
|     Prefer <limits.h> to <assert.h> if __STDC__ is defined, since
|     <limits.h> exists even on freestanding compilers.  */
| 
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 
| #undef ptw32_processTerminate
| 
| /* Override any gcc2 internal prototype to avoid an error.  */
| #ifdef __cplusplus
| extern "C"
| {
| #endif
| /* We use char because int might match the return type of a gcc2
|    builtin and then its argument prototype would still apply.  */
| char ptw32_processTerminate ();
| /* The GNU C library defines this for functions which it implements
|     to always fail with ENOSYS.  Some functions are actually named
|     something starting with __ and the normal name is an alias.  */
| #if defined (__stub_ptw32_processTerminate) || defined (__stub___ptw32_processTerminate)
| choke me
| #else
| char (*f) () = ptw32_processTerminate;
| #endif
| #ifdef __cplusplus
| }
| #endif
| 
| int
| main ()
| {
| return f != ptw32_processTerminate;
|   ;
|   return 0;
| }
configure:23165: result: no

configure:23339: creating ./config.status

## ---------------------- ##
## Running config.status. ##
## ---------------------- ##

This file was extended by jiaxclient config.status 0.0.6, which was
generated by GNU Autoconf 2.59.  Invocation command line was

  CONFIG_FILES    = 
  CONFIG_HEADERS  = 
  CONFIG_LINKS    = 
  CONFIG_COMMANDS = 
  $ ./config.status 

on sctl-desktop

config.status:799: creating Makefile
config.status:799: creating utils/Makefile
config.status:799: creating jni/Makefile
config.status:799: creating doc/Makefile
config.status:799: creating ext/Makefile
config.status:799: creating inifile/Makefile
config.status:799: creating src/Makefile
config.status:865: creating config.h
config.status:1001: config.h is unchanged
config.status:1181: executing depfiles commands

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnu
ac_cv_build_alias=i686-pc-linux-gnu
ac_cv_c_compiler_gnu=yes
ac_cv_c_const=yes
ac_cv_cxx_compiler_gnu=yes
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_DLLTOOL_set=
ac_cv_env_DLLTOOL_value=
ac_cv_env_F77_set=
ac_cv_env_F77_value=
ac_cv_env_FFLAGS_set=
ac_cv_env_FFLAGS_value=
ac_cv_env_GCJ_set=
ac_cv_env_GCJ_value=
ac_cv_env_JARSIGNER_set=
ac_cv_env_JARSIGNER_value=
ac_cv_env_JAR_set=
ac_cv_env_JAR_value=
ac_cv_env_JAVACC_set=
ac_cv_env_JAVACC_value=
ac_cv_env_JAVAC_set=
ac_cv_env_JAVAC_value=
ac_cv_env_JAVADOC_set=
ac_cv_env_JAVADOC_value=
ac_cv_env_JAVAH_set=
ac_cv_env_JAVAH_value=
ac_cv_env_JAVA_HOME_set=set
ac_cv_env_JAVA_HOME_value=/usr/lib/jvm/java-1.5.0-sun
ac_cv_env_LDFLAGS_set=set
ac_cv_env_LDFLAGS_value=-L/usr/lib
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_exeext=
ac_cv_f77_compiler_gnu=no
ac_cv_func_memset=yes
ac_cv_func_ptw32_processInitialize=no
ac_cv_func_ptw32_processTerminate=no
ac_cv_header_dlfcn_h=yes
ac_cv_header_iaxclient_h=yes
ac_cv_header_inttypes_h=yes
ac_cv_header_jni_h=yes
ac_cv_header_memory_h=yes
ac_cv_header_pthread_h=yes
ac_cv_header_stdc=yes
ac_cv_header_stdint_h=yes
ac_cv_header_stdlib_h=yes
ac_cv_header_string_h=yes
ac_cv_header_strings_h=yes
ac_cv_header_sys_stat_h=yes
ac_cv_header_sys_time_h=yes
ac_cv_header_sys_types_h=yes
ac_cv_header_time=yes
ac_cv_header_unistd_h=yes
ac_cv_host=i686-pc-linux-gnu
ac_cv_host_alias=i686-pc-linux-gnu
ac_cv_lib_gsm_gsm_create=yes
ac_cv_lib_iaxclient_iaxc_initialize=no
ac_cv_lib_m_log10=yes
ac_cv_lib_portaudio_Pa_Initialize=yes
ac_cv_lib_speex_speex_encoder_init=no
ac_cv_objext=o
ac_cv_path_HTMLCONVERTER=/usr/lib/jvm/java-1.5.0-sun/bin/HtmlConverter
ac_cv_path_JAR=/usr/lib/jvm/java-1.5.0-sun/bin/jar
ac_cv_path_JARSIGNER=/usr/lib/jvm/java-1.5.0-sun/bin/jarsigner
ac_cv_path_JAVA=/usr/lib/jvm/java-1.5.0-sun/bin/java
ac_cv_path_JAVAC=/usr/lib/jvm/java-1.5.0-sun/bin/javac
ac_cv_path_JAVADOC=/usr/lib/jvm/java-1.5.0-sun/bin/javadoc
ac_cv_path_JAVAH=/usr/lib/jvm/java-1.5.0-sun/bin/javah
ac_cv_path__ACJNI_JAVAC=/usr/lib/jvm/java-1.5.0-sun/bin/javac
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=mawk
ac_cv_prog_CPP='gcc -E'
ac_cv_prog_CXXCPP='g++ -E'
ac_cv_prog_PTHREAD_CC=gcc
ac_cv_prog_ac_ct_AR=ar
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_ac_ct_CXX=g++
ac_cv_prog_ac_ct_DLLTOOL=dlltool
ac_cv_prog_ac_ct_RANLIB=ranlib
ac_cv_prog_ac_ct_STRIP=strip
ac_cv_prog_cc_g=yes
ac_cv_prog_cc_stdc=
ac_cv_prog_cxx_g=yes
ac_cv_prog_egrep='grep -E'
ac_cv_prog_f77_g=no
ac_cv_prog_javac_works=yes
ac_cv_prog_make_make_set=yes
am_cv_CC_dependencies_compiler_type=gcc3
am_cv_CXX_dependencies_compiler_type=gcc3
lt_cv_deplibs_check_method=pass_all
lt_cv_file_magic_cmd='$MAGIC_CMD'
lt_cv_file_magic_test_file=
lt_cv_ld_reload_flag=-r
lt_cv_objdir=.libs
lt_cv_path_LD=/usr/bin/ld
lt_cv_path_LDCXX=/usr/bin/ld
lt_cv_path_NM='/usr/bin/nm -B'
lt_cv_path_SED=/bin/sed
lt_cv_prog_compiler_c_o=yes
lt_cv_prog_compiler_c_o_CXX=yes
lt_cv_prog_compiler_rtti_exceptions=no
lt_cv_prog_gnu_ld=yes
lt_cv_prog_gnu_ldcxx=yes
lt_cv_sys_global_symbol_pipe='sed -n -e '\''s/^.*[ 	]\([ABCDGIRSTW][ABCDGIRSTW]*\)[ 	][ 	]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p'\'''
lt_cv_sys_global_symbol_to_c_name_address='sed -n -e '\''s/^: \([^ ]*\) $/  {\"\1\", (lt_ptr) 0},/p'\'' -e '\''s/^[BCDEGRST] \([^ ]*\) \([^ ]*\)$/  {"\2", (lt_ptr) \&\2},/p'\'''
lt_cv_sys_global_symbol_to_cdecl='sed -n -e '\''s/^. .* \(.*\)$/extern int \1;/p'\'''
lt_cv_sys_max_cmd_len=32768
lt_lt_cv_prog_compiler_c_o='"yes"'
lt_lt_cv_prog_compiler_c_o_CXX='"yes"'
lt_lt_cv_sys_global_symbol_pipe='"sed -n -e '\''s/^.*[ 	]\\([ABCDGIRSTW][ABCDGIRSTW]*\\)[ 	][ 	]*\\([_A-Za-z][_A-Za-z0-9]*\\)\$/\\1 \\2 \\2/p'\''"'
lt_lt_cv_sys_global_symbol_to_c_name_address='"sed -n -e '\''s/^: \\([^ ]*\\) \$/  {\\\"\\1\\\", (lt_ptr) 0},/p'\'' -e '\''s/^[BCDEGRST] \\([^ ]*\\) \\([^ ]*\\)\$/  {\"\\2\", (lt_ptr) \\&\\2},/p'\''"'
lt_lt_cv_sys_global_symbol_to_cdecl='"sed -n -e '\''s/^. .* \\(.*\\)\$/extern int \\1;/p'\''"'

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/sctl/jiaxclient/jiaxclient-0.0.6/missing --run aclocal-1.9'
AMDEPBACKSLASH='\'
AMDEP_FALSE='#'
AMDEP_TRUE=''
AMTAR='${SHELL} /home/sctl/jiaxclient/jiaxclient-0.0.6/missing --run tar'
AR='ar'
AS='as'
AUTOCONF='${SHELL} /home/sctl/jiaxclient/jiaxclient-0.0.6/missing --run autoconf'
AUTOHEADER='${SHELL} /home/sctl/jiaxclient/jiaxclient-0.0.6/missing --run autoheader'
AUTOMAKE='${SHELL} /home/sctl/jiaxclient/jiaxclient-0.0.6/missing --run automake-1.9'
AWK='mawk'
CC='gcc'
CCDEPMODE='depmode=gcc3'
CFLAGS='-g -O2'
CPP='gcc -E'
CPPFLAGS=' -I/usr/lib/jvm/java-1.5.0-sun/include -I/usr/lib/jvm/java-1.5.0-sun/include/linux -pthread -I/usr/lib/jvm/java-1.5.0-sun/include/'
CXX='g++'
CXXCPP='g++ -E'
CXXDEPMODE='depmode=gcc3'
CXXFLAGS='-g -O2'
CYGPATH_W='echo'
DEFS='-DHAVE_CONFIG_H'
DEPDIR='.deps'
DLLTOOL='dlltool'
ECHO='echo'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP='grep -E'
EXEEXT=''
EXTRA_LIBS=''
F77=''
FFLAGS=''
GCJ=''
GXX_FALSE='#'
GXX_TRUE=''
HOST_ARCH='x86'
HOST_OS='linux'
HTMLCONVERTER='/usr/lib/jvm/java-1.5.0-sun/bin/HtmlConverter'
HTMLCONVERTER_FALSE='#'
HTMLCONVERTER_TRUE=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='${SHELL} $(install_sh) -c -s'
JAR='/usr/lib/jvm/java-1.5.0-sun/bin/jar'
JARSIGNER='/usr/lib/jvm/java-1.5.0-sun/bin/jarsigner'
JAVA='/usr/lib/jvm/java-1.5.0-sun/bin/java'
JAVAC='/usr/lib/jvm/java-1.5.0-sun/bin/javac'
JAVACC=''
JAVADOC='/usr/lib/jvm/java-1.5.0-sun/bin/javadoc'
JAVAH='/usr/lib/jvm/java-1.5.0-sun/bin/javah'
JAVA_HOME='/usr/lib/jvm/java-1.5.0-sun'
KEYSTORE_ALIAS=''
KEYSTORE_PATH='/home/sctl/.keystore'
LDFLAGS='-L/usr/lib'
LIBOBJS=''
LIBPREFIX_FALSE='#'
LIBPREFIX_TRUE=''
LIBS='-Wl,-Bstatic -lportaudio -lgsm -Wl,-Bdynamic -lm   -lpthread'
LIBTOOL='$(SHELL) $(top_builddir)/libtool'
LN_S='ln -s'
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/sctl/jiaxclient/jiaxclient-0.0.6/missing --run makeinfo'
OBJDUMP='objdump'
OBJEXT='o'
PACKAGE='jiaxclient'
PACKAGE_BUGREPORT='Mikael Magnusson <mikma@users.sourceforge.net>'
PACKAGE_NAME='jiaxclient'
PACKAGE_STRING='jiaxclient 0.0.6'
PACKAGE_TARNAME='jiaxclient'
PACKAGE_VERSION='0.0.6'
PATH_SEPARATOR=':'
PTHREAD_CC='gcc'
PTHREAD_CFLAGS='-pthread'
PTHREAD_DLL=''
PTHREAD_LIBS=''
PTHREAD_PATH=''
RANLIB='ranlib'
SET_MAKE=''
SHELL='/bin/bash'
SHLIB='libjiaxc.so'
SIGNJAR_FALSE=''
SIGNJAR_TRUE='#'
STRIP='strip'
VERSION='0.0.6'
WINDOWS_FALSE=''
WINDOWS_TRUE='#'
_ACJNI_JAVAC='/usr/lib/jvm/java-1.5.0-sun/bin/javac'
ac_ct_AR='ar'
ac_ct_AS=''
ac_ct_CC='gcc'
ac_ct_CXX='g++'
ac_ct_DLLTOOL='dlltool'
ac_ct_F77=''
ac_ct_GCJ=''
ac_ct_OBJDUMP=''
ac_ct_RANLIB='ranlib'
ac_ct_STRIP='strip'
acx_pthread_config=''
am__fastdepCC_FALSE='#'
am__fastdepCC_TRUE=''
am__fastdepCXX_FALSE='#'
am__fastdepCXX_TRUE=''
am__include='include'
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias=''
build_cpu='i686'
build_os='linux-gnu'
build_vendor='pc'
datadir='${prefix}/share'
exec_prefix='${prefix}'
host='i686-pc-linux-gnu'
host_alias=''
host_cpu='i686'
host_os='linux-gnu'
host_vendor='pc'
includedir='${prefix}/include'
infodir='${prefix}/info'
install_sh='/home/sctl/jiaxclient/jiaxclient-0.0.6/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
mkdir_p='mkdir -p --'
oldincludedir='/usr/include'
prefix='/usr/local'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define HAVE_DLFCN_H 1
#define HAVE_IAXCLIENT_H 1
#define HAVE_INTTYPES_H 1
#define HAVE_INTTYPES_H 1
#define HAVE_LIBGSM 1
#define HAVE_LIBM 1
#define HAVE_LIBPORTAUDIO 1
#define HAVE_MEMORY_H 1
#define HAVE_MEMORY_H 1
#define HAVE_MEMSET 1
#define HAVE_PTHREAD_H 1
#define HAVE_STDINT_H 1
#define HAVE_STDLIB_H 1
#define HAVE_STDLIB_H 1
#define HAVE_STRINGS_H 1
#define HAVE_STRINGS_H 1
#define HAVE_STRING_H 1
#define HAVE_STRING_H 1
#define HAVE_SYS_STAT_H 1
#define HAVE_SYS_TIME_H 1
#define HAVE_SYS_TYPES_H 1
#define HAVE_UNISTD_H 1
#define PACKAGE "jiaxclient"
#define PACKAGE_BUGREPORT "Mikael Magnusson <mikma@users.sourceforge.net>"
#define PACKAGE_NAME "jiaxclient"
#define PACKAGE_STRING "jiaxclient 0.0.6"
#define PACKAGE_TARNAME "jiaxclient"
#define PACKAGE_VERSION "0.0.6"
#define STDC_HEADERS 1
#define STDC_HEADERS 1
#define TIME_WITH_SYS_TIME 1
#define VERSION "0.0.6"
#endif
#ifdef __cplusplus
extern "C" void std::exit (int) throw (); using std::exit;

configure: exit 0

```

---

### Post by Goliath23 on 2007-09-28
I had the same issue on a system that was updated from edgy to feisty and then to gutsy.

a
```

sudo apt-get remove --purge libpthread-dev
```

did the job.

David

---

### Post by lamnk on 2007-10-09
Thank you Goliath23, i removed libpthread20 and libpthread-dev packages and now i can compile linuxdcpp.

---

