---
title: "Wireless driver in kernel source code"
date: 2010-04-18
forum: Programming Talk
---

### Post by vksingh on 2010-04-18
Hi,
 
Can some body tell me where i can find source code for wireless driver in kernel source code. I have downloaded kernel 2.6.33 .
 
Please help.
 
Thanks,
 
Vivek

---

### Post by Reiger on 2010-04-18
There is not a single wireless driver; and, if I understood the structure from a glance while trying to find a specific device driver myself, the more mature wireless drivers tend to rely heavily on a few skeleton pieces and merely add in their own device specific stuff.

That said you will find a drivers/ section. If the driver is new, you will probably find it under drivers/staging. For instance the Ralink drivers are found there, an example is drivers/staging/rt2870 for the rt2870 chipset (used in Wireless-N USB dongles).

It may be best to consult the documentation (various text files) supplied with the kernel if you want to examine specific sub sets.

---

### Post by nvteighen on 2010-04-18
And why do you need to do this? If you want to get the driver, the best is always to 1) check the repositories and grab the package (download it w/o installing or using "apt-get source" or whatever) 2) get it from the manufacturer's webpage. Unless you want to actually develop part of it, I don't see why you'd like to take the driver's source... not taking account of the fact that wireless drivers are usually proprietary, of course.

---

