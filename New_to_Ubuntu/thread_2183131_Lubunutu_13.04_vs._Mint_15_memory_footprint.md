---
title: "Lubunutu 13.04 vs. Mint 15 memory footprint"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by rogersma on 2013-10-23
I was thinking of replacing Mint on my desktop with Lubuntu, mainly because all else being equal, I prefer efficient software and Lubuntu is advertised as being super-efficient.

However, on a simple test I found that it isn't even as memory-efficient as Mint?  I booted my machine from the Lubuntu USB and ran 'top' in a Terminal window.  It consumed slightly more than 1GB of RAM -- more than I expected, so I removed the USB and rebooted with native Mint from my hard drive.  Mint takes only 740MB.  Even with Firefox up playing a flash video, Mint is still well under 1GB memory.

What gives?  I thought Lubuntu was supposed to be super-efficient.  Is this not a fair test?  Should it be USB vs. USB?

Just curious -- thanks for reading!

---

### Post by philinux on 2013-10-23
Not a fair test at all as you rightly point out. 

If you want small efficient try peppermint os.

---

### Post by grahammechanical on 2013-10-23
How can it be a fair test? Unless you are using the Lubuntu USB as a USB hard disk then runing a live session against a hard disk install is not a fair test because the live session runs in memory.

My machine has 1GB and I have seen a 10% - 15% drop in memory usage from 12.04 to 13.04 and on to 13.10. Ubuntu makes good use of cache memory. Make sure that any measurement is not including cache memory as used memory.

Regards.

---

### Post by newb85 on 2013-10-23
Indeed.  You'll notice that a Live USB can be installed on a 1GB disk.  However, installation to a HDD requires almost 5GB.

---

### Post by buzzingrobot on 2013-10-23
The biggest memory users are your applications, regardless of the interface in use.

Lubuntu runs the same kernel and, on the same hardware, the same drivers as any other version of of Ubuntu.

so, you don't gain anything from the applications, and you don't gain anything from the kernel or from the drivers. What's left? Not all that much.

Memory use also varies from configuration to configuration.  

The only way to know what's more efficient on your hardware, running you applcations, is to install different interfaces, measure the memory use, and compare the results.

That said, if you have sufficient memory, you really gain little by trying to be a memory piper other than having a lot of unused memory hanging around.

---

### Post by rogersma on 2013-10-24
Ok, thanks folks -- I suspected I was doing something wrong!

---

