---
title: "Using Windows Wireless Drivers"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by EvilOtto on 2008-10-25
Hello all!  I'm new to Ubuntu (just installed it this afternoon) and am trying to use the Windows wireless driver for my system with Ubuntu so that I can get online (I use a D-Link WUA-2340).  According to the directions here [https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html) the file should end with .inf but I can't seem to locate it on my computer (a search yielded about 1200 results).  Where can I find it?  Sorry for such a novice question- thanks in advance!

---

### Post by phidia on 2008-10-25
See if this driver [her]("ftp://ftp.dlink.com/Wireless/wua2340/Drivers/WUA2340_driver_140.zip")e will work for you.

---

### Post by EvilOtto on 2008-10-26
So far I haven't been able to get that to work.  Thanks though, I'll keep trying.

---

### Post by igknighted on 2008-10-26
What wireless chipset (not d-link, they package another company's chip)... if you don't know, try running the command 'lspci | grep network' and posting the results.  Most of the time you will have better luck with a native linux driver, we can point you to the proper one if we know which chip you have.

---

