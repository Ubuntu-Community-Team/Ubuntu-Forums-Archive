---
title: "Help compiling firmware"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by ff2kracer on 2008-11-01
Tried posting this in the programming section and got no response, so I'll try here. I'm really lost.

Can somebody try to help this noob figure out what is happening below? I am trying to compile Tomato firmware for a Linksys router (although the same thing happens if I just try to compile Linksys's code without the Tomato extensions). When I run make it is unable to find some of the required files. I have followed the instructions regarding setting path & symlinks to the letter and also have tried every variation I can think of with regard to these commands. mipsel-linux-gcc is provided with the source so I don't think this is an issue of something missing, I don't think. Any help appreciated.

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

---

### Post by Cypher on 2008-11-01
You don't have the cross-compilers for the MIPS processor running on the Linksys.

You will first need that, the error is right there in your log, "mipsel-linux-gcc: not found"..

Grab the toolchain from [http://www.dd-wrt.com/dd-wrtv2/downloads/others/sourcecode/toolchains/toolchains.darwin.ppc.sp1.tar.bz2](http://www.dd-wrt.com/dd-wrtv2/downloads/others/sourcecode/toolchains/toolchains.darwin.ppc.sp1.tar.bz2) and you should be able to compile the firmware..

---

### Post by ff2kracer on 2008-11-01
> **Cypher said:**
> You don't have the cross-compilers for the MIPS processor running on the Linksys.

You will first need that, the error is right there in your log, "mipsel-linux-gcc: not found"..

Thanks. I understand that much (but couldn't articulate it), the issue is that I believe I have the compilers - in other words, I can locate the mipsel-linux-gcc folder/files and have moved them around and linked to them. I guess my hang-up is why can't the makefile activate the cross-compiler. Also, I am confused if bin/sh may have something to do with this, I don't really understand that.

Any help appreciate in steps to possibly resolve this.

---

