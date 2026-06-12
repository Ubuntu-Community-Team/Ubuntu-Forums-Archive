---
title: "Grub Problem"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by tiger1550 on 2012-03-06
Hi Everybody , its the first time i post something here because its the first time i have a problem like this .

i installed windows after installing kubuntu ,i went back the live cd to instll my grub but i have an issues at first because i used 9.10 and i had 11.10  installed , any way i tried to install my grub on sda6 and nothing happened and that made me install it on sda1  and that was the chaos ( sda1 was windows boot manager partition )

255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8ffe8ffe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2   *      206848    94244863    47019008    7  HPFS/NTFS/exFAT
/dev/sda3        94244864   251529215    78642176    7  HPFS/NTFS/exFAT
/dev/sda4       251533310   488396799   118431745    f  W95 Ext'd (LBA)
/dev/sda5       251533312   420290559    84378624    7  HPFS/NTFS/exFAT
/dev/sda6       420292608   488396799    34052096   83  Linux

which was my big mistake then i pluged the ethernet and installed the grub  and every thing was fine ,until when i booted i didn't found windows choice from the list , i have tried more than time and lastly i found that sda1 is the bootmanager partition for windows 7 i formated it on linux and restarted installed the windows boot manager  and tried windows and started it  and then reinstalled the grub and re-restarted and i found that when i choose windows the windows BOOTMGR is missing i repeated the scenario more than one time and every time this happen the windows boot manager got installed and the grub installed and after then the windows boot manager files got lost 

i will attach the Result.txt of the boot_info_script.sh bash to make it easy for you to figure it out BTW that Result before then was screwed quit well before and sda 1 had a boot grub installed in it

---

### Post by kazztan0325 on 2012-03-07
Hi tiger1550,

I think, you should have installed Windows 7 first, and then should have installed Kubuntu after installing Windows.

---

### Post by lindsay7 on 2012-03-07
you can do this.....

[http://www.webupd8.org/2009/12/how-t...ub2-linux.html](http://www.webupd8.org/2009/12/how-t...ub2-linux.html)

or you can download and burn a iso disk of "Boot - Repair" and run it.
[http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html](http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html)

---

### Post by ixtok on 2012-03-07
Sometimes it is just as easy to start over, load windows letting it take the whole HD then load ubuntu.

---

### Post by ixtok on 2012-03-07
Sometimes it is just as easy to start from scratch, load windows letting it use the whole drive, then install ubuntu.

---

