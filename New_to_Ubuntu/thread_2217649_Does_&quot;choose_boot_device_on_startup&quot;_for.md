---
title: "Does &quot;choose boot device on startup&quot; format the drive i choose?"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by DrBlade on 2014-04-18
Hello, i posted this question on ask ubuntu already, but no response :(, so i copy and paste it over here, maybe i will get more lucky.
This is a quick question.
[TABLE]
[TR]
[TD="class: votecell"]So when i choose my 250 gb drive (D : which i use, will it delete the  data? Also, i have another drive 150 (E: and C:, C: has windows 7 installed)  but the 150 drive got shinked to have 2 drives , if i choose the 150 gb  drive, will it choose all the 2 drives?

If you want more information, just reply! :P

[/TD]
[TD="class: postcell"][/TD]
[/TR]
[/TABLE]

---

### Post by DrBlade on 2014-04-18
Bumpin'

---

### Post by Mark Phelps on 2014-04-18
Unfortunately, you're mixing terms -- which makes it difficult to understand your question.  MS Windows contributes to this by calling "partitions" (a formatted space on a device) as a "drive"; whereas, here in Linux, we refer to "drives" as complete hardware devices.  In your case, "D", "D", etc are not "drives"; instead, they are "partitions".

You can't install Ubuntu to a Windows partition -- so basically, you can't choose "C", "D", or any other Windows partition.  Instead, you need to have unallocated space to be formatted into a Linux filesystem by the Ubuntu installer.

If you are being given the choice of shrinking a Windows OS by the Ubuntu installer, do NOT do that.  Doing that risks filesystem corruption on the Windows side.

If you are trying to install from INSIDE Windows, do NOT do that, either.  That uses Wubi, which has been discontinued.

So basically, it would be best if you told us what your goal was in this.  That way, we could better advise you.

We need to know what you're running at present -- Win7? Win8? XP?

Also, when in the Ubuntu destkop, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  This will list out the partitions and filesystems on your drive.  Post that information back here.

---

### Post by DrBlade on 2014-04-18
> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xca1cca1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18459c45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848    87629823    43711488    7  HPFS/NTFS/exFAT
/dev/sdb3        87631870   234440703    73404417    5  Extended
/dev/sdb5        87631872   213958655    63163392    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e03afd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32     2015231     1007600    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 4005 MB, 4005527552 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x022348e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63     7823295     3911616+   b  W95 FAT32

My goal is to install ubuntu 12.04.4 alongside **windows 7. **I made a free space and made a root and swap area, under it there is a [SIZE=2]bar which says: **"Choose**[/SIZE]** boot device on startup"**.
So i got alot of drives and partitions, i got a **drive 250 gb **which is my D: drive, and 120 gb drive which i **used to create 2 partitions C: and E:**. [B][U]My real questions is, if i choose 250 gb drive, will it delete all the stuff i have on it, or is it save to select it.
C: has windows 7 installed on it, and E just for the games i use, the C: partition is 45 gb, the E: partition is 64.7, i have plugged 2 usb, 1 usb which i got my ubuntu installer, and other has boot up booster on it.
I deleted the swap and root and the free space.

[/U][/B]

---

### Post by DrBlade on 2014-04-18
I have an idea, if i choose e partition, will it have the grub?

---

### Post by DrBlade on 2014-04-18
bumpin

---

### Post by oldfred on 2014-04-18
More just to restate what Mark Phelps said.

Ubuntu will not install to NTFS partitions or anything your call c:, d: or e:. You have to create unallocated space. And you need to use Windows 7 own partition tools to shrink which ever NTFS partition on which ever drive you want. Then you can install Ubuntu into the unallocated space as long as you have one primary partition left to use as the extended partition.

Since you have two drives, it often is better to have Windows on one drive and Ubuntu on the other drive. Then you keep Windows boot loader in the MBR of the Windows drive and can boot it without the other drive.
And you install the grub2 boot loader to the Ubuntu drive to boot Ubuntu. Grub can then be updated to include Windows as a boot option on the other drive, so you set BIOS to boot Ubuntu drive by default and get a grub menu to boot either Windows or Ubuntu. Only if major issues with Ubuntu drive, would you perhaps change BIOS or use the one time boot key to directly boot the Windows drive.

---

### Post by DrBlade on 2014-04-18
I will try that, thanks!

---

