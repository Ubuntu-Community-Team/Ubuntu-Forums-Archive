---
title: "Correct partition plan for ubuntu 12.04?"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by Halpm on 2012-07-14
Hello all,
I'm an absolute beginner at linux, newly converted from mac. I was trying to delete partitions to completely reformat an external hard disk using GParted, and I'd deleted a couple before I realised that I wasn't deleting partitions on my external drive, but on my system drive. I've included a screenshot from GParted to show what the partitions on the boot disk look like now - and what I'm really interested in is finding out how I can rebuild them with out having to reformat my disk, and reinstall my OS and all my applications. Hope some of you wise old (wo)men can help me out here :confused:

Edit: The computer still boots, but it tells me on bootup that discs aren't ready, and that I can either wait, press S to skip mounting or M to do something manually.

---

### Post by oldfred on 2012-07-14
Welcome to the forums.

You should be able to use testdisk from a liveCD to see old partitions.

If not rebooted recover partition:
[http://ubuntuforums.org/showpost.php?p=10364557&postcount=34](http://ubuntuforums.org/showpost.php?p=10364557&postcount=34)

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by ub07 on 2012-07-14
I dual boot with Windows (which you apparently do not), and my partition scheme looks roughly like this:

NTFS  (150 Gb)

/boot (150 Mb)

/swap  (12 Gb)

/       (88 Gb)

/home    (100 Gb)

---

### Post by NikTh on 2012-07-14
> **ub07 said:**
> I dual boot with Windows (which you apparently do not), and my partition scheme looks roughly like this:

NTFS  (150 Gb)

/boot (150 Mb)

/swap  (12 Gb)

/       (88 Gb)

/home    (100 Gb)

I think that so much swap (12GB) its wasted space. :)

---

### Post by Miljet on 2012-07-14
From your screen shot, it looks like possibly all you have deleted is your swap partition and the system is complaining that a swap partition isn't available on boot up. I would try creating a new swap before trying anything else.

Bear in mind that the newly created swap will probably have a different UUID and your /etc/fstab file will have to be edited.

---

### Post by Halpm on 2012-07-19
Ok guys - I think I've got the partition fixed - but it still doesn't recognise it at startup. Miljet said something about a /etc/fstab file. What's the story with that?

---

### Post by oldfred on 2012-07-19
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors  it just remounts everything, but if errors you have to fix before  rebooting or you may not be able to:
sudo mount -a

If you are creating a new swap and want to know its UUID.

sudo blkid -c /dev/null -o list

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6

---

