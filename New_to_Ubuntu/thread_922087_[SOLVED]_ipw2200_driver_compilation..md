---
title: "[SOLVED] ipw2200 driver compilation."
date: 2008-09-16
forum: New to Ubuntu
---

### Post by OutOfReach on 2008-09-16
I just finished compiling a vanilla kernel (2.6.26.5) from kernel.org. Now everything except my wireless and ALSA works (I think I can handle compiling ALSA). But, I need some help with my wireless. My wireless card is a Intel PRO/Wireless 2915 ABG. The driver (according to lshw) is ipw2200. So I already downloaded the ipw220 package from (ipw2200.sourceforge.net) and I also downloaded the firmware. But I need help actually compiling and using this package and firmware.

Any help would be greatly appreciated.

---

### Post by jbrown96 on 2008-09-17
Not sure how much help this will be, but there is a list of requirements and instructions on this page [http://ipw2200.sourceforge.net/]("http://ipw2200.sourceforge.net/")

---

### Post by OutOfReach on 2008-09-17
Yes, in the end I found that the drivers (ipw2200) were actually installed along with the kernel, but the firmware (which is necessary) wasn't. So I solved that by downloading the firmware and putting it in /lib/firmware and problem solved.

---

