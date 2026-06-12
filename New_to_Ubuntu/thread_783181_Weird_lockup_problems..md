---
title: "Weird lockup problems."
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Jaremasyder on 2008-05-05
I recently installed Ubuntu 8.04 a few days ago and haven't had any real problems until today. I ran a normal update and then my desktop panels just stopped responding. I can't launch any applications without them freezing up. Folders on my dekstop still seem responsive though. I've gotten to the point where I can boot up and everything works but the panel will hang whenever I try to launch something. I can't even launch terminal or anything like that. I've tried a couple fixes I've found on the forums here (using alt + f2 to try and turn the panel off) but those cause the same problem or nothing gets resolved. 

I'm running on an Asus G2S laptop with a GeForce 8600m

---

### Post by DrPppr242 on 2008-05-05
> **Jaremasyder said:**
> I recently installed Ubuntu 8.04 a few days ago and haven't had any real problems until today. I ran a normal update and then my desktop panels just stopped responding. I can't launch any applications without them freezing up. Folders on my dekstop still seem responsive though. I've gotten to the point where I can boot up and everything works but the panel will hang whenever I try to launch something. I can't even launch terminal or anything like that. I've tried a couple fixes I've found on the forums here (using alt + f2 to try and turn the panel off) but those cause the same problem or nothing gets resolved. 

I'm running on an Asus G2S laptop with a GeForce 8600m

you might try getting some output from log files and posting it, or the output of 'dmesg|tail', it's hard to know what caused the problem without knowing what was updated or what errors the system had.

---

### Post by Jaremasyder on 2008-05-05
```
[20.237953] sdhci: SDHCI controller found at 0000:09:01.1 [1180:0822] (rev 22)
[20.238026] ACPI: PCI Interrupt 0000:09:01.1[B] -> GSI 17 (level, low) -> IRQ 17
[20.238924] sdhci.slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[20.239050] mmc0: SDHCI at 0xfeaff400 irq 17 DMA
[20.339362] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[20.339773] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[20.648171] 1p: driver loaded but no devices found
[20.744713] Adding 7960168k swap on /dev/sda5. Priority:-1 extents:1 across:7960168k
[20.838460] EXT3 FS on sda1, internal journal
[21.090357] ip_tables: (C) 2000-2006 Netfilter Core Team
```

thats the output from dmesg|tail. The only way I can get into the terminal is by going itno the root in recovery mode, and I'm hopelessly lost there, but thats what came up.

---

### Post by mmb1 on 2008-05-05
I've heard that this is a common problem that some are experiencing with 8.04.  Have you filed a bug report?

---

### Post by Jaremasyder on 2008-05-05
where would I go to file a bug report? 

Also, is there a system restore, or a way to restore the os to its original settings? 

The only thing I can think of to get this to work at this point is just reinstall everything.

---

### Post by Rrory on 2008-05-05
I too partitioned and installed Heron 2 weeks ago and it was perfect. They I tried to download a firefox plug-in. Suddenly no sound. I uninstalled the plug-in and rebooted.
  Now the screen says Ubuntu is doing a disc scan but it's frozen. My windows XP runs just fine. 

So what should I do? And I'm such a noob please give me simple instructions. Heron is so very user friendly. I'm kind of shocked..
    Rory

Also, is there a system restore, or a way to restore the os to its original settings? 

The only thing I can think of to get this to work at this point is just reinstall everything.[/QUOTE]

---

