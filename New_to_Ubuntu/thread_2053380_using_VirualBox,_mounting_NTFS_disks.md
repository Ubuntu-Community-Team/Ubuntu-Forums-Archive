---
title: "using VirualBox, mounting NTFS disks?"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by deeppow on 2012-09-05
I've used Ubuntu/Linus off and on but haven't worked with it for awhile.  This time around I've installed 12.04.1 within VirtualBox on Windows 7 64bit.

Within Ubuntu, how do I see/mount NTFS drives that are part of Windows7?  Appears Ubuntu sees only itself.

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000d526

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    15728639     7863296   83  Linux
/dev/sda2        15730686    16775167      522241    5  Extended
/dev/sda5        15730688    16775167      522240   82  Linux swap / Solaris


Thanks for any help!

---

### Post by Morbius1 on 2012-09-05
Start VBox
Right Click the Ubuntu Virtual Machine
Select - Settings > Shared Folders > Add

Then add the "drives" you want to mount within Ubuntu

When you start the Ubuntu virtual machine your Windows partitions will be mounted automatically to: **/media/sf_xxxxx**

You may have to make yourself a member of the vboxsf group in Ubuntu:
```
sudo gpasswd -a your-user-name vboxsf
```Then logoff ( the guest ) and login again.

---

### Post by deeppow on 2012-09-05
Thanks Morbius1 but when I have VM running, the settings are gray (unavailable) for Ubuntu.  It shows "Shared Folders" in what appears to be its attributes but I don't seem to be able any folders to share.  VM help doesn't shed any light on the problem.

I'm probably doing something dum.

---

### Post by deeppow on 2012-09-05
Got it, you have to have Ubuntu running too.  Kinda obvious when you think about it.

Thanks again.

---

