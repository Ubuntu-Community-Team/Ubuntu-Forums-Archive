---
title: "ubuntu-kernel 2.6.28 compilation problem"
date: 2009-05-08
forum: Packaging and Compiling Programs
---

### Post by titogrognon on 2009-05-08
Hi,

I used this how-to [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) to compile a custom kernel.
After a while i got thi error message:

```
CC [M]  ubuntu/tlsup/tlsup_radios.o
ubuntu/tlsup/tlsup_radios.c: In function ‘tlsup_radio_switch_set’:
ubuntu/tlsup/tlsup_radios.c:176: erreur: implicit declaration of function ‘msleep’
ubuntu/tlsup/tlsup_radios.c: In function ‘tlsup_register_rfkill’:
ubuntu/tlsup/tlsup_radios.c:237: attention : ignoring return value of ‘rfkill_register’, declared with attribute warn_unused_result
make[3]: *** [ubuntu/tlsup/tlsup_radios.o] Erreur 1
make[2]: *** [ubuntu/tlsup] Erreur 2
make[1]: *** [ubuntu] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-source-2.6.28 »
```Any idea to make this work?
Thanks!

---

