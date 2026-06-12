---
title: "Problem with GCC"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by japage1964 on 2008-07-16
Hi 

I need to run a c program for my course. IT only runs on Linux and not windows. Hence I spent 4 days trying to install Ubuntu  or debian and fedora and get GCC working.   I installed ubunto on (my PC - intel pent 4 ) using the i386 version on the ubunto iso. I started off installing gutsy (version 7) and upgraded using System -> administration -> update manager

I discovered my program wouldnt run. So I downloaded GCC and tried to do ./configure make and make install. I quickly found that I didnt have GMP and MFPR ( got an error with ./configure in location ~DESKTOP/jacqueline/gcc-4.3.1)
I then installed both GMP and MFPR  on desktop... no joy  so I moved these to ~DESKTOP/Jacqueline/gcc-4.3.1 and tried ./configure them all in each of their folder.

I got error messages

for GCC folder I initially got
checking for correct version of gmp.h ..no
configure: error: Building GCC requires GMP 4.1+ and MPFR 2.3.0+

and trying apt-get install gcc

no usuable m4 in $PATH or /usr/5bin 

mpfr folder checking for gmp.h ... no
configure: error: gmph cant be found or is unusable
in gmp folder I got checking for suitable m4 ... configure: error: no usable m4 $ path in $PATH or /usr/5bin (see config.log for reasons)

Then I noticed that somewhere on the internet they said to use apt-get so I tried and it said i had the most uptodate version

Then I read on the internet that I had to set my $PATH variable
by PATH=$PATH:$HOME/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin/sbin:/bin:usr/games:**~/DESKtop/gcc-4.3.1**

still nothing works and I think I have messed everything up. Advice urgently needed

Thanks in advance for your help

regards

---

### Post by unutbu on 2008-07-16
Instead of compiling gcc from source, perhaps try installing it through the package manager:
```

sudo apt-get install build-essential
```

This will install gcc, g++, make, dpkg-dev.

---

### Post by japage1964 on 2008-07-16
> **unutbu said:**
> Instead of compiling gcc from source, perhaps try installing it through the package manager:
```

sudo apt-get install build-essential
```

This will install gcc, g++, make, dpkg-dev.

Thanks for your help.. I tried that along the way and have just repeated it but it wont let me change anything.

Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jacqueline@jacqueline-desktop:~$ 

I am now using apt-get remove build-essential and will then do apt-get install build-essential

I think if I look at the config.log nothing is set.

jacqueline@jacqueline-desktop:~$ cat config.log
## --------- ##
## Platform. ##
## --------- ##

hostname = jacqueline-desktop
uname -m = i686
uname -r = 2.6.24-19-generic
uname -s = Linux
uname -v = #1 SMP Fri Jul 11 23:41:49 UTC 2008

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
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

configure:1505: checking build system type
configure:1523: result: i686-pc-linux-gnu
configure:1558: checking host system type
configure:1572: result: i686-pc-linux-gnu
configure:1580: checking target system type
configure:1594: result: i686-pc-linux-gnu
configure:1637: checking for a BSD-compatible install
configure:1692: result: /usr/bin/install -c
configure:1703: checking whether ln works
configure:1725: result: yes
configure:1729: checking whether ln -s works
configure:1733: result: yes
configure:2885: checking for gcc
configure:2901: found /usr/bin/gcc
configure:2911: result: gcc
configure:3155: checking for C compiler version
configure:3158: gcc --version </dev/null >&5
gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3161: $? = 0
configure:3163: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --w
ith-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/
usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enab
le-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
configure:3166: $? = 0
configure:3168: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:3171: $? = 1
configure:3194: checking for C compiler default output file name
configure:3197: gcc    conftest.c  >&5
configure:3200: $? = 0
configure:3246: result: a.out
configure:3251: checking whether the C compiler works
configure:3257: ./a.out
configure:3260: $? = 0
configure:3277: result: yes
configure:3284: checking whether we are cross compiling
configure:3286: result: no
configure:3289: checking for suffix of executables
configure:3291: gcc -o conftest    conftest.c  >&5
configure:3294: $? = 0
configure:3319: result: 
configure:3325: checking for suffix of object files
configure:3346: gcc -c   conftest.c >&5
configure:3349: $? = 0
configure:3371: result: o
configure:3375: checking whether we are using the GNU C compiler
configure:3399: gcc -c   conftest.c >&5
configure:3405: $? = 0
configure:3409: test -z 
			 || test ! -s conftest.err
configure:3412: $? = 0
configure:3415: test -s conftest.o
configure:3418: $? = 0
configure:3431: result: yes
configure:3437: checking whether gcc accepts -g
configure:3458: gcc -c -g  conftest.c >&5
configure:3464: $? = 0
configure:3468: test -z 
			 || test ! -s conftest.err
configure:3471: $? = 0
configure:3474: test -s conftest.o
configure:3477: $? = 0
configure:3488: result: yes
configure:3505: checking for gcc option to accept ANSI C
configure:3575: gcc  -c -g -O2  conftest.c >&5
configure:3581: $? = 0
configure:3585: test -z 
			 || test ! -s conftest.err
