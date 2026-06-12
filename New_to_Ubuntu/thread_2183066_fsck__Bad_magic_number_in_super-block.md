---
title: "fsck : Bad magic number in super-block"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by valex2 on 2013-10-23
I have a 30 GB MAXTOR 53073H6(DAC10S0C) ATA Hard Disk and I tried to install Hac..(caugh caugh) I mean Macintosh on it. But Snow Leopard's Disk Utility can't mount / partition or format it. It gives me lots of errors and if I set the partition table to MBR or GUID and try to make a HFS+ (Mac Extended OS Journaled or just Extended) partition the process just freezes at "partitioning" or "creating partition table". The First aid tool gives this output:
Checking Catalog file.
Invalid B-tree Header (in red meaning this is the problem)
...(and other lines in which it says that the disk is successfuly repaired- but it's not)
Other time the output was this:
The volume OSX needs to be repaired
Error: Filesystem verify or repair failed. (in red)

When i try to mount the disk it gives me: 
Mount failed
The disk "disk0s3" could not be mounted.
Try running First Aid on the disk and then retry mounting.
But the Verify disk and Repair disk are greyed out. So i can't select them.
 
I was able to make a HFS+ partition and set the partition table to mac with Trisquel's Gparted (after I installed hfsprogs) and I tried again to install OSX but again disk utility shows only the drive and no partition and I'm back to square one.
Then I typed in terminal: 
fsck.hfs /dev/sde (in mac's terminal i tried  fsck_hfs /dev/disk0
both give this output: 
** /dev/sde (or /disk0 on mac)

Fsck /dev/sde gives this output:
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sde


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


I tried to find the alternate superblocks so i typed: 
[COLOR=#333333]mke2fs -n /dev/sde 
output:[/COLOR]
First data block=0
Maximum filesystem blocks=0
224 block groups
32768 blocks per group, 32768 fragments per group
8176 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000

I tried e2fsck -b _______ /dev/sde  with every alternate superblock but it just gives:
 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

I don't know what to do other than give up.(I don't want to do that). Maybe you could help me.
I heard that DiskWarrior is capable of solving this kind of problems but i can't run it since I don't own a real Macintosh and I don't know anyone with one.
I posted this here because I heard that people on Ubuntu Forums are good at solving problems.
Please excuse my sh*ty english (i'm not a native speaker).

---

