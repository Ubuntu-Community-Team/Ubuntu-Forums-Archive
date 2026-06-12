---
title: "/dev/mapper/cryptswap1 no ready on startup"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by HappyPrime on 2013-01-20
Complete Ubuntu beginner here. Just installed ubuntu and have had this issue from the beginning.

Upon startup, I get flashed the message: The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present. Continue to wait, or Press S to skip mounting or M for manual recovery.

This quickly goes away and boots normally as far as I can tell. I'm just a little worried about this.

UPDATE:
Ok, after a fair bit of research I've found that most people suggest commenting out the "/dev/mapper/cryptswap1 none swap sw 0 0" line in /etc/fstab, however some people have stated that this merely masks the issue and doesn't actually fix the problem;
[For all the noobs like me out there, /etc/fstab is a FILE that can be opened in a text editor. /etc/fstab.d is a FOLDER (which for me is empty) and is not what you're looking for.]
This link is one of the ones that suggests commenting out the above line: [http://askubuntu.com/questions/56843/could-not-mount-dev-mapper-cryptswap1](http://askubuntu.com/questions/56843/could-not-mount-dev-mapper-cryptswap1)
However, it also propose a few checks. Here are the results when I run those checks:

Contents of /etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=88321295-bef2-4450-a039-05c598f37d00 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=218fc5d5-0014-49a7-8fbb-8bcd97300f36 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

ls -l /dev/disk/by-uuid/218fc5d5-0014-49a7-8fbb-8bcd97300f36
ls: cannot access /dev/disk/by-uuid/218fc5d5-0014-49a7-8fbb-8bcd97300f36: No such file or directory

If I just use "ls -l /dev/disk/by-uuid" I get:
total 0
lrwxrwxrwx 1 root root 10 Jan 21 10:30 62fe199b-0d25-41ca-9dac-ec64cbac268e -> ../../dm-0
lrwxrwxrwx 1 root root 10 Jan 21 10:30 88321295-bef2-4450-a039-05c598f37d00 -> ../../sda1
It doesn't seem to finding the swap partition at all, but as far as I can tell from other checks it is there.
e.g. "sudo fdisk -l /dev/sda" returns
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   296876031   148436992   83  Linux
/dev/sda2       296878078   312580095     7851009    5  Extended
/dev/sda5       296878080   312580095     7851008   82  Linux swap / Solaris
and "swapon -s" returns
Filename				Type		Size	Used	Priority
/dev/mapper/cryptswap1                  partition	7851004	0	-1


Basically I have no clue how to proceed.

---

### Post by verwaltungspraxis on 2013-10-10
I had the same issue. Eventually it turned out that the device in /etc/crypttab was wrong.

The system was installed from a USB pen-drive, so during installation the pen-drive was /dev/sda and the hard disc was /dev/sdb. The swap partition was hence written into /etc/crypttab as /dev/sdb6.
After booting from the harddrive this became /dev/sda6 and the mapper could not find it any more. 

To fix this just correct the line in /etc/crypttab to the correct /dev/sd?? or the UUID of the swap partition.

---

### Post by Dave_L on 2013-10-10
An article I read said that the message reflects a minor timing issue, and can be safely ignored.  I.e., "Continue to wait" is the best choice.

After boot, you can check that the encrypted swap is mounted properly:
```
$ swapon -s
Filename				Type		Size	Used	Priority
/dev/mapper/cryptswap1                  partition	2096444	965956	-1
```

Commenting out the /dev/mapper/cryptswap1 line in /etc/fstab doesn't seem like a good idea. Wouldn't that disable the encrypted swap partition?

---

