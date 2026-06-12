---
title: "Boot flag is showing for swap"
date: 2016-11-18
forum: New to Ubuntu
---

### Post by lnux12 on 2016-11-18
I was facing grub rescue error and during resolution When i run ```
sudo fdisk -l
``` its output shows

  ```
Disk /dev/sda: 320.1 GB, 320071851520 bytes
224 heads, 19 sectors/track, 146884 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x193d4ca9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     7999487     3998720   82  Linux swap / Solaris
/dev/sda2         8001534   625134047   308566257    f  W95 Ext'd (LBA)
/dev/sda5       204798739   409597439   102399350+   7  HPFS/NTFS/exFAT
/dev/sda6       409597459   625134047   107768294+   7  HPFS/NTFS/exFAT
/dev/sda7         8001536   204797951    98398208   83  Linux
```


During installation,I just make standard installation, not manual partition. As I know, boot flag indicate to which partition to boot. And here it is linux swap but it should be for Linux Id 83. I think i am missing concept or something else. Is it correct or wrong? Where should be a boot flag?

---

### Post by Impavidus on 2016-11-18
grub doesn't use the boot flag. The Windows boot loader needs it and it's said that some bioses want a boot flag or they won't try and boot from a particular hard drive, but grub should ignore the boot flag.

I see you have some ntfs logical partitions. Are you dual booting or have you got multiple hard drives? Windows doesn't like booting from logical partitions and using ntfs on a Linux-only computer isn't a good long term solution.

Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), create a boot-info summary and post the link here so we can see details.

---

### Post by oldfred on 2016-11-18
Did you convert your Windows boot partition to swap?
Windows only boots from primary NTFS partition and that usually is sda1 with boot flag.
You may be able to convert back to NTFS type 07 with disks, if swap not used. If used the it overwrote your NTFS boot data.

---

### Post by lnux12 on 2016-11-18
I had already tried a boot-repair but it did not work for me still issue was the same. Applied all the solution answer posted on askubuntu and ubuntuforums: Tried to mount the partition using Ubuntu live CD but it shows write protected, tried fsck but nothing worked. Also tried in Windows with chkdsk but it shows ***chkdsk does not support raw***. So at the end I used ***ddrescue*** to recover my data which recovered successfully. Only boot flag concept was making me confused. 

In many systems i have installed ubuntu, in all boot flag is for linux Id 83.

In my case, I was given 320 GB of hdd by sys admin in which two partition was already there and the remaining 100 GB partition, linux mint was installed and i had installed ubuntu in that 100 GB partiton a year ago. So there might be windows installed before linux mint. I can see data of other two partition using live cd, only ubuntu installed partition is corrupted.

---

