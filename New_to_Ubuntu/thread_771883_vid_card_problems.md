---
title: "vid card problems"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by sir_napsalot on 2008-04-28
Ok, I just installed *Ubuntu* recently and I'm still getting everything configured. The video card in question is part of the ATI Radeon x1600 series, the drivers installed fine (as far as I can tell) but when I try to boot into *Ubuntu* using the card instead of the integrated video I see this screen with some text on it and thats as far as it goes. Following is what is listed on said screen:
*Starting anac(h)ronistic cron anacron      [ok]
*Starting deferred execution scheduler atd  [ok]
*Starting peridic command scheduler crond   [ok]
*Checking battery state                     [ok]
*Running local boot scripts (/etc/rc.local) [ok]
I am running *Ubuntu* on a desktop.
AMD Athlon 64 2.4 GHz
1.5 GB DDR RAM
Any help is appreciate, thank you in advance!
Btw, does anyone know of a list that contains all or most of the commands for the GNOME Terminal?

---

### Post by sir_napsalot on 2008-04-29
well i have been trying to solve my video card problem myself. downloaded the ATI video card driver for the x1600 card. i have been following the binary driver installation instructions here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0)
but to no avail. everytime i run the 
sudo dpkg -i xorg-driver-fglrx_8.476-0ubuntu1_i386.deb command it comes back with an error that reads:
/usr/sbin/atienetsd: error while loading dhared libraries: libGL.so.1: cannot open shared object file: No such file or directory.
can someone tell me what im doing wrong?

---

