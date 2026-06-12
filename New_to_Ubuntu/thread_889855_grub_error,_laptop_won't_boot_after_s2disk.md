---
title: "grub error, laptop won't boot after s2disk"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by leptons on 2008-08-14
Sorry for posting this support thread here. but for some reason, I cannot make new thread in the support forum.

I have a laptop with same specs as the old system 76 daru2.
I installed ubuntu hardy on it (nothing else) and it has never given me a problem.

I installed s2disk, s2ram and such and suspended my laptop about an hour ago. (s2disk has worked for me a couple times without problems)

after my lunch break, I boot up my laptop and it gives me error 2 at grub booting stage 1.5.

I'm very lost here. What exactly is wrong?
I'll have access to a live cd soon.

any comment or hints are appreciated.
Regards,
Leptons.

---

### Post by S.A.A on 2008-08-14
I really don't know what happened, but yoy can  simply reinstall "grub" from the live cd.

---

### Post by gardara on 2008-08-14
Take a look at this site, I've found it very helpful when I get into grub errors... [http://users.bigpond.net.au/hermanzone/p15.htm#2_](http://users.bigpond.net.au/hermanzone/p15.htm#2_)

---

### Post by Submatrix on 2008-08-14
whenever I have a problem with GRUB I use a SuperGRUB boot disk to force whichever partition to boot (bypass the MBR entirely) then fix the problem from inside the OS. Much easier :)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by leptons on 2008-08-14
thanks for the speedy reply. I now have access to a fedora live cd. I tried to load my /dev/sda harddrive by typing

su
mount -t ext3 /dev/sda /shared

however, the mounting failed and gives me
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
dmesg | tail gives me
VFS: Can't find ext3 filesystem on dev sda.
could it be a harddrive problem?

edit:
I've edited the /etc/fstab file according to other online website i found,
more /etc/fstab gives

/dev/mapper/livecd-rw   /                       ext3    defaults,noatime 0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
sysfs                   /sys                    sysfs   defaults        0 0
/dev/sda                /shared                 ext3    defaults        0 0

is there any reason /dev/sda isn't mounting?

---

### Post by leptons on 2008-08-14
also,
fdisk gives me:


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001123a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1946    15631213+  83  Linux
/dev/sda2            1947       19457   140657107+   5  Extended
/dev/sda5            1947       19457   140657076   83  Linux

Disk /dev/dm-0: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table


I'm really worried that if there might be anything wrong with my harddrive...
I can mount /dev/sda5 but not /dev/sda, /dev/sda1, and /dev/sda2.

my harddrive has 2 paritions, one for system install and one for personal files, /dev/sda5 is for my personal files.

---

### Post by leptons on 2008-08-14
I got home and put my gusty live CD in. The system loads fine but however, the / partition would not mount. The /home (the other partition mounts without problem). When I try to mount the / partition, I get the same error as before:

mount: wrong fs type, bad option, bad superblock on /dev/sda,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so


this is very frustrating.... does anyone know how to just mount my disk so I can perform changes on it?

any comment is appreciated. Thanks.

---

### Post by caljohnsmith on 2008-08-14
> mount -t ext3 /dev/[COLOR="Blue"]sda[/COLOR] /shared
You can't mount the HDD itself (sda), you have to mount a particular partition, like sda1, which is your bootable linux partition. :)

If you have any more file system problems, often fsck can fix them:
```
sudo fsck /dev/sda1
```

---

