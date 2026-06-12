---
title: "Errors compiling driver module [newbie]"
date: 2005-05-09
forum: Packaging and Compiling Programs
---

### Post by DonQui(Kong)ote on 2005-05-09
I have installed Ubuntu (standard install) from DVD, and now I need to compile the rt2500 wireless drivers so I can get my network going (I have the source files for it already).  I have apt-got build-essentials from the DVD, and it seemed to install fine.  However, when I try to compile the driver module, I get the following error:

user@ubuntu:~/Desktop/STA/Module$ make
cc -D__KERNEL__ -I/usr/src/linux-2.6.10-5-amd64-generic/include -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -mpreferred-stack-boundary=4 -march=i686 -DMODULE -DMODVERSIONS -include /usr/src/linux-2.6.10-5-amd64-generic/include/linux/modversions.h -Wall -Wstrict-prototypes -Wno-trigraphs   -c -o rtmp_main.o rtmp_main.c
<command line>:9861602:1: /usr/src/linux-2.6.10-5-amd64-generic/include/linux/modversions.h: No such file or directory
rtmp_main.c: In function `RT2500_probe':
rtmp_main.c:131: warning: cast from pointer to integer of different size
rtmp_main.c:232: warning: cast to pointer from integer of different size
make: *** [rtmp_main.o] Error 1

I get this error whether or not I am root, user, sudo, etc.  Alternatively, is there any source for a AMD64 Hoary compiled version of of the RT2500 driver?  I have not found anything.

Thanks.  Great distro so far, will be better whe my wireless works :)

---

### Post by highhighs on 2005-11-12
edit the  MakeFile and change the line which has .../include/linux/modversions.h to  
/include/config/modversions.h

---

