---
title: "Grub rescue with boot repair log, plz help"
date: 2016-03-24
forum: New to Ubuntu
---

### Post by jroenf on 2016-03-24
My problem: dual-boot (Windows 7 upgraded to 10 and Ubuntu 15.10) PC does not start up again. Grub-rescue prompt is visible.
I tried this to solve:
[LIST]
[*]I used an ubuntu startup usb to start ubuntu (15.10).
[*]I installed and ran boot-repair. System is still not starting up. Grub-rescue prompt visible.
[/LIST]
My boot-repair log is on [http://paste.ubuntu.com/15490942/](http://paste.ubuntu.com/15490942/)
What should I do to make grub work again (repair dual boot system)?

---

### Post by grahammechanical on 2016-03-24
You have the Linux bootloader installed into the MBR of the hard disk (sda) but you do not have Ubuntu installed any more. When Grub loads it looks for a configuration file called grub.cfg in the /boot folder of the partition that Ubuntu is one. As Ubuntu is not installed Grub cannot find its grub.cfg file that allows it to configure the boot menu. So, it goes into rescue mode.

I have heard that Windows 10 has a habit of re-writing the hard disk partition table and not including Linux partitions in the table. That could be the problem here.

Regards.

---

### Post by fantab on 2016-03-24
> **grahammechanical said:**
> I have heard that Windows 10 has a habit of re-writing the hard disk partition table and not including Linux partitions in the table. That could be the problem here.


Yep. That seems to the issue.
The following link has some tested methods to restore Ubuntu after Windows10:

[https://askubuntu.com/questions/655011/windows-10-upgrade-kills-grub-and-boot-repair-doesnt-help](https://askubuntu.com/questions/655011/windows-10-upgrade-kills-grub-and-boot-repair-doesnt-help)

---

### Post by jroenf on 2016-03-25
Thank you for your help so far.
> My problem: dual-boot (Windows 7 upgraded to 10 and Ubuntu 15.10) PC does not start up again. Grub-rescue prompt is visible.

I included OS versions for information, the problem did not start directly after system update (Windows 7 to 10) which I performed months ago. The problem started after I was working with Ubuntu and the electricity in my house went down. I fixed electricity, put the PC back on and got grub rescue. 
My question stays: how to proceed (in Ubuntu running from USB(?)) to make my PC startup again? 
Your link is to 
> 
restore Ubuntu after Windows10

which is not exactly my problem. Nevertheless I will research provided solutions there and report here.

---

### Post by LostFarmer on 2016-03-25
Your paste bin output list only 1 hdd (sda) and it has only NTFS MS Window partitions.  All sectors of that hdd are contained in the NTFS partitions with no space for any linux partitions.  If that system had linux , it has to be on a 2nd hdd that is not showing up.  So need for you to say if your system has in fact has 2 separate hdds ?  It make a big difference in needed trouble shooting.

If the problem is what the others are saying, (it can happen)  then there would be sectors that are free (not contained in the NTFS partitions) space between the stop sector of one partition and the start sector of the next partition, there are not.  The fdisk output agrees with the pbr (partition boot record) hex dump, they are NTFS.  The partition size reported by the MBR is checked with the partition size reported by the pbr, if they do not agree , the error will be listed.  It all points to no linux partitions are on sda, so the only option is a second hdd that I can think of.

---

### Post by jroenf on 2016-03-25
> So need for you to say if your system has in fact has 2 separate hdds ?
Yes, my system has in fact 2 separate hdds. Is one broken? 
My question stays: how to proceed (in Ubuntu running from USB(?)) to make my PC startup again?

---

### Post by LostFarmer on 2016-03-25
To get you comp to boot into MS WIndows  [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)  , you can use boot-repair and select 'Restore MBR' or use the terminal 'via command lines' and a few commands (all given in link).  That will replace the current grub boot code in the mbr with a simple code that will boot the partition with the boot flag set, your case sda2.  

Your linux hdd was not working when the pastebin was made.  You may just need to enter the bios and do a firmware reset ' with luck' , due to all Manufactures are different can not tell you just what needs done. Try that before anything else, it could fix all your problems.

---

### Post by fantab on 2016-03-26
Can you post a fresh BootInfo? You say you have two HDDs, however your first bootinfo shows only one HDD and a USb:

```
parted -l:

Model: ATA WDC WD20EARX-22P (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      1049kB  20.4GB  20.4GB  primary  ntfs         diag
2      20.4GB  20.5GB  105MB   primary  ntfs         boot
3      20.5GB  1010GB  990GB   primary  ntfs
4      1010GB  2000GB  990GB   primary  ntfs


Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 2004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      1049kB  2004MB  2003MB  primary  fat32        boot, lba
```

Grub is apparently installed but the Linux partitions are missing:
```

Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

```

Have you checked the HDD for any electrical damage?

---

### Post by jroenf on 2016-04-07
Thank you Lostfarmer, I will try the bios firmware reset and report back. I will [COLOR=#000000]use boot-repair and select 'Restore MBR' later, if other options fail.[/COLOR]

---

### Post by jroenf on 2016-04-07
Thank you Fantab,

I managed to get the second HDD (with ubuntu) spinning again. The HDD used to be in the swap tray accessed from the front of my PC, putting the hdd in the tray doesn't work anymore (PC sees no hdd). Obviously something is wrong with the hardware, I'll get someone to have a look at it.
I have put the HDD in a USB cradle, started Ubuntu from my USB stick. The hdd started spinning and I ran boot-repair again. Here is the new log with the hdd on it: [http://paste.ubuntu.com/15660915/](http://paste.ubuntu.com/15660915/) 
Can I restore my dual boot system with the hdd in the cradle?

---

### Post by oldfred on 2016-04-07
You now show sdh, but it is fully allocated with one NTFS partition.
No Linux partitions shown anywhere?

---

### Post by jroenf on 2016-05-03
Thanks all for your great help. I totally mixed up HDDs while trying to fix my computer. I found the ubuntu partition on another HDD. Also, my computer's front-loading HDD-tray (perhaps its power-supply) needs to be fixed by an expert.

---

### Post by him610 on 2016-05-04
To state the obvious, to avoid getting your swappable HDDs mixed up again, why not mark each with its own individual identifying label.

---

