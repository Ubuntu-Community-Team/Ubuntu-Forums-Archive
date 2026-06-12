---
title: "Is my computer 64-bit capable?  uname -a"
date: 2016-01-23
forum: New to Ubuntu
---

### Post by SciGuy1872 on 2016-01-23
Hi.  Chrome is ending support for 32-bit Linux AND 12.04; If my computer is 64-bit capable

anthony@anthony-desktop:~$ uname -a
Linux anthony-desktop 3.2.0-97-generic-pae #137-Ubuntu SMP Thu Dec 17 21:37:53 UTC 2015 i686 i686 i386 GNU/Linux

I will upgrade (GoPanda will have recent libs; is this process recommended for other programs?--Celestia; I read posts where the answer was to stay with the 32)  If this machine isn't 64-Bit capable, I will just move to Chromium.

Thanks,
     Anthony

---

### Post by vasa1 on 2016-01-23
Please post the output of **lscpu** within code tags like this:```
11:05 AM ~ $ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              10
CPU MHz:               2000.000
BogoMIPS:              3989.95
L1d cache:             32K
L1i cache:             32K
L2 cache:              2048K
NUMA node0 CPU(s):     0,1
11:05 AM ~ $ 
```

---

### Post by SciGuy1872 on 2016-01-23
anthony@anthony-desktop:~$ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            15
Model:                 2
Stepping:              7
CPU MHz:               2399.765
BogoMIPS:              4799.53

---

### Post by vasa1 on 2016-01-23
I suspect i686 and the second line indicate that your computer isn't 64-bit capable. I hope someone who knows better comments!

---

### Post by Petro Dawg on 2016-01-23
Looks like you have a 32bit CPU, which will not be able to run any 64bit OS or programs.  I run 32 bit OS for various reasons and have found Chromium to be a very good replacement for Google Chrome for all the stuff I do with my internet browsing.

> **vasa1 said:**
> I suspect i686 and the second line indicate that your computer isn't 64-bit capable. I hope someone who knows better comments!

Yes, i686 indicates an Intel x86 platform which is only 32bit.

---

### Post by SciGuy1872 on 2016-01-23
Okay, thanks for the help all!  I just installed Chromium and am now trying to sync my speed dial from Chrome.  Again, thanks everyone!

---

