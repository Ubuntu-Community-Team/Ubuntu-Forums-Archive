---
title: "help: asm/io.h: No such file or directory"
date: 2009-07-13
forum: Programming Talk
---

### Post by tomasd on 2009-07-13
Dear all,

I'm trying to compile an example from [http://tldp.org/HOWTO/IO-Port-Programming-9.html](http://tldp.org/HOWTO/IO-Port-Programming-9.html) and getting an error:
```
example.c:11:20: error: asm/io.h: No such file or directory
example.c: In function &#8216;main&#8217;:
example.c:18: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
example.c:30: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
example.c:32: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;

```
I tried looking for io.h in /usr/src/linux-headers-2.6.28-13-generic/ and the only io.h I found is /usr/src/linux-headers-2.6.28-13-generic/include/config/fb/deferred/io.h I suspect my kernel headers are incomplete. Is there another package for kernel headers that contains all header files?

---

### Post by Zugzwang on 2009-07-13
That HOW-TO is now ~9 years old. Consider using something more recent.

---

### Post by monraaf on 2009-07-13
```

$ locate 'asm/io.h'
/usr/src/linux-headers-2.6.28-13/arch/alpha/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/arm/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/avr32/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/blackfin/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/cris/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/h8300/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/ia64/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/m68knommu/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/mips/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/parisc/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/powerpc/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/s390/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/sh/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/sparc/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/um/include/asm/io.h
/usr/src/linux-headers-2.6.28-13/arch/x86/include/asm/io.h

```

Other than that I agree with Zugzwang.

---

### Post by tomasd on 2009-07-13
thanks for quick replies, could you recomend anything I can read? I'm trying to create a little program that would wait for HIGH on one of the pins and then would set HIGH another pin for n delay

---

### Post by NathanB on 2009-07-13
ioctl is what you are looking for:

[http://en.wikipedia.org/wiki/Ioctl](http://en.wikipedia.org/wiki/Ioctl)

---

### Post by tomasd on 2009-07-17
After some reading got it although I must say there are very limited resources on the paralel programming in Linux that are not dated...
> 
#include <stdio.h>
#include <sys/io.h>
#include <string.h>
#include <errno.h>

#define PORTBASE 0x3bc //Data register
#define PORTSTATUS 0x3bd //Status register
#define PORTCTRL 0x3be // Control register

int main() {
    // Get access to PORTBASE
    if (ioperm(PORTBASE, 1, 1)) {
        printf("Couldn't get the port.\n");
        perror("ioperm problem:");
    }
    // Get access to PORTSTATUS
    if (ioperm(PORTSTATUS, 1, 1)) {
        printf("Couldn't get the port.\n");
        perror("ioperm problem:");
    }
    // Start Infinite loop
    for(;;){
        // Tring to avoid %100cpu usage
        sleep(1);
        // Pin 13 of status register became low (from 0x7F to 0x6F)
        if (inb(PORTSTATUS) == 0x6F){
            // Notify about pin status change
            printf("status port register value %X\n",inb(PORTSTATUS));
            // External function respond
            respond();
        }
    }
    return 0;
}

respond(void){
    // Set pin 2 (pin 0 data register) high
    outb(0x1, PORTBASE);
    sleep(1);
    // Set data register low
    outb(0x0, PORTBASE);
}



---

### Post by manusbattersby on 2010-02-21
I'm trying to do something similar, but had no success controlling the parallel port.  
I've tried the code you supplied but it doesn't compile, i'm new to this kind of thing on Linux. I'm sure it's something I'm doing wrong.
I'm using g++ on the command line, but it comes up with errors.

root@ubuntu-pc:/home/manus/Desktop# g++ lp_port.c -o lp_port
lp_port.c: In function ‘int main()’:
lp_port.c:26: error: expected primary-expression before ‘{’ token
lp_port.c:26: error: expected `;' before ‘{’ token
lp_port.c:26: error: expected primary-expression before ‘{’ token
lp_port.c:26: error: expected `)' before ‘{’ token
lp_port.c:28: error: ‘sleep’ was not declared in this scope
lp_port.c:35: error: ‘respond’ was not declared in this scope
lp_port.c: At global scope:
lp_port.c:41: error: ISO C++ forbids declaration of ‘respond’ with no type
lp_port.c: In function ‘int respond()’:
lp_port.c:45: error: ‘sleep’ was not declared in this scope
root@ubuntu-pc:/home/manus/Desktop# 


what compiler are you using ?

---

### Post by Zugzwang on 2010-02-22
> **manusbattersby said:**
> what compiler are you using ?

I think that the problem you are having comes from the smiley that the forum software inserted into the code because the poster forgot to use "CODE" tags. Replace the respective line by:
```

for (;;) {

```

For the errors in line 28 and 35, find out which header file you need to include. There have been some changes in the GCC library recently, but you can simply have a look at the man pages for the functions to find out what to include. Good luck!

---

