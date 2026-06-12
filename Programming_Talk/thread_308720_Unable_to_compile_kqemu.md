---
title: "Unable to compile kqemu"
date: 2006-11-28
forum: Programming Talk
---

### Post by Teo on 2006-11-28
My Ubuntu is Edgy and I can't compile Kqemu kernel module (kqemu from qemu project page).

Got:
build-essential
linux-image-2.6.17-10-generic
linux-image-generic
linux-headers-2.6.17-10-generic
linux-headers-2.6.17-10
linux-headers-generic
linux-source-2.6.17
linux-source

Here's some code
```
tomek@teo:~$ cd kqemu-1.3.0pre9/
tomek@teo:~/kqemu-1.3.0pre9$ ls -an
total 612
drwxr-xr-x  2 1000 1000   4096 2006-11-28 21:34 .
drwxr-x--x 67 1000 1000   4096 2006-11-28 21:34 ..
-rw-r--r--  1 1000 1000   1369 2006-06-23 22:52 Changelog
-rwxr-xr-x  1 1000 1000   7274 2006-06-23 22:52 configure
-rwxr-xr-x  1 1000 1000    435 2006-06-23 22:52 install.sh
-rw-r--r--  1 1000 1000   7351 2006-06-23 22:52 kqemu-doc.html
-rw-r--r--  1 1000 1000   6022 2006-06-23 22:52 kqemu-doc.texi
-rw-r--r--  1 1000 1000  12380 2006-06-23 22:52 kqemu-freebsd.c
-rw-r--r--  1 1000 1000   4728 2006-06-23 22:52 kqemu.h
-rw-r--r--  1 1000 1000   1552 2006-06-23 22:52 kqemu.inf
-rw-r--r--  1 1000 1000   1586 2006-06-23 22:52 kqemu-kernel.h
-rw-r--r--  1 1000 1000   9447 2006-06-23 22:52 kqemu-linux.c
-rw-r--r--  1 1000 1000  98845 2006-06-23 22:52 kqemu-mod-i386.o
-rw-r--r--  1 1000 1000  99209 2006-06-23 22:52 kqemu-mod-i386-win32.o
-rw-r--r--  1 1000 1000 157954 2006-06-23 22:52 kqemu-mod-x86_64.o
-rwxr-xr-x  1 1000 1000 123939 2006-06-23 22:52 kqemu.sys
-rw-r--r--  1 1000 1000  10563 2006-06-23 22:52 kqemu-win32.c
-rw-r--r--  1 1000 1000    704 2006-06-23 22:52 LICENSE
-rw-r--r--  1 1000 1000   1568 2006-06-23 22:52 Makefile
-rw-r--r--  1 1000 1000    184 2006-06-23 22:52 Makefile.freebsd
-rw-r--r--  1 1000 1000    992 2006-06-23 22:52 Makefile.winnt
-rw-r--r--  1 1000 1000    131 2006-06-23 22:52 README


tomek@teo:~/kqemu-1.3.0pre9$ ./configure
Source path       /home/tomek/kqemu-1.3.0pre9
C compiler        gcc
Host C compiler   gcc
make              make
host CPU          i386

kernel sources    /lib/modules/2.6.17-10-generic/build
kbuild type       2.6


tomek@teo:~/kqemu-1.3.0pre9$ make
make -C /lib/modules/2.6.17-10-generic/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/tomek/kqemu-1.3.0pre9/kqemu-linux.o
cp /home/tomek/kqemu-1.3.0pre9/kqemu-mod-i386.o /home/tomek/kqemu-1.3.0pre9/kqemu-mod.o
  LD [M]  /home/tomek/kqemu-1.3.0pre9/kqemu.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /home/tomek/kqemu-1.3.0pre9/.kqemu-mod.o.cmd for /home/tomek/kqemu-1.3.0pre9/kqemu-mod.o
  CC      /home/tomek/kqemu-1.3.0pre9/kqemu.mod.o
  LD [M]  /home/tomek/kqemu-1.3.0pre9/kqemu.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
```

Did it once (same way) in Dapper and successfully compiled. What's wrong? Why 'make' can't find this file?

BTW why there's no kqemu package in repos? ](*,)

---

### Post by gborzi on 2006-11-28
Hello, I have successfully compiled kqemu recently on my edgy installation using the instructions from and italian blog, [http://pollycoke.wordpress.com/](http://pollycoke.wordpress.com/). I suppose you don't read italian, so I give you an english summary of the steps to follow:
[LIST=1]
[*]Get qemu 0.8.2 and kqemu 1.3.0pre9 sources;
[*]extract qemu and kqemu inside the qemu directory, i.e.> tar zxf qemu-0.8.2.tar.gz
cd qemu-0.8.2
tar zxf ../kqemu-1.3.0pre9.tar.gz
[*]configure qemu compilation > ./configure --disable-gcc-check --disable-gfx-check
[*]move to kqemu directory, configure, compile and install > cd kqemu-1.3.0pre9
./configure && make && sudo make install
[*]finally, create the file /etc/modprobe.d/kqemu with the following content > options kqemu major=0
install kqemu /sbin/modprobe --ignore-install kqemu && chmod 666 /dev/kqemu

[/LIST]
Hope this works.

---

### Post by shining on 2006-11-28
> **Teo said:**
> 
Did it once (same way) in Dapper and successfully compiled. What's wrong? Why 'make' can't find this file?


Are you sure it didn't work? It's only a warning, and it seems the kqemu module was built anyway.

> 
BTW why there's no kqemu package in repos? ](*,)

[http://fabrice.bellard.free.fr/qemu/qemu-accel.html](http://fabrice.bellard.free.fr/qemu/qemu-accel.html) :
> 
Try it
 The QEMU Accelerator Module is available in the Download area. Be aware that unlike the rest of QEMU it is a closed source proprietary product with a specific license. 
Terms of Use
 The QEMU Accelerator is free to use, but it is a closed source proprietary product. You are not allowed to distribute it yourself to other people without an explicit authorisation. Distributors wishing to include the QEMU accelerator on CDs, ISO images or packages must contact the author to know the exact terms.


---

### Post by Teo on 2006-11-28
> **shining said:**
> Are you sure it didn't work? It's only a warning, and it seems the kqemu module was built anyway.
To say truth, I did not check. Well it's working anyway :)

THX both of you (gborzi and shining) for help :).

---

### Post by lqqkout4elfy on 2007-02-21
I think kqemu is now released as an open sourced GPL product.
[http://fabrice.bellard.free.fr/qemu/download.html]("http://fabrice.bellard.free.fr/qemu/download.html")

---

