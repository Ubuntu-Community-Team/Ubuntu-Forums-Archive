---
title: "Linux-headers"
date: 2010-02-28
forum: Packaging and Compiling Programs
---

### Post by TobbeR on 2010-02-28
Hi

I have a new problem when compiling a FT245 driver, I have done it many times before but with Karmic it is not possible.

Error:
make -C /lib/modules/2.6.31-19-generic/build M=/home/tobbe/ft245 modules
make[1]: Går till katalogen "/usr/src/linux-headers-2.6.31-19-generic"
  CC [M]  /home/tobbe/ft245/ft245.o
/home/tobbe/ft245/ft245.c: In function ‘ft245_probe’:
/home/tobbe/ft245/ft245.c:229: error: implicit declaration of function ‘info’
/home/tobbe/ft245/ft245.c: In function ‘ft245_open’:
/home/tobbe/ft245/ft245.c:365: error: implicit declaration of function ‘warn’
/home/tobbe/ft245/ft245.c: In function ‘ft245_disconnect’:
/home/tobbe/ft245/ft245.c:863: error: implicit declaration of function ‘lock_kernel’
/home/tobbe/ft245/ft245.c:871: error: implicit declaration of function ‘unlock_kernel’
make[2]: *** [/home/tobbe/ft245/ft245.o] Fel 1
make[1]: *** [_module_/home/tobbe/ft245] Fel 2
make[1]: Lämnar katalogen "/usr/src/linux-headers-2.6.31-19-generic"
make: *** [default] Fel 2

AFAIK this shows some functions are no longer present in the headers, please advice me what to do.

Regards
John

---

