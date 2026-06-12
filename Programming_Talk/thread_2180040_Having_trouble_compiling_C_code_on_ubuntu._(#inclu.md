---
title: "Having trouble compiling C code on ubuntu. (#include errors)"
date: 2013-10-11
forum: Programming Talk
---

### Post by Bond112 on 2013-10-11
I'm trying to compile a C program on ubuntu 12.10 running in vmware, for the purpose of putting the compiled program on another, older linux  machine later. However, when I compile with gcc prog.c -o prog, I get an  error: "fatal error: asm/page.h: No such file or directory" Here are  the headers:

  #include <stdio.h>
#include <errno.h>
#include <stdlib.h>
#include <string.h>
#include <malloc.h>
#include <limits.h>
#include <signal.h>
#include <unistd.h>
#include <sys/uio.h>
#include <sys/mman.h>
#include <asm/page.h>
#include <asm/unistd.h>  

I get an error at #include. It says "fatal error: asm/page.h: No such  file or directory." How can I get the missing header? Thanks.

---

### Post by alan9800 on 2013-10-11
have you tried to run the following command in a Terminal window:```
sudo find / -iname page.h
```:?:
If that file exists on the HD on which you installed Ubuntu, with that command you'll find it.

---

### Post by Bond112 on 2013-10-11
Well I found files named that in a number of locations, but I don't understand how I should make the program access it. Here's the results:

> /usr/src/linux-headers-3.5.0-17/include/xen/page.h
/usr/src/linux-headers-3.5.0-17/include/asm-generic/page.h
/usr/src/linux-headers-3.5.0-17/arch/um/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/hexagon/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/frv/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/xtensa/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/arm/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/alpha/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/h8300/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/blackfin/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/sparc/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/x86/include/asm/xen/page.h
/usr/src/linux-headers-3.5.0-17/arch/x86/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/score/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/openrisc/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/parisc/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/avr32/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/tile/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/s390/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/mips/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/cris/include/arch-v32/arch/page.h
/usr/src/linux-headers-3.5.0-17/arch/cris/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/cris/include/arch-v10/arch/page.h
/usr/src/linux-headers-3.5.0-17/arch/mn10300/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/microblaze/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/c6x/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/m68k/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/m32r/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/sh/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/powerpc/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/unicore32/include/asm/page.h
/usr/src/linux-headers-3.5.0-17/arch/ia64/include/asm/xen/page.h
/usr/src/linux-headers-3.5.0-17/arch/ia64/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/include/xen/page.h
/usr/src/linux-headers-3.5.0-41/include/asm-generic/page.h
/usr/src/linux-headers-3.5.0-41/arch/um/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/hexagon/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/frv/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/xtensa/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/arm/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/alpha/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/h8300/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/blackfin/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/sparc/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/x86/include/asm/xen/page.h
/usr/src/linux-headers-3.5.0-41/arch/x86/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/score/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/openrisc/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/parisc/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/avr32/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/tile/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/s390/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/mips/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/cris/include/arch-v32/arch/page.h
/usr/src/linux-headers-3.5.0-41/arch/cris/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/cris/include/arch-v10/arch/page.h
/usr/src/linux-headers-3.5.0-41/arch/mn10300/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/microblaze/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/c6x/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/m68k/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/m32r/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/sh/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/powerpc/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/unicore32/include/asm/page.h
/usr/src/linux-headers-3.5.0-41/arch/ia64/include/asm/xen/page.h
/usr/src/linux-headers-3.5.0-41/arch/ia64/include/asm/page.h
/usr/src/linux-headers-3.5.0-41-generic/include/config/have/aligned/struct/page.h
/usr/src/linux-headers-3.5.0-41-generic/include/config/hugetlb/page.h
/usr/src/linux-headers-3.5.0-17-generic/include/config/have/aligned/struct/page.h
/usr/src/linux-headers-3.5.0-17-generic/include/config/hugetlb/page.h

---

### Post by alan9800 on 2013-10-11
try```
#include <asm-generic/page.h>
```

---

### Post by sanderj on 2013-10-11
Same question (+answers) here [http://stackoverflow.com/questions/19310541/having-trouble-compiling-c-code-on-ubuntu-include-errors](http://stackoverflow.com/questions/19310541/having-trouble-compiling-c-code-on-ubuntu-include-errors) ?

---

### Post by Bond112 on 2013-10-11
> **alan9800 said:**
> try```
#include <asm-generic/page.h>
```

I get the same error.

> **sanderj said:**
> Same question (+answers) here [http://stackoverflow.com/questions/19310541/having-trouble-compiling-c-code-on-ubuntu-include-errors](http://stackoverflow.com/questions/19310541/having-trouble-compiling-c-code-on-ubuntu-include-errors) ?

Yes that's me obviously. I still haven't been able to compile it though. You can see my reply to the last answer.

---

### Post by trent.josephsen on 2013-10-11
> **Bond112 said:**
> Yes that's me obviously. I still haven't been able to compile it though. You can see my reply to the last answer.

What about the first answer?

---

### Post by qyot27 on 2013-10-11
Pass -I/usr/src/linux-headers-3.5.0-17/arch/x86/include/ to your CFLAGS - including a file in <> denotes a system location, and the purpose of the CFLAGS parameters are to tell your compiler to look in additional directories as a system location.

However, I'd still consider the point of whether it's necessary to include that file at all, like was suggested on SO.

---

