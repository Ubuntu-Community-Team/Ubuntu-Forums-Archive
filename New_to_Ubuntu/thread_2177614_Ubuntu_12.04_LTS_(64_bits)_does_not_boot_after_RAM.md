---
title: "Ubuntu 12.04 LTS (64 bits) does not boot after RAM upgrade"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by Kees_Vis on 2013-09-29
Dear Community,

I've successfully installed Ubuntu 64-bit on a Dell Latitude E6510 with 2GB of RAM. Looks great! It is my plan however to run a virtualized windows 7 on top of Ubuntu for the programs which absolutely need windows (e.g. Outlook) and for this I've upgraded the RAM space to 8GB.

After the upgrade Ubuntu does not boot and ends in a panic: early exception 08 rip 246:10.
It does want to boot however when I add the boot command "mem=2048m", but this is off course not my intention. I've also upgraded the BIOS.

Another interesting thing is the result of the memtest86+ program. It fails with a memory error: too small lower memory.

Any ideas on this one.

Thanks in advance,
Kees

---

### Post by sandyd on 2013-09-29
> **Kees_Vis said:**
> Dear Community,

I've successfully installed Ubuntu 64-bit on a Dell Latitude E6510 with 2GB of RAM. Looks great! It is my plan however to run a virtualized windows 7 on top of Ubuntu for the programs which absolutely need windows (e.g. Outlook) and for this I've upgraded the RAM space to 8GB.

After the upgrade Ubuntu does not boot and ends in a panic: early exception 08 rip 246:10.
It does want to boot however when I add the boot command "mem=2048m", but this is off course not my intention. I've also upgraded the BIOS.

Another interesting thing is the result of the memtest86+ program. It fails with a memory error: too small lower memory.

Any ideas on this one.

Thanks in advance,
Kees

memtest error is a bug [https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/560839](https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/560839)

Have you tried testing the RAM (i.e. two at a time) to see if one of them is incompatible with the new RAM kit?

---

### Post by Kees_Vis on 2013-09-29
> **sandyd said:**
> memtest error is a bug [https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/560839](https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/560839)

Have you tried testing the RAM (i.e. two at a time) to see if one of them is incompatible with the new RAM kit?


Hello Sandyd, thanks for your reply!

It concerns a laptop with two mem banks for a total of 2 SO-Dimm's. Both original installed 1GB modules have been replaced by identical 4GB modules. I dont know how strict MS Windows 7 is on memory, but this runs without problems.

kind regards,
Kees

---

