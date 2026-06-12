---
title: "32 bit or 64? Does it matter?"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by james104 on 2014-03-16
Hello,

The reason I ask is that in windows terms 64 bit is for when you wish to have more than the 4gb ram that 32 bit supports but what I seem to have done is install Windows 7 as 32bit since I only have 2gb ram and dual boot it with Ubuntu.

Under details in system settings my Ubuntu is 64 bit! I must have downloaded it by mistake, anyway I guess this isnt likely to cause any issues or complaints?

---

### Post by lisati on 2014-03-16
With recently built machines it doesn't really matter too much, they will run either 32bit or 64bit quite happily, but, as with Windows, using 64bit can make getting the most out of more RAM easier. 

It shouldn't matter too much if you use 64bit Ubuntu with less than 4Gb RAM: my day-to-day laptop runs 64-bit Ubuntu quite happily with only 2Gb RAM.

---

### Post by coldcritter64 on 2014-03-16
> **james104 said:**
> Hello,

...in windows terms 64 bit is for when you wish to have more than the 4gb ram that 32 bit supports...

With 32 bit linux installs a **pae** (physical address extension) kernel is usually available for larger RAM machines. I ran 32 bit Ubuntu Lucid (10.04) on a machine with 8 GB RAM with a pae kernel and had the full amount of RAM available to the installation. 

I now stick fully with the 64 bit installations, they are stable on my hardware and should be so on newer machines.

---

### Post by Impavidus on 2014-03-16
PAE makes more than 4GB memory available to the system on 32 bit systems, but not to individual processes. So if most of the memory is used by a single process (as is usually the case with me), pae doesn't help much. On the other hand, the same process takes more memory on 64 bits systems than on 32 bit systems, because the pointers (programming thing) are larger. I use 32 bit on 3GB memory but consider moving to 64 bit and adding some ram when 14.04 is released. They say that 64 bit is also a little faster.

---

### Post by 3rdalbum on 2014-03-16
64-bit Ubuntu is absolutely fine. Windows users don't like 64-bit because they remember the problems with 64-bit XP, but Linux has had perfect 64-bit compatibility since forever.

---

