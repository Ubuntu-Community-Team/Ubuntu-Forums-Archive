---
title: "Cannot find arm-linux-gcc"
date: 2012-08-09
forum: Programming Talk
---

### Post by ilnadi on 2012-08-09
I am trying to cross-build uClinux for ARM on Ubuntu 10.04 and I have a number of packages installed (see below) but none of them seem to install arm-linux-gcc (which is what the uClinux uses).  What am I missing? (BTW, I am a newbie)  Thank you

gcc-4.4-arm-linux-gnueabi
gcc-4.5-arm-linux-gnueabi
gcc-4.6-arm-linux-gnueabi
gcc-arm-linux-gnueabi

Also, gcc-linaro-arm-linux-gnueabi will not install because: 
" Depends: libc6 (>=2.13) but 2.11.1-0ubuntu7.10 is to be installed"

---

### Post by Bachstelze on 2012-08-09
The command arm-linux-gcc does not exist in any official Ubuntu package. In particular, the package  gcc-4.6-arm-linux-gnueabi installs the command arm-linux-gnueabi-gcc-4.6. I suppose you must have a symlink arm-linux-gnueabi-gcc.

---

### Post by pellyhawk on 2012-08-10
Bachstelze,

See you again:wink:, and thanks for your help several days ago.

ilnadi,

Maybe I can help you and give you some suggestion. gcc-arm-linux-gnueabi package is not supported until Ubuntu 10.10. See [here]("http://askubuntu.com/questions/123835/gcc-arm-linux-gnueabi-package-not-found-on-10-04-lts-lucid"). Special thanks to spjackson for providing me with this link.

---

### Post by ilnadi on 2012-08-16
I had already found the link you provided and installed the linero toolchain.  The issue seems to be that the makefile is looking for arm-linux-gcc and nothing with that name is installed (that I can see).  Did you end up changing the makefile to the proper gcc toolchain?

> **pellyhawk said:**
> ilnadi,

Maybe I can help you and give you some suggestion. gcc-arm-linux-gnueabi package is not supported until Ubuntu 10.10. See [here]("http://askubuntu.com/questions/123835/gcc-arm-linux-gnueabi-package-not-found-on-10-04-lts-lucid"). Special thanks to spjackson for providing me with this link.

---

### Post by ilnadi on 2012-08-17
ok, so I upgraded to Ubuntu 11.04 AND installed Mentor Codesourcery for ARM uClinux.  Still there is no arm-linux-gcc.  There are a number of arm-...-gcc available but I cannot see how to force the makefile to use the other command (e.g. "arm-uclinuxeabi-gcc" from codesourcery)

---

### Post by the_unforgiven on 2012-08-19
> **ilnadi said:**
> ok, so I upgraded to Ubuntu 11.04 AND installed Mentor Codesourcery for ARM uClinux.  Still there is no arm-linux-gcc.  There are a number of arm-...-gcc available but I cannot see how to force the makefile to use the other command (e.g. "arm-uclinuxeabi-gcc" from codesourcery)

You could simply try ```
CC=arm-uclinuxeabi-gcc make
```

---

