---
title: "Modem Driver (Iburst)"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by silkko on 2008-08-16
Im a complete newbie to Ubuntu, but really interested in it.. I have a little problem though and this is because i have problems with installations.. I find it rather easy to install .deb files but when it comes to .tar.gz i guess i get a bit confused.

My modem came with a driver installation cd which had the linux drivers but i cannot install them. this is what i get

```
silkko@DATA-laptop:~$ tar -xvf /home/silkko/Desktop/ibdriver-1.2.8.tar.gz
ibdriver-1.2.8/
ibdriver-1.2.8/Makefile
ibdriver-1.2.8/README.txt
ibdriver-1.2.8/ib0stat.py
ibdriver-1.2.8/ib-usb.c
ibdriver-1.2.8/LICENSE
ibdriver-1.2.8/ib-file.c
ibdriver-1.2.8/ib-pcmcia.c
ibdriver-1.2.8/ib-net.c
ibdriver-1.2.8/ib-net.h
silkko@DATA-laptop:~$ cd ibdriver-1.2.8
silkko@DATA-laptop:~/ibdriver-1.2.8$ make
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/silkko/ibdriver-1.2.8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/silkko/ibdriver-1.2.8/ib-net.o
/home/silkko/ibdriver-1.2.8/ib-net.c: In function ‘ib_net_setup’:
/home/silkko/ibdriver-1.2.8/ib-net.c:293: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/silkko/ibdriver-1.2.8/ib-net.c:347:50: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/silkko/ibdriver-1.2.8/ib-net.c: In function ‘ib_net_register’:
/home/silkko/ibdriver-1.2.8/ib-net.c:347: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/silkko/ibdriver-1.2.8/ib-net.c:347: error: (Each undeclared identifier is reported only once
/home/silkko/ibdriver-1.2.8/ib-net.c:347: error: for each function it appears in.)
make[2]: *** [/home/silkko/ibdriver-1.2.8/ib-net.o] Error 1
make[1]: *** [_module_/home/silkko/ibdriver-1.2.8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
silkko@DATA-laptop:~/ibdriver-1.2.8$ 
```

It also came with a patch which i have no idea of how to apply. Im kind of in a fix right now so can anyone offer a helping hand.

---

