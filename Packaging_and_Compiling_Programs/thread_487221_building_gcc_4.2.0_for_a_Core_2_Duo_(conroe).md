---
title: "building gcc 4.2.0 for a Core 2 Duo (conroe)"
date: 2007-06-28
forum: Packaging and Compiling Programs
---

### Post by praxis22 on 2007-06-28
Hi,

I decided that I wanted speed!  :) So having found this:

[https://wiki.ubuntu.com/Maxalt](https://wiki.ubuntu.com/Maxalt)

I figured I'd first have to rebuild gcc, then rebuild my build environment, then things like libc, etc. 

I then took a trip down memory lane looking at the gentoo forums, where I found the usual bunch of tweakers discussing the best build flags, which I judiciously stole, *"standing on the shoulders of giants"* and all that. :)

[http://forums.gentoo.org/viewtopic-t-517629.html](http://forums.gentoo.org/viewtopic-t-517629.html)

So I then had to setup my build environment:
```

sudo apt-get build-essential makeinfo expect flex bison libtool automake autoconf
sudo apt-get remove libpth20 libpth-dev libpthread20 libpthread-dev
```

If you don't remove the GNU Portable thread library Pth, then you'll get pthread.h build errors.

So having downloaded gcc 4.2.0 from a mirror via: [http://gcc.gnu.org/gcc-4.2/](http://gcc.gnu.org/gcc-4.2/)

I then did the following.

First I looked up what the system version of gcc (4.1.2) with:

```

e$ gcc -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

```

Then extracted the 4.20.0 source, (and the 4.2.0 test harness) into a new dir (build)

```

cd build
bunzip2 -c /tmp/gcc-4.2.0.tar.bz2 |tar xvf -
bunzip2 -c /tmp/gcc-testsuite-4.2.0.tar.bz2 |tar xvf -
cd gcc-4.2.0

```

add:
#undef  DRIVER_SELF_SPECS
#define DRIVER_SELF_SPECS "%{m64:%{!mtune:-mtune=x86-64}}"

to:
./gcc/config/i386/biarch64.h
./gcc/config/i386/linux64.h
./gcc/config/i386/x86-64.h

This will generate a lot of warnings during the final compile stage, as with all warnings, provided they don't kill the build, you can ignore them. ;)

**Read the documentation!**  Faq.html in the current directory, and the stuff here: [http://gcc.gnu.org/install/configure.html](http://gcc.gnu.org/install/configure.html)

This tells you to build in a new dir (x64)  in which to run the compile process. Finally I configured the build as follows:

```

cd x64
../configure -v --enable-languages=c,c++,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.2 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --with-gnu-ld --enable-checking=release x86_64-linux-gnu --disable-multilib
```

I took out Fortran as it complained about two libraries that I couldn't be bothered to hunt for, the first time I ran it. If you don't disable multilib, the compile dies as it cant find stubs-32.h, which as a 64 optimised build is pointless. However this does mean you cannot subsequently build 32bit object code. Meh. :)

I then set CFLAGS, and kicked off the make as an optimised bootstrap (3 stage build) process. What this does is it builds a minimal pre-compiler, then it builds the second stage compiler with your optimisation flags, then it changes to the second stage build to create the final, heavily optimised, end product.

```

set CFLAGS="-m64"; export CFLAGS
make BOOT_CFLAGS="-Os -march=nocona -m64 -msse3 -pipe -mfpmath=sse -falign-functions=64 -fforce-addr" bootstrap
```

It should run for an hour or so then say this:

```

(cd .libs && rm -f libgomp.so.1 && ln -s libgomp.so.1.0.0 libgomp.so.1)
(cd .libs && rm -f libgomp.so && ln -s libgomp.so.1.0.0 libgomp.so)
ar rc .libs/libgomp.a  alloc.o barrier.o critical.o env.o error.o iter.o loop.o ordered.o parallel.o sections.o single.o team.o work.o lock.o mutex.o proc.o sem.o bar.o time.o fortran.o
ranlib .libs/libgomp.a
creating libgomp.la
(cd .libs && rm -f libgomp.la && ln -s ../libgomp.la libgomp.la)
true  DO=all multi-do # make
make[4]: Leaving directory `~/build/gcc-4.2.0/x64/x86_64-linux-gnu/libgomp'
make[3]: Leaving directory `~/build/gcc-4.2.0/x64/x86_64-linux-gnu/libgomp'
make[2]: Leaving directory `~/build/gcc-4.2.0/x64/x86_64-linux-gnu/libgomp'
make[1]: Leaving directory `~/build/gcc-4.2.0/x64'

```

At this point it's built.

You can check it thus:

```

./gcc/xgcc -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../configure -v --enable-languages=c,c++,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.2 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --with-gnu-ld --enable-checking=release x86_64-linux-gnu --disable-multilib
Thread model: posix
gcc version 4.2.0

```

Tomorrow, I'll build the test harness and test my new compiler, then, (and only then) will I install it. 

Time for bed, More later :)

---

### Post by praxis22 on 2007-06-29
For the check process I again had a quick check of the documentation in ../gcc/testsuite/README This tells you how to run the test rig and what you'll need. 

I copied over the testsuite to my build dir, though this is actually not necessary, then I installed the packages required:
```

~/build/gcc-4.2.0/x64$ cp -r ../gcc/testsuite/ ./gcc
sudo apt-get install autogen dejagnu

```

Then it was a simple task to actually run the tests, I still had my CFLAGS="-m64" just in case.
```

~/build/gcc-4.2.0/x64$** make check**
make[1]: Entering directory `/build/gcc-4.2.0/x64'
make[2]: Entering directory `/build/gcc-4.2.0/x64/fixincludes'
autogen -T ../../fixincludes/check.tpl ../../fixincludes/inclhack.def
/bin/sh ./check.sh ../../fixincludes/tests/base
Fixed:  testing.h
Fixed:  testing.h
Fixed:  ansi/math.h
Fixed:  ansi/stdlib.h
Fixed:  arch/i960/archI960.h
Fixed:  architecture/ppc/math.h
Fixed:  arpa/inet.h
Fixed:  assert.h
Fixed:  AvailabilityMacros.h
Fixed:  bits/huge_val.h
Fixed:  bsd/libc.h
Fixed:  c_asm.h
Fixed:  com_err.h
Fixed:  ctrl-quotes-def-1.h
Fixed:  ctype.h
Fixed:  curses.h
Fixed:  errno.h
Fixed:  fixinc-test-limits.h
Fixed:  fs/rfs/rf_cache.h
Fixed:  _G_config.h
Fixed:  hsfs/hsfs_spec.h
Fixed:  ia64/sys/getppdp.h
Fixed:  internal/math_core.h
Fixed:  internal/sgimacros.h
Fixed:  internal/wchar_core.h
Fixed:  inttypes.h
Fixed:  io-quotes-def-1.h
Fixed:  iso/math_c99.h
Fixed:  locale.h
Fixed:  machine/cpu.h
Fixed:  mach-o/dyld.h
Fixed:  malloc.h
Fixed:  math.h
Fixed:  netdnet/dnetdb.h
Fixed:  netinet/in.h
Fixed:  netinet/ip.h
Fixed:  obstack.h
Fixed:  pixrect/memvar.h
Fixed:  pthread.h
Fixed:  regex.h
Fixed:  regexp.h
Fixed:  reg_types.h
Fixed:  rpc/auth.h
Fixed:  rpc/rpc.h
Fixed:  rpc/svc.h
Fixed:  rpcsvc/rstat.h
Fixed:  rpcsvc/rusers.h
Fixed:  rpc/xdr.h
Fixed:  sparc/asm_linkage.h
Fixed:  standards.h
Fixed:  stdio.h
Fixed:  stdio_tag.h
Fixed:  stdlib.h
Fixed:  string.h
Fixed:  strings.h
Fixed:  sundev/vuid_event.h
Fixed:  sunwindow/win_lock.h
Fixed:  sym.h
Fixed:  sys/asm.h
Fixed:  sys/cdefs.h
Fixed:  sys/file.h
Fixed:  sys/ioctl.h
Fixed:  sys/limits.h
Fixed:  sys/machine.h
Fixed:  sys/mman.h
Fixed:  sys/pthread.h
Fixed:  sys/regset.h
Fixed:  sys/signal.h
Fixed:  sys/socket.h
Fixed:  sys/spinlock.h
Fixed:  sys/stat.h
Fixed:  sys/time.h
Fixed:  sys/times.h
Fixed:  sys/types.h
Fixed:  sys/ucontext.h
Fixed:  sys/utsname.h
Fixed:  sys/wait.h
Fixed:  testing.h
Fixed:  time.h
Fixed:  tinfo.h
Fixed:  types/vxTypesBase.h
Fixed:  unistd.h
Fixed:  wchar.h
Fixed:  widec.h
Fixed:  X11/ShellP.h
Fixed:  X11/Xmu.h
Fixed:  Xm/BaseClassI.h
Fixed:  Xm/Traversal.h
math.h /build/gcc-4.2.0/fixincludes/tests/base/math.h differ: byte 1538, line 77
*** math.h      2007-06-29 23:27:35.000000000 +0100
--- /build/gcc-4.2.0/fixincludes/tests/base/math.h      2007-02-06 18:12:22.000000000 +0000
***************
*** 74,79 ****
--- 74,80 ----
  
  
  #if defined( MATH_HUGE_VAL_FROM_DBL_MAX_CHECK )
+ 
  #define HUGE_VAL 3.1415e+9 /* really big */
  #endif  /* MATH_HUGE_VAL_FROM_DBL_MAX_CHECK */
  
reg_types.h /build/gcc-4.2.0/fixincludes/tests/base/reg_types.h differ: byte 266, line 12
*** reg_types.h 2007-06-29 23:27:35.000000000 +0100
--- /build/gcc-4.2.0/fixincludes/tests/base/reg_types.h 2004-08-31 10:27:00.000000000 +0100
***************
*** 9,15 ****
  
  
  
! #if defined( OSF_NAMESPACE_A_CHECK )typedef struct {
    int stuff, mo_suff;
  } __regex_t;
  extern __regex_t    re;
--- 9,16 ----
  
  
  
! #if defined( OSF_NAMESPACE_A_CHECK )
! typedef struct {
    int stuff, mo_suff;
  } __regex_t;
  extern __regex_t    re;
sys/stat.h /build/gcc-4.2.0/fixincludes/tests/base/sys/stat.h differ: byte 1338, line 64
*** sys/stat.h  2007-06-29 23:27:35.000000000 +0100
--- /build/gcc-4.2.0/fixincludes/tests/base/sys/stat.h  2004-08-31 10:27:00.000000000 +0100
***************
*** 61,67 ****
  #endif  /* ULTRIX_STAT_CHECK */
  
  
! #if defined( VXWORKS_NEEDS_VXWORKS_CHECK )#include </dev/null> /* ULONG */
  # define      __INCstath <sys/stat.h>
  #include <types/vxTypesOld.h>
  #endif  /* VXWORKS_NEEDS_VXWORKS_CHECK */
--- 61,68 ----
  #endif  /* ULTRIX_STAT_CHECK */
  
  
! #if defined( VXWORKS_NEEDS_VXWORKS_CHECK )
! #include </dev/null> /* ULONG */
  # define      __INCstath <sys/stat.h>
  #include <types/vxTypesOld.h>
  #endif  /* VXWORKS_NEEDS_VXWORKS_CHECK */
time.h /build/gcc-4.2.0/fixincludes/tests/base/time.h differ: byte 375, line 17
*** time.h      2007-06-29 23:27:35.000000000 +0100
--- /build/gcc-4.2.0/fixincludes/tests/base/time.h      2004-08-31 10:27:00.000000000 +0100
***************
*** 14,20 ****
  #endif  /* VXWORKS_NEEDS_VXTYPES_CHECK */
  
  
! #if defined( VXWORKS_TIME_CHECK )#ifndef __gcc_VOIDFUNCPTR_defined
  #ifdef __cplusplus
  typedef void (*__gcc_VOIDFUNCPTR) (...);
  #else
--- 14,21 ----
  #endif  /* VXWORKS_NEEDS_VXTYPES_CHECK */
  
  
! #if defined( VXWORKS_TIME_CHECK )
! #ifndef __gcc_VOIDFUNCPTR_defined
  #ifdef __cplusplus
  typedef void (*__gcc_VOIDFUNCPTR) (...);
  #else

**There were fixinclude test FAILURES**
make[2]: *** [check] Error 1
make[2]: Leaving directory `/build/gcc-4.2.0/x64/fixincludes'
make[1]: *** [check-fixincludes] Error 2
make[1]: Leaving directory `/build/gcc-4.2.0/x64'
make: *** [do-check] Error 2
~/build/gcc-4.2.0/x64$ 
```

As you can see above, the build died because of differences with the header files, however on closer inspection it appears these are only cosmetic. So I simply edited the files listed with vi, (though any editor will do) and made the bottom section look like the top section, the diff excerpts actually give you line numbers, and show you what to look for with the ! & + signs, so it's an easy fix, mostly just concatenating two lines together, and removing one extra one. 

Then I ran make check again, and after waiting a long, long time, it produced the following (condensed)  results:
```

                === gcc Summary ===

# of expected passes            41889
# of expected failures          127
# of unresolved testcases       13
# of untested testcases         28
# of unsupported tests          401
/build/gcc-4.2.0/x64/gcc/xgcc  version 4.2.0

                === g++ Summary ===

# of expected passes            13352
# of unexpected successes       2
# of expected failures          66
# of unsupported tests          104
/build/gcc-4.2.0/x64/gcc/testsuite/g++/../../g++  version 4.2.0

                === objc Summary ===

# of expected passes            1806
# of expected failures          7
# of unsupported tests          24
/build/gcc-4.2.0/x64/gcc/xgcc  version 4.2.0

                === obj-c++ Summary ===

# of expected passes            426
# of unexpected failures        9
# of unresolved testcases       3
# of unsupported tests          13
/build/gcc-4.2.0/x64/gcc/testsuite/obj-c++/../../g++  version 4.2.0

                === libstdc++ Summary ===

# of expected passes            3842
# of unexpected successes       2
# of expected failures          14
# of unsupported tests          316

```

At that point it bombs out for reasons unknown, after completing the libstdc++ testsuite seemingly successfully. However I don't have time to check it tonight, got to go into work tomorrow morning to do a few checks.

---

### Post by steinlee on 2007-11-04
installation successful. But when I typed gcc --v or g++, I still got 
 Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)


