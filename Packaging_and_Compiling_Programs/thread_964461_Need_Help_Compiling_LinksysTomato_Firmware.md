---
title: "Need Help Compiling Linksys/Tomato Firmware"
date: 2008-10-30
forum: Packaging and Compiling Programs
---

### Post by ff2kracer on 2008-10-30
Total Linux nOOb here. I am hoping to compile some modifications into the Tomato firmware for Linksys routers. The modifications are made and I have followed all of the directions to the letter - including HOURS of searching around looking for what is happening. I have created the symlinks and PATH statements per the direction. When I execute MAKE from the specified directory (either normally or front-ended with SUDO), I get many errors messages, like below:

```
mdh@1330-linux:~/Desktop/tomato/release/src$ sudo make
[sudo] password for mdh: 
make libc
make[1]: Entering directory `/home/mdh/Desktop/tomato/release/src'
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[2]: mipsel-linux-gcc: Command not found
make[2]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc'
find . \( -name \*.o -o -name \*.a -o -name \*.so -o -name core -o -name .\#\* \) -exec rm -f {} \;
make -C test clean
make[3]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test'
make -C  args clean
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/args'
rm -f *.[oa] *~ core arg_test
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/args'
make -C  assert clean
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/assert'
rm -f *.[oa] *~ core assert
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/assert'
make -C  ctype clean
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/ctype'
rm -f *.[oa] *~ core ctype ctype_run
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/ctype'
make -C  ldso clean
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/ldso'
rm -f *.o *.so dltest2 dltest core libhowdy.so dlttest dlttest2
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/ldso'
make -C  pwd_grp clean
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/pwd_grp'
rm -f *.[oa] *~ core test_pwd test_pwd_glibc test_grp test_grp_glibc test_pwd_diff test_grp_diff *.out
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/pwd_grp'
make -C  signal clean
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/signal'
rm -f *.[oa] *~ core signal signal_glibc sigchld sigchld_glibc 
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/signal'
make -C  silly clean
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/silly'
rm -f *.[oa] *~ core hello_source hello hello_glibc tiny
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/silly'
make -C  stdlib clean
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/stdlib'
rm -f *.[oa] *~ core teststrtol teststrtol_glibc teststrtol_diff qsort qsort_glibc qsort_diff teston_exit teston_exit_glibc teston_exit_diff testatexit testatexit_glibc testatexit_diff ptytest *.out
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/stdlib'
make -C  string clean
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/string'
rm -f *.[oa] *~ core string string_glibc testcopy testcopy_glibc  testcopy.gnu.out testcopy.out
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/string'
make -C  unistd clean
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/unistd'
rm -f *.[oa] *~ core fork fork_glibc vfork vfork_glibc getcwd getopt getopt_long preadwrite 
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/unistd'
make -C  crypt clean
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/crypt'
rm -f *.[oa] *~ core crypt_glibc crypt crypt_glibc.out crypt.out md5c-test
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test/crypt'
rm -f *.[oa] *~ core
make[3]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/test'
make -C ldso clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[3]: mipsel-linux-gcc: Command not found
make[3]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/ldso'
set -e ; for d in ldso libdl util ; do make -C $d clean ; done
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/ldso/ldso'
ls: cannot access /*.S: No such file or directory
ls: cannot access /*.S: No such file or directory
ls: cannot access /*.S: No such file or directory
rm -f -f ld-uClibc.so.0*  ldso.o ld-uClibc-0.9.19.so* core *.o *.a *.s *.i ldso.h *~
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/ldso/ldso'
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/ldso/libdl'
rm -f -f .depend libdl.so* libdl-0.9.19.so core *.o *.a *.s *.i tmp_make foo *~
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/ldso/libdl'
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/ldso/util'
rm -f elf_header ldd *.o *~ core ./elf.h *.target
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/ldso/util'
find . -name '*~' | xargs rm -f
make[3]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/ldso'
make -C libc/misc/internals clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[3]: mipsel-linux-gcc: Command not found
make[3]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/misc/internals'
rm -f *.[oa] interp.c *~ core
make[3]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/misc/internals'
make -C libc/misc/wchar clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[3]: mipsel-linux-gcc: Command not found
make[3]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/misc/wchar'
rm -f *.[oa] *~ core iconv.target
make[3]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/misc/wchar'
make -C libc/unistd clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[3]: mipsel-linux-gcc: Command not found
make[3]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/unistd'
rm -f *.[oa] *~ core gen_sysconf sysconf_*.c
make[3]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/unistd'
make -C libc/sysdeps/linux/common clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[3]: mipsel-linux-gcc: Command not found
make[3]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/common'
rm -f *.[oa] *~ core crt[in].* *.S
make[3]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/common'
make -C extra/gcc-uClibc clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[3]: mipsel-linux-gcc: Command not found
make[3]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/extra/gcc-uClibc'
/bin/sh: mipsel-linux-gcc: not found
rm -f gcc-uClibc.h *-uclibc-gcc *-uclibc-ld core
make[3]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/extra/gcc-uClibc'
make -C extra/locale clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[3]: mipsel-linux-gcc: Command not found
make[3]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/extra/locale'
rm -f *.[oa] *~ core
rm -f gen_wc8bit gen_wctype gen_locale gen_ldc gen_collate
rm -f c8tables.h wctables.h locale_tables.h lt_defines.h locale_collate.h
rm -f gen_mmap locale.mmap lmmtolso
rm -f locale_data.c locale_data.o  uClibc_locale_data.h
make[3]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/extra/locale'
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[3]: mipsel-linux-gcc: Command not found
make[3]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux'
make -C  arm clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/arm'
rm -f *.[oa] *~ core
rm -f bits/sysnum.h
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/arm'
make -C  common clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/common'
rm -f *.[oa] *~ core crt[in].* *.S
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/common'
make -C  cris clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/cris'
rm -f *.[oa] *~ core
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/cris'
make -C  h8300 clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/h8300'
rm -f *.[oa] *~ core
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/h8300'
make -C  i386 clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/i386'
rm -f *.[oa] *~ core
rm -f bits/sysnum.h
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/i386'
make -C  m68k clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/m68k'
rm -f *.[oa] *~ core
rm -f bits/sysnum.h
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/m68k'
make -C  mips clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/mips'
rm -f *.[oa] *~ core
rm -f bits/sysnum.h
rm -f ../../../..//include/sgidefs.h
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/mips'
make -C  powerpc clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/powerpc'
rm -f *.[oa] *~ core
rm -f bits/sysnum.h
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/powerpc'
make -C  sh clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/sh'
rm -f *.[oa] *~ core
rm -f bits/sysnum.h
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/sh'
make -C  sparc clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/sparc'
rm -f *.[oa] *~ core
rm -f bits/sysnum.h
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/sparc'
make -C  v850 clean
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[4]: mipsel-linux-gcc: Command not found
make[4]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/v850'
rm -f *.[oa] *~ core
rm -f bits/sysnum.h
make[4]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux/v850'
make[3]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc/libc/sysdeps/linux'
make[2]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc'
/bin/sh: mipsel-linux-gcc: not found
/bin/sh: mipsel-linux-gcc: not found
make[2]: mipsel-linux-gcc: Command not found
make[2]: Entering directory `/home/mdh/Desktop/tomato/tools-src/uClibc'
rm -rf include/bits
mkdir -p include/bits
can't find file extra/Configs/Config.
make[2]: *** [include/bits/uClibc_config.h] Error 1
make[2]: Leaving directory `/home/mdh/Desktop/tomato/tools-src/uClibc'
make[1]: *** [libc] Error 2
make[1]: Leaving directory `/home/mdh/Desktop/tomato/release/src'
make: *** [all] Error 2
mdh@1330-linux:~/Desktop/tomato/release/src$ 

```

Clearly, I simply don't understand something here - but I feel like all the pieces exist. I would sure appreciate any guidance on explaining why this is failing so miserably. Thanks.

---

### Post by HarshReality on 2008-11-01
Your OS x86 or x64?

---

### Post by ff2kracer on 2008-11-01
> **harshreality said:**
> your os x86 or x64?

64

---

### Post by HarshReality on 2008-11-03
> **ff2kracer said:**
> 64

Your error messages seem to be indicating your missing the toolchains needed to complete the compile. I suffer the same issue and have yet to locate them much less get specific direction on how to install them myself.

---