configure:3588: $? = 0
configure:3591: test -s conftest.o
configure:3594: $? = 0
configure:3612: result: none needed
configure:3630: gcc -c -g -O2  conftest.c >&5
conftest.c:2: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'me'
configure:3636: $? = 1
configure: failed program was:
| #ifndef __cplusplus
|   choke me
| #endif
configure:3821: checking for g++
configure:3837: found /usr/bin/g++
configure:3847: result: g++
configure:3863: checking for C++ compiler version
configure:3866: g++ --version </dev/null >&5
g++ (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3869: $? = 0
configure:3871: g++ -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --w
ith-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/
usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enab
le-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
configure:3874: $? = 0
configure:3876: g++ -V </dev/null >&5
g++: '-V' option must have argument
configure:3879: $? = 1
configure:3882: checking whether we are using the GNU C++ compiler
configure:3906: g++ -c   conftest.cc >&5
configure:3912: $? = 0
configure:3916: test -z 
			 || test ! -s conftest.err
configure:3919: $? = 0
configure:3922: test -s conftest.o
configure:3925: $? = 0
configure:3938: result: yes
configure:3944: checking whether g++ accepts -g
configure:3965: g++ -c -g  conftest.cc >&5
configure:3971: $? = 0
configure:3975: test -z 
			 || test ! -s conftest.err
configure:3978: $? = 0
configure:3981: test -s conftest.o
configure:3984: $? = 0
configure:3995: result: yes
configure:4037: g++ -c -g -O2  conftest.cc >&5
configure:4043: $? = 0
configure:4047: test -z 
			 || test ! -s conftest.err
configure:4050: $? = 0
configure:4053: test -s conftest.o
configure:4056: $? = 0
configure:4082: g++ -c -g -O2  conftest.cc >&5
conftest.cc: In function 'int main()':
conftest.cc:13: error: 'exit' was not declared in this scope
configure:4088: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| exit (42);
|   ;
|   return 0;
| }
configure:4037: g++ -c -g -O2  conftest.cc >&5
conftest.cc:9: error: 'void std::exit(int)' should have been declared inside 'std'
configure:4043: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| extern "C" void std::exit (int) throw (); using std::exit;
| #include <stdlib.h>
| int
| main ()
| {
| exit (42);
|   ;
|   return 0;
| }
configure:4037: g++ -c -g -O2  conftest.cc >&5
conftest.cc:9: error: 'void std::exit(int)' should have been declared inside 'std'
In file included from conftest.cc:10:
/usr/include/stdlib.h:531: error: declaration of 'void std::exit(int) throw ()' throws different exceptions
conftest.cc:9: error: from previous declaration 'void std::exit(int)'
configure:4043: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| extern "C" void std::exit (int); using std::exit;
| #include <stdlib.h>
| int
| main ()
| {
| exit (42);
|   ;
|   return 0;
| }
configure:4037: g++ -c -g -O2  conftest.cc >&5
configure:4043: $? = 0
configure:4047: test -z 
			 || test ! -s conftest.err
configure:4050: $? = 0
configure:4053: test -s conftest.o
configure:4056: $? = 0
configure:4082: g++ -c -g -O2  conftest.cc >&5
configure:4088: $? = 0
configure:4092: test -z 
			 || test ! -s conftest.err
