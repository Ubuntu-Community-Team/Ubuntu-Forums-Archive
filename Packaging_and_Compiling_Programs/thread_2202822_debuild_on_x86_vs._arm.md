---
title: "debuild on x86 vs. arm ?"
date: 2014-01-31
forum: Packaging and Compiling Programs
---

### Post by hvn2 on 2014-01-31
Hi,

I'm running Ubuntu 12.04 on both x86 and ARMv7 (armhf). I need to install Xenomai, and doing so from source (2.6.3) I downloaded it and acted according to [http://www.xenomai.org/index.php/Building_Debian_packages](http://www.xenomai.org/index.php/Building_Debian_packages). The odd thing is that debuild prefectly on x86: I get the packages that I need. Then I try on ARMv7, and debuild ends in error that it can't create certain directories. Then finding the "debuild -aarmhf" option, I decide to cross-compile, but I end up with a build-log and no packages . I asked at Xenomai, but they have no solution other than patching debuild. Can someone please help me out ?

Thanks.

Addition: using "debuild -eCROSS_COMPILE=arm-none-linux-gnueabihf- -aarmhf -uc -us" on x86 for armhf results in the same error that I get on native building on armhf.
Addition 2: using "debuild -eCROSS_COMPILE=arm-none-linux-gnueabihf- -uc -us" on x86 for armhf results in the build of i386 packages. So apparently there is something wrong with debuild for armhf.

---

