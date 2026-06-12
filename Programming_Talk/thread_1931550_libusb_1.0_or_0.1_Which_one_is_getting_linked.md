---
title: "libusb 1.0 or 0.1: Which one is getting linked"
date: 2012-02-25
forum: Programming Talk
---

### Post by ufuser01 on 2012-02-25
Hi,

When I use -lusb option in my Makefile, which shared library is being used libusb 1.0 or 0.1? Below is a list from my linux box: 

```

$ dpkg -l | grep libusb
rc  libusb++-0.1-4c2                     2:0.1.12-14ubuntu0.2                            userspace C++ USB programming library
ii  libusb-0.1-4                         2:0.1.12-14ubuntu0.2                            userspace USB programming library
ii  libusb-1.0-0                         2:1.0.6-1                                       userspace USB programming library
ii  libusb-1.0-0-dev                     2:1.0.6-1                                       userspace USB programming library developmen
ii  libusb-dev                           2:0.1.12-14ubuntu0.2                            userspace USB programming library developmen
ii  libusbmuxd1                          1.0.2-1ubuntu2                                  USB multiplexor daemon for iPhone and iPod T
 
```

Thanks.

---

### Post by Bachstelze on 2012-02-25
Run [font=monospace]ldd[/font] on the compiled program to find out.

---

### Post by MadCow108 on 2012-02-25
the 0.1 one

the 1.0 one is called libusb-1.0 -> -lusb-1.0

---

