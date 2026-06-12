---
title: "Windows XP &quot;No working init found&quot; Ubuntu Version 16.04.1"
date: 2018-12-17
forum: New to Ubuntu
---

### Post by the-blank-bear on 2018-12-17
I was trying to install Ubuntu Version 16.04.1 via CD into my Windows XP I believe its the Home version and after trying the demo, trying to install or testing the CD it showed an error saying**"[29.885764] ---[ end Kernel panic - not syncing: No working init found. Try passing init= option to kernel. See Linux Documentation/admin-guide/init.rst for guidance. [50.280077] random: crng init done"** after it shows this up on the screen it stops displaying anything else and doesn't do anything theirs more text above so here's the rest.
```
[      28.663292]  Initramfs unpacking failed: write error
[      29.916952]  Failed to execute /init (error -2)
[      29.917103]  Kernel panic - not syncing: No working init found. Try passing init= option to kernel. See Linux Document/admin-guide/init.rst for guidance.

[      29.917103]  CPU:  0 PID:  1 Comm: swapper/0 Not tainted 4.15.0-29-generic #31~16.04.1-Ubuntu
[      29.917233]  Hardware name: Hewlett-Packard HP Pavilion Notebook PC/N/A, BIOS GC.M1.63 01/01/1992
[      29.917288] Call Trace:
[      29.917368]   dump_stack+0*58/0*81
[      29.917424]   ? rest_init+0*10/0*90
[      29.917487]   panic+0*94/0*1e6
[      29.917533]   ? rest_init+0*90/0*90
[      29.917581]   kernal_init+0*da/0*fo
[      29.917635]   ret_from_fork+0*2e/0*38
[      29.917699]  Kernal Offset: 0*7000000 from 0*c1000000 (relocation range: 0*c0000000-0*do7effff)
[      29.917761] ---[  end Kernel panic - not syncing: No working init found.   Try passing init= option to kernel. See Linux Documentation/admin-guide/init.rst for guidance.
[      50.360077] random: crng init done
```


 and that's the whole error showing up on the screen directly from the Windows XP

---

### Post by TheFu on 2018-12-18
Welcome to the forums.

Ubuntu isn't a program to be installed into Windows.

It is a replacement operating system. 

The BIOS for that computer is from 1992!!!  Do you know which CPU it has?  I'm not certain that a CPU from that time period is supported by any Ubuntu.  A i686 CPU was the minimum for a long time. Using an expert install with the "alternate installer" ISO might be possible, but IDK.  A $25 Raspberry Pi v2 would probably be faster than a CPU from 1992.
There would be other challenges with a computer from that time.  In 1992, most computers had 4MB of RAM.  I think the minimum for any Ubuntu would be 512MB for a lite LXDE desktop Ubuntu.  No way would 4MB work.  I bought 8MB of RAM in 1992 for my system. It cost almost $700.  8MB won't work either.

Moving on ... Since WinXP hasn't been supported for years, don't expect anyone to have tested installing Ubuntu in a safe way onto the same disk.  Expect total data loss and make backups with that expectation.

Hopefully, you understand this and the technical accuracy of the first post is just off a little.  I can only assume that what you wrote is what you meant.

Anyways, if the computer has a Pentium CPU, the model would be good to know, then we can look up any support challenges. Knowing the amount of RAM inside the system would be important too.

---

### Post by the-blank-bear on 2018-12-18
thanks, I've been trying to solve this problem for a while now.I'll respond later with more information on my Windows XP as I don't have access to it at the moment.

---

### Post by oldos2er on 2018-12-18
What are the full hardware specs for this computer? If it's as old as TheFu suspects no modern OS is going to run on it.

---

### Post by the-blank-bear on 2018-12-18
Sorry, it took me a while to respond I just came back from school. It says it's a Windows XP Professional Version 2002 Service Pack 3 its processor is an Intel Celeron Processor with 796 MHz and 256 MB of ram.

---

### Post by TheFu on 2018-12-18
[https://www.intel.com/pressroom/kits/quickreffam.htm#Celeron](https://www.intel.com/pressroom/kits/quickreffam.htm#Celeron) doesn't show a CPU with that Mhz. Can you be more specific, please? It might not be possible.

I'm guessing it was in to 2000-2001 timeframe by the Mhz, but the BIOS from 1992 seems really odd.

With only 256MB of RAM, you'll have to stick with Lubuntu or something even lighter (which wouldn't be an Ubuntu desktop).  Something like TinyCore should work, however.

---

### Post by the-blank-bear on 2018-12-18
ok, thanks for helping me out with my Windows XP.

---

### Post by oldos2er on 2018-12-20
> **TheFu said:**
> With only 256MB of RAM, you'll have to stick with Lubuntu or something even lighter 

I'm aware of the minimum system requirements for Lubuntu, but personally I've found that running it on anything less than 1GB RAM painfully slow.

---

