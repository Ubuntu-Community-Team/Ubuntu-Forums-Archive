---
title: "Compiling Firefox 1.5.0.7 with icpc"
date: 2006-09-27
forum: Programming Talk
---

### Post by angkel07 on 2006-09-27
I was trying to compile Firefox using Intel C++ Compiler. But I always get an error at the end. What can be the problems that I am getting with it? Here's what I got:
> eGTK.cpp:(.text+0xb58): undefined reference to `XftDrawCreate'
make[4]: *** [firefox-bin] Error 1
make[4]: Leaving directory `/home/lazarus/mozilla/obj-i686-pc-linux-gnu/browser/app'
make[3]: *** [libs] Error 2
make[3]: Leaving directory `/home/lazarus/mozilla/obj-i686-pc-linux-gnu/browser'make[2]: *** [tier_99] Error 2
make[2]: Leaving directory `/home/lazarus/mozilla/obj-i686-pc-linux-gnu'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/lazarus/mozilla/obj-i686-pc-linux-gnu'
make: *** [build] Error 2

Thanks in advance.

---

