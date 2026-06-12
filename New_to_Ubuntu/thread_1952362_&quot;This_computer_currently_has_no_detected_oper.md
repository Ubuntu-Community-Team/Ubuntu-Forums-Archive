---
title: "&quot;This computer currently has no detected operating systems&quot;"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by dmcff on 2012-04-04
I'm trying to install Ubuntu 11.10 on a dual boot system that currently contains an installation of Windows XP and another of Ubuntu 12.04 - I want to replace this with 11.10. while retaining the install of Windows XP.  However, the 11.10 LiveCD installer says that "This computer currently has no detected operating systems", and gives me only 2 options: 

1) Erase disk and install Ubuntu
2) Something else (manual partitioning)

The output of fdisk -l is:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00073acd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   157710104    78855021    7  HPFS/NTFS/exFAT
/dev/sda2       157704190   312576704    77436257+   5  Extended
/dev/sda3       311011328   312580095      784384   82  Linux swap / Solaris
/dev/sda5       157704192   311011327    76653568   83  Linux

Disk /dev/sdb: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          80    15663103     7831512    c  W95 FAT32 (LBA)


I'm wondering why the Ubuntu LiveCD installer apparently doesn't see the Win XP partition on sda1?

---

### Post by shymega on 2012-04-04
Hi, I've noticed that you have a device mounted at /dev/sdb.

Providing you are installing from CD, could you attempt to unplug the device and try again?

Thanks,
sm.

---

### Post by dmcff on 2012-04-04
With the device unplugged (it's an 8Gb USB Lexar flash drive), the result is the same: I get the same two options, and the message that "this computer currently has no detected operating systems".

---

### Post by shymega on 2012-04-04
Can you try Manual Partitioning and see if they WinXP is visible there please?

---

### Post by dmcff on 2012-04-04
In the manual partitioning screen there's an entry for /dev/sda - i.e. the 160Gb disk.  It's the only entry there.

---

### Post by dmcff on 2012-04-04
There are one or two other threads about this topic, but they date from several years ago. e.g.

 [http://ubuntuforums.org/showthread.php?t=1132131](http://ubuntuforums.org/showthread.php?t=1132131)

and don't seem very conclusive, as far as I can see,

---

### Post by shymega on 2012-04-04
Is is at all possible for you to take a screenshot of the partitions on the installer for me and attach it to your post?

I wouldn't normally ask, but it would help to have a visual view of what's going wrong on your installer.

Cheers,
SM

---

### Post by oldfred on 2012-04-04
I have had gparted not even show my sda drive which then only had XP. Even though XP would boot. But then I ran chkdsk, XP booted a bit faster and gparted would show sda drive.

You might try running chkdsk on the NTFS partition from your XP install disk.

---

### Post by dmcff on 2012-04-04
> **shymega said:**
> Is is at all possible for you to take a screenshot of the partitions on the installer for me and attach it to your post?


It's not really a screenshot, more like a snapshot :-) - but here it is, anyway.

---

### Post by shymega on 2012-04-04
Yes, that is a bit odd.

I would suggest what oldfred suggested and run chkdsk on your WinXP system. It might be worth a try. When booted into WinXP as the admin user, go to the command prompt and type ```
 chkdsk c: /r
``` type Y in response the question about the volume being in use, hit enter and restart. If you could then attempt to run the Ubuntu installation again and report back.

Cheers,
SM

---

### Post by dmcff on 2012-04-04
Chkdsk /r/f didn't find any errors in the drive (except for flagging the "volume bitmap" error message which Microsoft say it's safe to ignore), and chkntfs says that the drive is not dirty.

So I don't know what to try next. It's true that the hard disk is quite old (six years), and maybe it's just starting to wear out?

---

### Post by dmcff on 2012-04-04
Also, Ubuntu's "Something Else" install screen still takes me to the same partition table as before: /dev/sda - and all the rest is blank.

---

### Post by oldfred on 2012-04-04
I thought fdisk gave an overlapping error so we knew to check math.

/dev/sda1   *          63   [COLOR=Red]157710104[/COLOR]    78855021    7  HPFS/NTFS/exFAT
/dev/sda2 [COLOR=Red]      157704190[/COLOR]   312576704    77436257+   5  Extended

(also sda5 which is in sda2 has same start)

It looks like sda1 ends after the start of sda2. The issue then is should sda1 be shorter or sda2 start later. And if you have data from both in the overlap you will have problems. Back up everything that is important.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

You can edit the PTsda.txt file as it is just text and read the corrected data back in. You may be able to use Testdisk to show old partition layout and recover that but again any overlap change may cause data loss.

Fix overlaping partition error srs5694 post #34
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)

Use sfdisk to edit partitions and links to how to convert primary/logical
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
sfdisk to fix extended beyond end -partition outside the disk!
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by shymega on 2012-04-04
Hm. Okay This does sound rather odd but I would give oldfred's suggestion a try as I am at a loss of what to try next but wish all the luck in fixing your problem.

Thanks,
SM

---

### Post by dmcff on 2012-04-04
> **oldfred said:**
> I thought fdisk gave an overlapping error so we knew to check math.

/dev/sda1   *          63   [COLOR=Red]157710104[/COLOR]    78855021    7  HPFS/NTFS/exFAT
/dev/sda2 [COLOR=Red]      157704190[/COLOR]   312576704    77436257+   5  Extended] 


Thanks for checking this, oldfred. Yes, it does look as though there may be something wrong with the partition table. There is really very little material on that computer that's of much importance, so it doesn't matter if things get messed up a bit, though I want to preserve the dual boot system if I can. I'll try to do the editing you recommend, but it may take some time to find a solution - if I do find one, I will mark this thread as SOLVED.

---

