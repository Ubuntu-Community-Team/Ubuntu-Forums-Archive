---
title: "32 bit and 64 bit"
date: 2012-04-26
forum: Recurring Discussions
---

### Post by StatusFresh on 2012-04-26
I have a 64 bit operating system and my processor came out like 3 months ago and my laptop is 6 GB RAM.  Do I install the 64 bit or 32 bit ubuntu? What is the difference between them, and is there any performance issues with 64 bit?

---

### Post by TBABill on 2012-04-26
If you scroll through new posts on the forum you'll see this same question answered in many different threads. Wikipedia and a plethora of other sites can also provide detailed answers on the differences. In my mind, if your machine has 3+ GB RAM and is 64 bit capable, go for it. No issues running 64 bit for years on any machine.

---

### Post by techsupport on 2012-04-26
> **StatusFresh said:**
> I have a 64 bit operating system and my processor came out like 3 months ago and my laptop is 6 GB RAM.  Do I install the 64 bit or 32 bit ubuntu? What is the difference between them, and is there any performance issues with 64 bit?

Use 64-bit:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

### Post by oldfred on 2012-04-27
Moved to recurring discussions.

Why Ubuntu offically suggests 32bit (25% have 32bit systems)
[https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035088.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035088.html)

Essentially says if you can use the 64bit kernel you should.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

With a new system, is it UEFI or BIOS, and MBR or gpt, as how you install makes a big difference. 
If you do not know then you probably are BIOS as most UEFI systems will boot in BIOS mode and if BIOS and you have Windows then you have MBR. gpt has to be used with UEFI for Windows. Ubuntu will use gpt with BIOS or UEFI but additional partitions are required.

---

