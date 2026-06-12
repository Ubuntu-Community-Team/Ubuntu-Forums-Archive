---
title: "unable to update ubuntu and read or write in windows common drives"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by baijopjoy on 2013-03-15
hi all,
i am facing a problem, i am unable to update my system.
when i am using software update i'm getting an error message please check your internet connection
but i am having a working connection

and also i am unable to write files in my windows common drives
please help

---

### Post by Mark Phelps on 2013-03-15
The second problem can be due to a variety of issues ...

First -- hibernation.  If you are hibernating Window and THEN, trying to write to any paritions that Windows uses, while Windows is hibernated, that will not work.  Even if it does look like it works, it doesn't -- as when you boot back into MS Windows, the files you created will be gone.

Second -- mounting.  If you're mounting NTFS partitions from inside Ubuntu, anytime those filesystems get corrupted, after that, Ubuntu will only mount them read-only, preventing you from writing to them. The safe thing to do, since Linux has no real tools for doing this, is to boot into Windows and run CHKDSK on those partitions -- which you do from Computer, right-click that "drive", look at Properties, and select the option to scan the drive for errors.

Third -- you should NOT write to your Windows OS partition from inside Ubuntu, even if you can.  This risks corrupting Windows and rendering it unbootable.  Writing to data partitions, is OK, but not to OS partitions.

---

### Post by baijopjoy on 2013-03-15
the issue is there with data partition also.
and i have not windows in between

---

### Post by Mark Phelps on 2013-03-15
You don't have to be in Windows "in between" ...

You need to tell us whether or not you're hibernating windows.

Also, what IS the issue?  Your thread title says you can't read or write, but your text in the first post only says you can't write.

Open a command window and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions and filesystems on your drive.

---

### Post by baijopjoy on 2013-03-15
phelps,
 thank you for responding
the issue is only about writing
and when i am using the command which you have given i am getting an error message as "sudo: [COLOR=#000000]fdisk -lu: command not found[/COLOR]

---

### Post by baijopjoy on 2013-03-15
sudo fdisk -lu
result

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x7ee618ea


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   981161983   490477568    7  HPFS/NTFS/exFAT
/dev/sda3       981161984  1660159593   339498805    7  HPFS/NTFS/exFAT
/dev/sda4      1660159998  1953523711   146681857    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1660160000  1937307647   138573824   83  Linux
/dev/sda6      1937309696  1953523711     8107008   82  Linux swap / Solaris

---

### Post by Mark Phelps on 2013-03-16
Did you do the CHKDSK I suggested on the Windows partitions? You need to do that to identify and fix any filesystem errors.

How are you trying to mount the drives? Are you clicking on the filesystem icon?

Are you trying to write to sda1? Or, are you trying to write to sda2?

---

### Post by baijopjoy on 2013-03-16
i am mounting directly from the home window.
explorer bar
i couldn't try chkdsk in windows

---

### Post by baijopjoy on 2013-03-16
thank you phelps
i tried chkdsk and it worked
but still unable to update ubuntu

---

