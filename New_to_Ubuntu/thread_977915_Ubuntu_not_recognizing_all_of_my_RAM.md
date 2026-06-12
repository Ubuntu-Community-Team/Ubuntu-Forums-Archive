---
title: "Ubuntu not recognizing all of my RAM"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by jlbr21 on 2008-11-10
Hi, I just installed 8.10 and Im dual-booting it together with Vista, my laptop is an HP Pavilion dv5-1095, has 320Gb HD, 4Gb Ram, Intel core 2 duo processor. Problem is, Ubuntu only recognizes 3 of the 4 Gb of Ram. Now, the machine came with 3 originally, but I bought a new ddr2 card, inserted it successfully, because I had been using it with Vista and it was recognized and I had no problems whatsoever.

Anybody knows how to fix this?

Thanks in advance!

---

### Post by MasterSander on 2008-11-10
check your bios settings, dunno if it'll help

---

### Post by -Zeus- on 2008-11-10
you have 2 options:  1, install the 64-bit edition of Ubuntu, probably the easier coice.  2, recompile your kernel with high memory support, if you choose to do this, a google search should pay dividends.

---

### Post by Joeb454 on 2008-11-10
Unless you installed the 64 bit version, this is perfectly normal. Did Vista recognize 4GB or 3.25GB?

---

### Post by jlbr21 on 2008-11-10
Yes, of course, thats the problem, so stupid of me, I had to install the 64 bit and I believe the Live CD I have is the i386.

Thank you all!

---

### Post by jlbr21 on 2008-11-10
ok, I jsut googled around a bit and realized its not so easy to uninstall ubuntu from a dual-boot, do you have any easy suggestions on how to uninstall without touching Vista?

---

### Post by unutbu on 2008-11-10
Um, I'm no expert at this, but I believe the 32-bit version of Ubuntu can access up to 4GB of RAM. 

See [http://fixunix.com/ubuntu/506776-32-bit-os-4-gb-limit.html](http://fixunix.com/ubuntu/506776-32-bit-os-4-gb-limit.html),
and in particular, post #2.

---

### Post by MasterSander on 2008-11-10
> **jlbr21 said:**
> ok, I jsut googled around a bit and realized its not so easy to uninstall ubuntu from a dual-boot, do you have any easy suggestions on how to uninstall without touching Vista?

It is easy, I just reinstalled 8.10 twice today, it won't touch vista nor will it touch the vista bootloader, it will write to the MBR (master boot record) and point to the grub (installed by default on every installation) and the grub should recognize vista immediatly and point to the right place, the only problem you can have with vista is that vista claims the boot is corrupted, just insert your vista install disk and click on repair and everything should work just fine

---

### Post by Keen101 on 2008-11-10
> install the 64-bit edition of Ubuntu, probably the easier coice. 2, recompile your kernel with high memory support

+1 ^

yeah, i've heard that you either need the 64bit version, or you need to recompile your kernel to support this if your really want 32bit.

If you want to just remove ubuntu really quick, then use this. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

just use gparted live-cd to remove the linux partitions, click apply, then reinstall ubuntu with "use largest continuous free space" option.

---

### Post by unutbu on 2008-11-10
If you only have 4GB of RAM, I think the machine would actually run slower under the 64-bit version, because every memory address would have to be shipped around as a 64-bit address, while only the lower 32-bits would actually get used. 

2^32 = 4GiB.

Even under 32-bit, you can add more swap space in addition to the 4GB of physical RAM, 
(again, see post #2 [http://fixunix.com/ubuntu/506776-32-bit-os-4-gb-limit.html](http://fixunix.com/ubuntu/506776-32-bit-os-4-gb-limit.html))
but I would venture to guess most users do not come anywhere close to using 4GB of RAM during normal usage, so unless you have a good reason, there is probably no need for a swap partition either.

---

### Post by abrussak on 2008-11-10
> **jlbr21 said:**
> ok, I jsut googled around a bit and realized its not so easy to uninstall ubuntu from a dual-boot, do you have any easy suggestions on how to uninstall without touching Vista?

You could try to just install right over...formatting just that specific partition where the 32bit version was installed. That SHOULD work :) I know I've done it before.

---

