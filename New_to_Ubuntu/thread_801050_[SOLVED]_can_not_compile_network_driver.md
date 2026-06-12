---
title: "[SOLVED] can not compile network driver"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Phuzzy_one on 2008-05-20
when i try to compile a network driver i get this erro message:
"make -C src/ clean
make[1]: Entering directory `/usr/src/r8168-8.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/usr/src/r8168-8.006.00/src'
make -C src/ modules
make[1]: Entering directory `/usr/src/r8168-8.006.00/src'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/r8168-8.006.00/src'
make: *** [modules] Error 2"
any idea why tyhis is,

---

### Post by quelx on 2008-05-20
Have you tried following this guide for the realtek r8168?

[http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)

---

### Post by Phuzzy_one on 2008-05-21
thank you for the web site, it worked just fine:)

---

