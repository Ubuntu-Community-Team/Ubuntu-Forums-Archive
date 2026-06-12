---
title: "Backing up files with live cd"
date: 2015-02-16
forum: New to Ubuntu
---

### Post by Crossbow on 2015-02-16
Please help!

Situation: 
- I can't get a GUI. I want to do a clean install. 
- I have so many photos on my hard drive, I haven't been able to back them up on line. 
- The last bootable CD I have is for Ubuntu 7.10. 

I found this tutorial which seemed to be just what I needed: [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/")

but I got stuck at mounting the hard drive. The instructions there didn't work. 

[b]root@ubuntu:~# mount -t vfat -o umask=000 /dev/sda1 /media/disk/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/b]

I did find this exact question on a thread from 2011 but it was never resolved. 

What do I need to do now? 

Thanks!

Oh, and:  

[b]root@ubuntu:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30020   241135618+  83  Linux
/dev/sda2           30021       30394     3004155    5  Extended
/dev/sda5           30021       30394     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 517 MB, 517472256 bytes
65 heads, 63 sectors/track, 246 cylinders
Units = cylinders of 4095 * 512 = 2096640 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         245      501216+   4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 64, 63) logical=(244, 52, 40)
root@ubuntu:~# 
[/b]

---

### Post by coffeecat on 2015-02-16
Duplicate here:

[http://ubuntuforums.org/showthread.php?t=2265655](http://ubuntuforums.org/showthread.php?t=2265655)

Please do not post duplicate threads.

Closed.

---