It is not 4.2.2. What is the problem?

---

### Post by praxis22 on 2007-11-04
If you're using the version of gcc that comes with Feisty, etc. (which it appears you are) then you'll need to download and compile a later release manually.

---

### Post by steinlee on 2007-11-04
I compiled and installed 4.2.2 with no error messages. 
/usr/bin/gcc-4.2.2 is available. But gcc -v is gcc version 4.1.3. I tried
to use ln to link gcc to gcc-4.2.2 and did not succeed.

---

### Post by jkays94 on 2007-11-14
Did you consider uninstalling your existing gcc version? If not you might want to do that using apt-get, before you install from your compiled source.

---

### Post by jaybombalous on 2007-11-14
```
   ../../gcc/c-decl.c -o c-decl.o
/home/jasin/Desktop/build/gcc-4.2.2/gcc_x64/./prev-gcc/xgcc -B/home/jasin/Desktop/build/gcc-4.2.2/gcc_x64/./prev-gcc/ -B/usr/x86_64-linux-gnu/bin/ -c   -march=athlon64 -O2 -pipe -fomit-frame-pointer -fno-ident -DIN_GCC   -W -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -pedantic -Wno-long-long -Wno-variadic-macros -Wno-overlength-strings -Wold-style-definition -Wmissing-format-attribute    -DHAVE_CONFIG_H -I. -I. -I../../gcc -I../../gcc/. -I../../gcc/../include -I../../gcc/../libcpp/include  -I../../gcc/../libdecnumber -I../libdecnumber    ../../gcc/c-typeck.c -o c-typeck.o
../../gcc/c-typeck.c: In function ‘tagged_types_tu_compatible_p’:
../../gcc/c-typeck.c:1041: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
make[3]: *** [c-typeck.o] Error 1
make[3]: Leaving directory `/home/jasin/Desktop/build/gcc-4.2.2/gcc_x64/gcc'
make[2]: *** [all-stage3-gcc] Error 2
make[2]: Leaving directory `/home/jasin/Desktop/build/gcc-4.2.2/gcc_x64'
make[1]: *** [stage3-bubble] Error 2
make[1]: Leaving directory `/home/jasin/Desktop/build/gcc-4.2.2/gcc_x64'
make: *** [bootstrap] Error 2
```

I almost made it then this. I found a patch, but it was dated for 2004 so the patch didn't work because it wanted me to assume -R (reverse) and I said no, should I say yes?

---

