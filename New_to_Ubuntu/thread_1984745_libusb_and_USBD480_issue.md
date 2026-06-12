---
title: "libusb and USBD480 issue"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by qake on 2012-05-22
Hey community of ubuntu.

I'm studying basic embedded electronics in Denmark and for my final project, I have together with my internship-company decided to make a user-interface on a USBD480 TFT Display. ( [http://forum.lcdinfo.com/](http://forum.lcdinfo.com/) )

However, after a month of googlin' and three weeks before deadline, I have decided to post the very edge of my problem.

The display has a library from their manufacturer of which I can use commands, but it needs to be interfaced with use of a USB to an ARM processor which has built-in Linux .

$gcc test.c

```
#include </home/admin/arm-linux-gcc/libusb/libusb-1.0.9/libusb/libusb.h> 
 
int main (int argc, char **argv) //  
{
    usb_init();

    return 0; 
}
```Output:

```
admin@linux-machine:~/ALEX_GCC$ gcc test.c
/tmp/cchkSBid.o: In function `main':
test.c:(.text+0x7): undefined reference to `usb_init'
collect2: ld returned 1 exit status
admin@linux-machine:~/ALEX_GCC$ 
```The questions that I have are:

What do I need to do to fix the "undefined reference" problem?

If not *libusb*, which library would you recommend for this project and why?


Any help is appreciated

Sincerely, Qake

---

