---
title: "can't debug glibc after intall libc6-dbg"
date: 2011-06-29
forum: Programming Talk
---

### Post by simonwolf on 2011-06-29
System Info: 
Ubuntu 10.10
~$ uname -a
Linux yeyx-desktop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux

libc version:
/lib/libc.so.6 -> libc-2.12.1.so

gcc version:
~$ gcc -v
Using built-in specs.
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.4.4-14ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.4 --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) 

Why:
I want to debug glibc function for learning purpose.

How:
1. sudo apt-get install libc6-dbg
This will create a debug directory in /usr/lib. It contains the some sub directories. As following:
~$ ls /usr/lib/debug/
lib  lib64  sbin  usr

2.install source
~$ mkdir ~/libc ; cd ~/libc
~$ apt-get source libc6
~$ ls ~/libc/
eglibc-2.12.1  eglibc_2.12.1-0ubuntu10.2.diff.gz  eglibc_2.12.1-0ubuntu10.2.dsc  eglibc_2.12.1.orig.tar.gz

3.
//test_malloc.c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int* pa = (int*)malloc(sizeof(int)*100);

    printf("%p", pa);
    return 0;
} 

~$ echo $LD_LIBRARY_PATH
/usr/lib:/usr/local/lib:
~$ gcc -g -o test_malloc test_malloc.c
~$ gdb test_malloc
.......
0x08048324 in malloc@plt ()
(gdb) bt
#0  0x08048324 in malloc@plt ()
#1  0x08048409 in main () at test_malloc.c:5

4.other infomation
~/.gdbinit is empty

~$ ldd test_malloc
	linux-gate.so.1 =>  (0x00618000)
	libc.so.6 => /lib/libc.so.6 (0x007dc000)
	/lib/ld-linux.so.2 (0x00b5b000)

~$ ls /usr/lib/debug/lib/ -all
drwxr-xr-x 3 root root    4096 2011-06-28 20:11 .
drwxr-xr-x 6 root root    4096 2011-06-28 17:49 ..
-rwxr-xr-x 1 root root  494496 2011-01-22 07:08 ld-2.12.1.so
-rw-r--r-- 1 root root   48589 2011-01-22 07:08 libanl-2.12.1.so
-rw-r--r-- 1 root root   13700 2011-01-22 07:08 libBrokenLocale-2.12.1.so
-rwxr-xr-x 1 root root 6527831 2011-01-22 07:08 libc-2.12.1.so
-rw-r--r-- 1 root root   60945 2011-01-22 07:08 libcidn-2.12.1.so
-rw-r--r-- 1 root root   67616 2011-01-22 07:08 libcrypt-2.12.1.so
-rw-r--r-- 1 root root   94855 2011-01-22 07:08 libdl-2.12.1.so
-rw-r--r-- 1 root root  441404 2011-01-22 07:08 libm-2.12.1.so
-rw-r--r-- 1 root root   21683 2011-01-22 07:08 libmemusage.so
-rw-r--r-- 1 root root  363439 2011-01-22 07:08 libnsl-2.12.1.so
-rw-r--r-- 1 root root   74804 2011-01-22 07:08 libnss_compat-2.12.1.so
-rw-r--r-- 1 root root   43962 2011-01-22 07:08 libnss_dns-2.12.1.so
-rw-r--r-- 1 root root  133091 2011-01-22 07:08 libnss_files-2.12.1.so
-rw-r--r-- 1 root root   51502 2011-01-22 07:08 libnss_hesiod-2.12.1.so
-rw-r--r-- 1 root root  147338 2011-01-22 07:08 libnss_nis-2.12.1.so
-rw-r--r-- 1 root root  188279 2011-01-22 07:08 libnss_nisplus-2.12.1.so
-rw-r--r-- 1 root root    6020 2011-01-22 07:08 libpcprofile.so
-rwxr-xr-x 1 root root  593067 2011-01-22 07:08 libpthread-2.12.1.so
-rw-r--r-- 1 root root  184552 2011-01-22 07:08 libresolv-2.12.1.so
-rw-r--r-- 1 root root  135766 2011-01-22 07:08 librt-2.12.1.so
-rw-r--r-- 1 root root   16872 2011-01-22 07:08 libSegFault.so
-rw-r--r-- 1 root root  149887 2011-01-22 07:08 libthread_db-1.0.so
-rw-r--r-- 1 root root   15019 2011-01-22 07:08 libutil-2.12.1.so
drwxr-xr-x 3 root root    4096 2011-06-28 17:49 tls


Does anyone has any hint to fix this problem.

I had google much, but i can't find solution. I need help.

---

