---
title: "Open2x Won't Compile"
date: 2006-12-28
forum: Programming Talk
---

### Post by Megatog615 on 2006-12-28
```
autoconf: Undefined macros:
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_MSG
for dir in /home/megatog615/svn/open2x/toolchain/glibc-2.3.5/build-open2x-stage1 sysdeps/arm/elf linuxthreads/sysdeps/unix/sysv/linux/arm linuxthreads/sysdeps/unix/sysv/linux linuxthreads/sysdeps/pthread sysdeps/pthread linuxthreads/sysdeps/unix/sysv linuxthreads/sysdeps/unix linuxthreads/sysdeps/arm sysdeps/unix/sysv/linux/arm sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/common sysdeps/unix/mman sysdeps/unix/inet sysdeps/unix/sysv sysdeps/unix/arm sysdeps/unix sysdeps/posix sysdeps/arm sysdeps/wordsize-32 sysdeps/ieee754/flt-32 sysdeps/ieee754/dbl-64 sysdeps/ieee754 sysdeps/generic/elf sysdeps/generic; do \
          test -f $dir/syscalls.list && \
          { /bin/sh sysdeps/unix/make-syscalls.sh $dir || exit 1; }; \
          test $dir = sysdeps/unix && break; \
        done > /home/megatog615/svn/open2x/toolchain/glibc-2.3.5/build-open2x-stage1/sysd-syscallsT
mv -f /home/megatog615/svn/open2x/toolchain/glibc-2.3.5/build-open2x-stage1/sysd-syscallsT /home/megatog615/svn/open2x/toolchain/glibc-2.3.5/build-open2x-stage1/sysd-syscalls
make[2]: Failed to remake makefile `/home/megatog615/svn/open2x/toolchain/glibc-2.3.5/build-open2x-stage1/config.make'.
make[2]: Leaving directory `/home/megatog615/svn/open2x/toolchain/glibc-2.3.5'
make[2]: Entering directory `/home/megatog615/svn/open2x/toolchain/glibc-2.3.5'
autoconf  sysdeps/unix/sysv/linux/configure.in > sysdeps/unix/sysv/linux/configure.new
autoconf: Undefined macros:
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_MSG
***BUG in Autoconf--please report*** AC_FD_CC
***BUG in Autoconf--please report*** AC_FD_MSG
make[2]: Failed to remake makefile `/home/megatog615/svn/open2x/toolchain/glibc-2.3.5/build-open2x-stage1/config.make'.
/usr/bin/install -c -m 644 include/limits.h /usr/local/open2x/open2x/include/limits.h
/usr/bin/install -c -m 644 include/values.h /usr/local/open2x/open2x/include/values.h
/usr/bin/install -c -m 644 include/features.h /usr/local/open2x/open2x/include/features.h
/usr/bin/install -c -m 644 include/gnu-versions.h /usr/local/open2x/open2x/include/gnu-versions.h
/usr/bin/install -c -m 644 linuxthreads/sysdeps/pthread/bits/libc-lock.h /usr/local/open2x/open2x/include/bits/libc-lock.h
/usr/bin/install -c -m 644 include/bits/xopen_lim.h /usr/local/open2x/open2x/include/bits/xopen_lim.h
/usr/bin/install -c -m 644 include/gnu/libc-version.h /usr/local/open2x/open2x/include/gnu/libc-version.h
/usr/bin/install -c -m 644 /home/megatog615/svn/open2x/toolchain/glibc-2.3.5/build-open2x-stage1/gnu/lib-names.h /usr/local/open2x/open2x/include/gnu/lib-names.h
/usr/bin/install: cannot stat `/home/megatog615/svn/open2x/toolchain/glibc-2.3.5/build-open2x-stage1/gnu/lib-names.h': No such file or directory
make[2]: *** [/usr/local/open2x/open2x/include/gnu/lib-names.h] Error 1
make[2]: Leaving directory `/home/megatog615/svn/open2x/toolchain/glibc-2.3.5'
make[1]: *** [install-headers] Error 2
make[1]: Leaving directory `/home/megatog615/svn/open2x/toolchain/glibc-2.3.5/build-open2x-stage1'
make: *** [/usr/local/open2x/open2x/include/stdio.h] Error 2

```It compiled just fine on my other Ubuntu 6.10 machine... What are the dependencies for Open2x, anyway?

---

### Post by hod139 on 2006-12-30
What version of autoconf do you have installed and what version is Open2x expecting?

---