configure:4095: $? = 0
configure:4098: test -s conftest.o
configure:4101: $? = 0
configure:4188: checking for gnatbind
configure:4215: result: no
configure:4268: checking for gnatmake
configure:4295: result: no
configure:4307: checking whether compiler driver understands Ada
configure:4330: result: no
configure:4339: checking how to compare bootstrapped objects
configure:4364: result: cmp --ignore-initial=16 $$f1 $$f2
configure:4484: checking for correct version of gmp.h
configure:4507: gcc -c -g -O2   conftest.c >&5
conftest.c:12:17: error: gmp.h: No such file or directory
conftest.c: In function 'main':
conftest.c:18: error: 'choke' undeclared (first use in this function)
conftest.c:18: error: (Each undeclared identifier is reported only once
conftest.c:18: error: for each function it appears in.)
conftest.c:18: error: expected ';' before 'me'
configure:4513: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #ifdef __cplusplus
| extern "C" void exit (int) throw ();
| #endif
| /* end confdefs.h.  */
| #include "gmp.h"
| int
| main ()
| {
| 
|   #if __GNU_MP_VERSION < 4 || (__GNU_MP_VERSION == 4 && __GNU_MP_VERSION_MINOR < 1)
|   choke me
|   #endif
| 
|   ;
|   return 0;
| }
configure:4534: result: no
configure:4669: error: Building GCC requires GMP 4.1+ and MPFR 2.3.0+.
Try the --with-gmp and/or --with-mpfr options to specify their locations.
Copies of these libraries' source code can be found at their respective
hosting sites as well as at [ftp://gcc.gnu.org/pub/gcc/infrastructure/](ftp://gcc.gnu.org/pub/gcc/infrastructure/).
See also [http://gcc.gnu.org/install/prerequisites.html](http://gcc.gnu.org/install/prerequisites.html) for additional info.
If you obtained GMP and/or MPFR from a vendor distribution package, make
sure that you have installed both the libraries and the header files.
They may be located in separate packages.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnu
ac_cv_build_alias=i686-pc-linux-gnu
ac_cv_c_compiler_gnu=yes
ac_cv_cxx_compiler_gnu=yes
ac_cv_env_AR_FOR_TARGET_set=
ac_cv_env_AR_FOR_TARGET_value=
ac_cv_env_AR_set=
ac_cv_env_AR_value=
ac_cv_env_AS_FOR_TARGET_set=
--More--(62%)
ac_cv_build=i686-pc-linux-gnu
ac_cv_build_alias=i686-pc-linux-gnu
ac_cv_c_compiler_gnu=yes
ac_cv_cxx_compiler_gnu=yes
ac_cv_env_AR_FOR_TARGET_set=
ac_cv_env_AR_FOR_TARGET_value=
ac_cv_env_AR_set=
ac_cv_env_AR_value=
ac_cv_env_AS_FOR_TARGET_set=
ac_cv_env_AS_FOR_TARGET_value=
ac_cv_env_AS_set=
ac_cv_env_AS_value=
ac_cv_env_CC_FOR_TARGET_set=
ac_cv_env_CC_FOR_TARGET_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_FOR_TARGET_set=
ac_cv_env_CXX_FOR_TARGET_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_DLLTOOL_FOR_TARGET_set=
ac_cv_env_DLLTOOL_FOR_TARGET_value=
ac_cv_env_DLLTOOL_set=
ac_cv_env_DLLTOOL_value=
ac_cv_env_GCC_FOR_TARGET_set=
ac_cv_env_GCC_FOR_TARGET_value=
ac_cv_env_GCJ_FOR_TARGET_set=
ac_cv_env_GCJ_FOR_TARGET_value=
ac_cv_env_GFORTRAN_FOR_TARGET_set=
ac_cv_env_GFORTRAN_FOR_TARGET_value=
ac_cv_env_LDFLAGS_set=
--More--(66%)
ac_cv_env_AS_value=
ac_cv_env_CC_FOR_TARGET_set=
ac_cv_env_CC_FOR_TARGET_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_FOR_TARGET_set=
ac_cv_env_CXX_FOR_TARGET_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_DLLTOOL_FOR_TARGET_set=
ac_cv_env_DLLTOOL_FOR_TARGET_value=
ac_cv_env_DLLTOOL_set=
ac_cv_env_DLLTOOL_value=
ac_cv_env_GCC_FOR_TARGET_set=
ac_cv_env_GCC_FOR_TARGET_value=
ac_cv_env_GCJ_FOR_TARGET_set=
ac_cv_env_GCJ_FOR_TARGET_value=
ac_cv_env_GFORTRAN_FOR_TARGET_set=
ac_cv_env_GFORTRAN_FOR_TARGET_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LD_FOR_TARGET_set=
ac_cv_env_LD_FOR_TARGET_value=
ac_cv_env_LD_set=
ac_cv_env_LD_value=
ac_cv_env_LIPO_FOR_TARGET_set=
ac_cv_env_LIPO_FOR_TARGET_value=
ac_cv_env_LIPO_set=
ac_cv_env_LIPO_value=
ac_cv_env_NM_FOR_TARGET_set=
ac_cv_env_NM_FOR_TARGET_value=
ac_cv_env_NM_set=
ac_cv_env_NM_value=
ac_cv_env_OBJCOPY_set=
ac_cv_env_OBJCOPY_value=
ac_cv_env_OBJDUMP_FOR_TARGET_set=
ac_cv_env_OBJDUMP_FOR_TARGET_value=
ac_cv_env_OBJDUMP_set=
ac_cv_env_OBJDUMP_value=
ac_cv_env_RANLIB_FOR_TARGET_set=
ac_cv_env_RANLIB_FOR_TARGET_value=
ac_cv_env_RANLIB_set=
ac_cv_env_RANLIB_value=
ac_cv_env_STRIP_FOR_TARGET_set=
ac_cv_env_STRIP_FOR_TARGET_value=
ac_cv_env_STRIP_set=
ac_cv_env_STRIP_value=
ac_cv_env_WINDMC_FOR_TARGET_set=
ac_cv_env_WINDMC_FOR_TARGET_value=
ac_cv_env_WINDMC_set=
ac_cv_env_WINDMC_value=
ac_cv_env_WINDRES_FOR_TARGET_set=
ac_cv_env_WINDRES_FOR_TARGET_value=
ac_cv_env_WINDRES_set=

---

### Post by nowshining on 2008-07-16
when u have ./configure probs - u need the -dev versions of any programs/libs it asks for.

---

### Post by Chris S. on 2008-07-16
You could try installing the GMP and MPFR libraries via apt-get too.  Try:

```
sudo apt-get install libgmp3-dev libmpfr-dev
```

You should then be able to use both of those with the GCC you get from the build-essential package.  When compiling your program, if it uses the GMP and/or MPFR libraries, be sure to link those with a -lgmp or -lmpfr switch.

---

