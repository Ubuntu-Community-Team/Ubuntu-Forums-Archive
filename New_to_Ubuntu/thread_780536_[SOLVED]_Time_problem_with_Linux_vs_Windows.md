---
title: "[SOLVED] Time problem with Linux vs Windows"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2008-05-03
Hi
I have a computer with 2 HDD, one is with Windows XPSP2, the other with Linux Ubuntu 7.04 (hummm 7.06 ? not sure)
When I boot Linux, then later reboot with Windows, time is offset by 4 hours.

Look to me Ubuntu changes time in BIOS

How can I fix this ?

Thanks,

PL

---

### Post by lazyart on 2008-05-03
Make sure your time zones are correct.

---

### Post by Helios38 on 2008-05-03
modify your time settings, probably a timezone mess up.

---

### Post by spupy on 2008-05-03
> **Pierrot Lafouine said:**
> Look to me Ubuntu changes time in BIOS

Both operating systems change the time of the hardware clock. The difference is that the one saves in the local time zone, the other one in UTC (Coordinated Universal Time). 

Here
[https://help.ubuntu.com/community/UbuntuTime#head-7f2edfd2f352f7f015759cd8eb7652deb69088aa](https://help.ubuntu.com/community/UbuntuTime#head-7f2edfd2f352f7f015759cd8eb7652deb69088aa)
is explained how to fix the problem for Windows or for Ubuntu, which ever one you prefer.

---

### Post by Pierrot Lafouine on 2008-07-08
Forgot to close ticket
Thanks Spupy
It works.

---

