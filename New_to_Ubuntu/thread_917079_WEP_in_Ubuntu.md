---
title: "WEP in Ubuntu"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by tonycm1 on 2008-09-11
I've been trying to connect to my school's wireless internet for the last few hours and haven't been able to. Works fine when i boot in Windows, but in Ubuntu doesn't quite work.

I've tried to mimic the instructions at [http://apps.carleton.ca/ntw/wireless/start/CU_wirelessConnectivity.php](http://apps.carleton.ca/ntw/wireless/start/CU_wirelessConnectivity.php) to work in Ubuntu but it looks like it's searching for a certificate and can't find it....

Is this even possible in Ubuntu?

---

### Post by jamesrl on 2008-09-11
Can you post wireless hardware and driver information?  While I haven't had a wireless issue since at least 6.06 or so, it used to be that certain features (such as WEP/WPA) weren't supported by the drivers for certain network cards (especially when using ndiswrapper).  The reason is that the hardware manufacturers often don't release linux drivers, so the people writing the linux drivers often don't put in all the features immediately (as they don't perfectly understand the hardware or simply never took the time to implement features they don't use, such as WEP).

If you aren't sure the hardware, you can find out by say:
```
lspci | grep "Network"
```

---

### Post by tonycm1 on 2008-09-11
Here's the hardware
```
tony@tony-laptop:~$ lspci | grep "Network"
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

### Post by tonycm1 on 2008-09-14
bump

---

### Post by farsight on 2008-09-14
Hey hey,

Sorry to hear about the problem. At my university we gain access by registering the MAC address. Is this an option for you? If so maybe it will connect as my does at university.

---

### Post by R_T_H on 2008-09-14
I know at my (secondary) school one is meant to obtain a key from the IT technicians. Or use something to find the key out ;). But I reccomend talking to the IT department.

---

### Post by Miljet on 2008-09-14
On the login screen where you type in the passcode, try changing the default connection type from "128 bit encryption" to "64 bit/128 bit hex". That usually works for me at RV Parks that use WEP. Slow as molasas, but it works.

---

