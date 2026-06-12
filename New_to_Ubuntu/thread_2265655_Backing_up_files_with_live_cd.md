---
title: "Backing up files with live cd"
date: 2015-02-16
forum: New to Ubuntu
---

### Post by Crossbow on 2015-02-16
Please help!

Situation: 
- I can't get a GUI. I want to do a clean install. 
- I have so many photos on my hard drive, I haven't been able to back them up on line. I need to back them up on disks. 
- The last bootable CD I have is for Ubuntu 7.10.

I found this tutorial which seemed to be just what I needed: 
[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/")

but I got stuck at mounting the hard drive. The instructions there didn't work. 

```
root@ubuntu:~# mount -t vfat -o umask=000 /dev/sda1 /media/disk/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I found a thread with this issue from 2011 but it was never resolved: 
[http://ubuntuforums.org/showthread.php?t=1849547&page=2]("http://ubuntuforums.org/showthread.php?t=1849547&page=2")

What do I need to do now? 

Thanks!

Oh, PS. 

```

root@ubuntu:~# fdisk -l

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

```

---

### Post by Crossbow on 2015-02-16
Also, 

```
root@ubuntu:~# dmesg | tail
[  290.474779] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[  438.942031] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[  603.326574] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[  885.126285] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[  888.248147] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[  980.395191] FAT: Unrecognized mount option "unmask=000" or missing value
[ 2448.661218] FAT: bogus number of reserved sectors
[ 2448.661226] VFS: Can't find a valid FAT filesystem on dev sda1.
[ 5163.445860] FAT: bogus number of reserved sectors
[ 5163.445868] VFS: Can't find a valid FAT filesystem on dev sda1.

```

---

### Post by steeldriver on 2015-02-16
The /dev/sda1 partition has your ext3 Linux filesystem on it, you shouldn't be trying to mount it with type vfat. Try just

```

mount /dev/sda1 /media/disk

```

(it should be able to figure out the filesystem type automatically). If the /media/disk directory doesn't already exist you will need to create it first

```

mkdir -p /media/disk

```

---

### Post by SeijiSensei on 2015-02-16
Also you'll need to run both those commands with sudo like "sudo mount ...".

---

### Post by Crossbow on 2015-02-16
Actually I tried those first, as part of the procedure I linked to. 
```

ubuntu@ubuntu:~$ sudo /bin/bash
root@ubuntu:~# mkdir -p /media/disk
root@ubuntu:~# mount /dev/sda1 /media/disk
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:~#  dmesg | tail
[  888.248147] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[  980.395191] FAT: Unrecognized mount option "unmask=000" or missing value
[ 2448.661218] FAT: bogus number of reserved sectors
[ 2448.661226] VFS: Can't find a valid FAT filesystem on dev sda1.
[ 5163.445860] FAT: bogus number of reserved sectors
[ 5163.445868] VFS: Can't find a valid FAT filesystem on dev sda1.
[ 6408.276347] FAT: bogus number of reserved sectors
[ 6408.276355] VFS: Can't find a valid FAT filesystem on dev sda1.
[ 6495.757355] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[ 6768.324585] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
root@ubuntu:~# fdisk -l

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


```

---

### Post by steeldriver on 2015-02-16
OK let's assume it's actually ext**4** and try that explicitly:

```

mount **-t ext4** /dev/sda1 /media/disk

```

(that's probably what "unsupported optional features" is alluding to)

---

### Post by Crossbow on 2015-02-16
:(

```
root@ubuntu:~# mount -t ext4 /dev/sda1 /media/disk
mount: unknown filesystem type 'ext4'
root@ubuntu:~# 
```

---

### Post by steeldriver on 2015-02-16
In that case I suspect that Ubuntu 7.10 is simply too old for the job

---

### Post by Crossbow on 2015-02-16
Hmm. If that's the problem maybe I can burn a new disk from someone eles's computer. Thanks. I'll see if that works.

---

### Post by mastablasta on 2015-02-17
you could also try installing another GUI and then move the data. e.g. to install lubuntu-desktop package for example.

because I am not quite sure what this means: 
 - I can't get a GUI. I want to do a clean install.

also you don't need a live CD to mount disk in command line.

---

### Post by newb85 on 2015-02-17
7.10 would not have support for ext4, which is the filesystem for the newer releases.  Burning a new disc from someone else's machine wouldn't be a bad idea.

mastablasta's idea could work, too, depending why you can't get a GUI.  What happened that caused this problem?  Is it not something you can get around in recovery mode?  Can you still get to a terminal?

---

### Post by steeldriver on 2015-02-17
Also perhaps worth pointing out it doesn't need to be an Ubuntu live disc specifically - especially if you only have access to a CD (rather than a DVD), which the later desktop versions of Ubuntu don't fit on any more. You could even use something small and light like systemrescuecd:

[http://sourceforge.net/projects/systemrescuecd/](http://sourceforge.net/projects/systemrescuecd/)
[http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)

---

