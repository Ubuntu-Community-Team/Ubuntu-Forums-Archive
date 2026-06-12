---
title: "[SOLVED] After a power down the problem started..."
date: 2008-09-03
forum: New to Ubuntu
---

### Post by vasiauvi on 2008-09-03
Hello everyone,
After the power was off from the main energy provider I have some problems:
- my NTFS drives doesn't appear enymore on my descktop and I can't acces them.
- my desktop background has disapeard and now i have only a brown descktop
- my TV tuner doesn't work anymore--but this is happening after the update from yesterday: "linux headers xxxx"

How can i find out wat is wrong and what have happened?

Thanks!!

---

### Post by vasiauvi on 2008-09-03
I have tried this :[http://ubuntuforums.org/showthread.php?t=802699](http://ubuntuforums.org/showthread.php?t=802699)
 but when I click on Places-->NTFS partision it's saing that I don't have the permission to mount the volume!!!
Also puted the ```
/dev/sda1 /media/backup ntfs defaults,umask=007,gid=46 0 0 
``` in the fstab and when I rebooted an error ocured.

---

### Post by halitech on 2008-09-03
> **vasiauvi said:**
> Hello everyone,
After the power was off from the main energy provider I have some problems:
- my NTFS drives doesn't appear enymore on my descktop and I can't acces them.
- my desktop background has disapeard and now i have only a brown descktop
- my TV tuner doesn't work anymore--but this is happening after the update from yesterday: "linux headers xxxx"

How can i find out wat is wrong and what have happened?

Thanks!!

was your background picture saved on the ntfs drive? if so thats why its not showing anymore

can you open a terminal and post back the results of
```
sudo fdisk -l
```that's a lower case L, not the number 1

> in the fstab and when I rebooted an error ocured.
what was the error you got on reboot?

---

### Post by vasiauvi on 2008-09-03
The result of sudo fdisk -l:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00a300a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       24320   174867525    f  W95 Ext'd (LBA)
/dev/sda5            2551        8924    51199123+   7  HPFS/NTFS
/dev/sda6            8925       24320   123668338+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6e69b11

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         892     7164958+  83  Linux
/dev/sdb2             893        4865    31913122+   f  W95 Ext'd (LBA)
/dev/sdb5             893        1016      995998+  82  Linux swap / Solaris
/dev/sdb6            1017        4865    30917061   83  Linux

---

### Post by vasiauvi on 2008-09-03
The background is in Linux partition but I have puted again and now has appeard.Hoppely is there after tne next restart!

---

### Post by halitech on 2008-09-03
try the instructions here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

looks like windows is installed on the primary master and it is being seen so that is a good thing.

---

### Post by vasiauvi on 2008-09-03
I have done like it's sais in that link but didn't worked.
When I have put : sudo mount -a   this apeared:
```
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/hda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/hda1 ntfs-3g force 0 0
```
But i don't really understand what I have to do :confused:

---

### Post by vasiauvi on 2008-09-03
OK, I have entered in WinXP and propely shut down the PC and entered back in Ubuntu and now I have all the NTFS drives. :) Now I have only to resolv the TV tuner.

---

