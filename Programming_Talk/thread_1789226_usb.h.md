---
title: "usb.h"
date: 2011-06-23
forum: Programming Talk
---

### Post by jaypatel on 2011-06-23
I am getting ther following error while using usb.h
In function `device_init':
usb.c:(.text+0x7): undefined reference to `usb_init'
usb.c:(.text+0xc): undefined reference to `usb_find_busses'
usb.c:(.text+0x11): undefined reference to `usb_find_devices'
usb.c:(.text+0x16): undefined reference to `usb_busses'
collect2: ld returned 1 exit status
How to use gcc -L and -I to give reference to usb.h.I am not using libusb.

---

### Post by dwhitney67 on 2011-06-23
> **jaypatel said:**
> 
How to use gcc -L and -I to give reference to usb.h.I am not using libusb.

:confused:

Why are you not using libusb?  You need it to link your application!

```

gcc app.c -lusb

```

P.S.  Remember this... system header files only define function prototypes, sometimes an external variable (such as in usb.h).  The implementation for these functions (and variables) is located within the library file itself (eg. /usr/lib/libusb.so).

---

