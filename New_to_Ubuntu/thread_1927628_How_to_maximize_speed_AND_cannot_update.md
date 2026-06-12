---
title: "How to maximize speed? AND cannot update"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by SevenHundred on 2012-02-18
I'm running 11.10 on an old dinosaur of a computer, and (surprise) it's running very slowly. It was not this bad when I was using 11.04. I have very few files so I do not think that is the problem. Should I change to a different version of Ubuntu or is there something I can do now to speed it up?

Also, (and this is probably not helping my speed) I am not completely updated software-wise because anytime I try to download the 306 updates in my queue it gives me this message:

Failed to download package files

Check your Internet connection.


Any and all help for the newbie is appreciated.

---

### Post by josephmills on 2012-02-18
Hi there I was wondering if we could get some more info on your system ? could you please open your terminal (ctrl+alt+t) and enter in 
```
cat /proc/cpuinfo && free -m && lspci -nn && lsusb 
```
then paste that all here thanks.

---

### Post by SevenHundred on 2012-02-18
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.20GHz
stepping	: 9
cpu MHz		: 2193.567
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips	: 4387.13
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

             total       used       free     shared    buffers     cached
Mem:          1000        926         74          0         44        394
-/+ buffers/cache:        487        513
Swap:         1019         24        995
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 01)
00:02.0 Display controller [0380]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
01:04.0 PCI bridge [0604]: Pericom Semiconductor PI7C9X110 PCI Express to PCI bridge [12d8:e110] (rev 04)
01:09.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:00.0 VGA compatible controller [0300]: nVidia Corporation G98 [GeForce 8400 GS] [10de:06e4] (rev a1)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:1004 Dell Computer Corp. 
Bus 002 Device 003: ID 413c:2006 Dell Computer Corp. 
Bus 002 Device 004: ID 0461:4d46 Primax Electronics, Ltd 


Here you go. Hope it helps.

---

### Post by josephmills on 2012-02-18
I would wait for others but I suggest debian 6 or lubuntu 11.10. but that is just me. Like I said there will be others with info too... I hope this helps

---

### Post by SevenHundred on 2012-02-18
That does help, thanks.

---

### Post by 2F4U on 2012-02-18
If you want to stay in the Ubuntu family, I would suggest either Xubuntu or Lubuntu. Try the liveCD before you install and see how it goes. If you want to look outside of Ubuntu there are plenty of alternatives available. For older computers, you could go to distrowatch and search for distros dedicated to older hardware.

---

### Post by mörgæs on 2012-02-18
Small world: Right now I am using a Pentium 4, 15.2.9.

Confirming that Lubuntu works well.

---

### Post by SevenHundred on 2012-02-18
Thanks everyone, I will definitely try those ideas.

---

### Post by Paqman on 2012-02-18
Before doing anything else, try switching to Unity 2D instead of the default 3D. Log out and click the little cog by your username. With a bit of luck that'll be all you'll need to do.

---

