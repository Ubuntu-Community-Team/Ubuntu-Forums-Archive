---
title: "[SOLVED] GParted reports device busy or fs mounted"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-11-15
While in LiveCD session, using GParted to first move unused space to "rear" of drive and then grow /sda3 to absorb unused space, GParted says:

ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda3
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Group descriptors look bad... trying backup blocks...
Corruption found in superblock.  (blocks_count = 0).

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 32768 <device>

ubuntu@ubuntu:~$ sudo e2fsck -b 32768 /dev/sda3
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sda3
Filesystem mounted or opened exclusively by another program?

GParted seems to have moved about 64 gig to the 'rear', and shows it as unallocated, when I try to grow /sda3 into it, it balks. Anybody know what to do.

---

### Post by taurus on 2008-11-15
Post the screenshot of gparted and the output of this command from a terminal, from the LiveCD.

```
df -h
```

p.s.  Looks like you have been playing around with your harddrive lately.  If you can back up your personal files in $HOME, maybe your best bet is to reinstall the whole thing so you can resize what partitions to whatever your heart desires.

---

### Post by Mark_in_Hollywood on 2008-11-15
> **taurus said:**
> Post the screenshot of gparted and the output of this command from a terminal, from the LiveCD.

```
df -h
```

p.s.  Looks like you have been playing around with your harddrive lately.  If you can back up your personal files in $HOME, maybe your best bet is to reinstall the whole thing so you can resize what partitions to whatever your heart desires.

there is no output from df -h, as the /dev/sda3 won't mount. /sda3 is where gparted balked.

I saved the GParted error output:

GParted 0.3.5

Libparted 1.7.1

Grow /dev/sda3 from 220.81 GiB to 285.43 GiB  00:00    ( ERROR )
     	
calibrate /dev/sda3  00:00    ( SUCCES )
     	
path: /dev/sda3
start: 20482875
end: 483556499
size: 463073625 (220.81 GiB)
calculate new size and position of /dev/sda3  00:00    ( SUCCES )
     	
requested start: 20482875
requested end: 619080839
requested size: 598597965 (285.43 GiB)
new start: 20482875
new end: 619080839
new size: 598597965 (285.43 GiB)
check filesystem on /dev/sda3 for errors and (if possible) fix them  00:00    ( ERROR )
     	
e2fsck -f -y -v /dev/sda3
     	
e2fsck: Group descriptors look bad... trying backup blocks...
Corruption found in superblock. (blocks_count = 0).

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 32768 <device>

e2fsck 1.40.8 (13-Mar-2008)

AND

ubuntu@ubuntu:~$ dmesg | tail
[ 5871.484229] cdrom: sr0: mrw address space DMA selected
[ 5872.010446] cdrom: sr0: mrw address space DMA selected
[ 5872.749666] cdrom: sr0: mrw address space DMA selected
[ 9756.942433] kjournald starting.  Commit interval 5 seconds
[ 9756.947321] EXT3 FS on sda1, internal journal
[ 9756.947334] EXT3-fs: mounted filesystem with ordered data mode.
[ 9759.581590] EXT2-fs error (device sda3): ext2_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[ 9759.581604] EXT2-fs: group descriptors corrupted!
[11218.005948] EXT2-fs error (device sda3): ext2_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[11218.005961] EXT2-fs: group descriptors corrupted!

---

### Post by Mark_in_Hollywood on 2008-11-17
I've done a clean install.

---

