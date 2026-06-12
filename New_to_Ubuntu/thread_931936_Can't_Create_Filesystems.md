---
title: "Can't Create Filesystems"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by WhyCantEveryOSBePerfect on 2008-09-27
ubuntu@ubuntu:~$ sudo fdisk /dev/mapper/isw_diihdeefba_RAID0

The number of cylinders for this disk is set to 48641.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/mapper/isw_diihdeefba_RAID0: 400.0 GB, 400093872128 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2363eab2

                            Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_diihdeefba_RAID0p1               1        1786    14346013+   7  HPFS/NTFS
/dev/mapper/isw_diihdeefba_RAID0p2   *        1787       46031   355391264    7  HPFS/NTFS
/dev/mapper/isw_diihdeefba_RAID0p3           46032       48269    17976735   83  Linux
/dev/mapper/isw_diihdeefba_RAID0p4           48270       48641     2988090   82  Linux swap / Solaris







ubuntu@ubuntu:~$ mkfs -t ext3 /dev/mapper/isw_diiheefba_RAID0p3
mke2fs 1.40.8 (13-Mar-2008)
Could not stat /dev/mapper/isw_diiheefba_RAID0p3 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_diihdeefba_RAID0" already active
RAID set "isw_diihdeefba_RAID01" already active
RAID set "isw_diihdeefba_RAID02" already active
RAID set "isw_diihdeefba_RAID04" already active
ubuntu@ubuntu:~$ mkfs -t ext3 /dev/mapper/isw_diiheefba_RAID04
mke2fs 1.40.8 (13-Mar-2008)
Could not stat /dev/mapper/isw_diiheefba_RAID04 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
ubuntu@ubuntu:~$ 


I'm trying to setup a dual boot ubuntu on my system which has a fakeRAID configuration.  Somebody help me please!!  I can't get anything to work for me!! Arg!!

---

### Post by Xiong Chiamiov on 2008-09-27
Have you tried cfdisk (CLI) or gparted (GUI)?  They're much easier to work with than fdisk.

EDIT: Oh, and please don't [double-post]("http://ubuntuforums.org/showthread.php?t=931899").

---

### Post by WhyCantEveryOSBePerfect on 2008-09-28
I've tried gparted I think, is that the parition editor that comes with ubuntu?  If so, no dice.  I don't even know what the partition name is for my partition, if you look through the information I posted from the terminal it could be either
/dev/mapper/isw_diihdeefba_RAID0p3 or maybe /dev/mapper/isw_diihdeefba_RAID04, and there is no /dev/mapper/isw_diihdeefba_RAID03...  I'm starting to think I'm not going to be able to have ubuntu.

As for my double post/double thread:  sorry.  When I posted it and then logged on later I searched for all my threads and that one didn't show up...  so I made a new one.  Is there some way I could delete that one?  It's lacking in information anyway.

---

### Post by Xiong Chiamiov on 2008-09-28
Yep, gparted is what comes with Ubuntu.  Did it give you errors?

Normally running 
```

sudo fdisk -l

```
is the best way to list your drives/partitions.  I don't know about with RAID, though.

You can't delete threads, but you can edit your post there and provide a link here for anyone who comes across it.

---

### Post by WhyCantEveryOSBePerfect on 2008-09-28
Yes, it gave me errors.  It could not create the filesystem, and when that happened I tried to do it manually through the terminal.  The partitioning itself seemed to work fine in both gparted and fdisk though.

"sudo fdisk -l" does not work either.  If I run it before I run "sudo dmraid -ay" then it tells me I have 2 discs, the first one with two partitions and that the second one does not have a valid partition table, which is no help to me.

As for my other thread with the double post, should I just mark it solved so no one bothers with it?

---

### Post by Xiong Chiamiov on 2008-09-28
You might need to run a fsck on your drive to repair your filesystem.  You can't have the drive mounted at the time, so you'll have to boot off a cd...

I'd keep your other thread unsolved (since it is unsolved).  If someone knows enough about the subject to read the thread, they'll just follow your link here and hopefully help you out.

---

### Post by WhyCantEveryOSBePerfect on 2008-09-28
How can I repair it if I don't have a filesystem yet?  I'm trying to create a filesystem on newly partitioned space.  Sorry if I was unclear about that.  Also, I have been booting from the live cd, I do not have ubuntu installed yet, I'm trying to setup a dual-boot system with vista and raid0 (fakeraid)already setup.

---

### Post by Xiong Chiamiov on 2008-09-28
> **WhyCantEveryOSBePerfect said:**
> How can I repair it if I don't have a filesystem yet?  I'm trying to create a filesystem on newly partitioned space.  Sorry if I was unclear about that.  Also, I have been booting from the live cd, I do not have ubuntu installed yet, I'm trying to setup a dual-boot system with vista and raid0 (fakeraid)already setup.
Oh sorry, you did specify that.  I'm just jumping around threads and irc and forgot.  Apologies.

---

### Post by WhyCantEveryOSBePerfect on 2008-09-28
No problem man!  I am glad to have any replies, lol.  I've been working on getting ubuntu onto my computer for like 3 weeks now, and it's aggravating!  I contacted gateway to ask for help and basically got "we don't support linux"  I'm learning how to use ubuntu though, just from all the crap I've been trying.  

I don't know if it'll help at all, but here's my devices pertaining to raid and my disks from the windows device manager (as it appears there).

Disk Drives
-RAID0

IDE ATA/ATAPI controllers
-ATA Channel 0
-ATA Channel 1
-Intel(R) ICH8M  Ultra ATA Storage Controllers -2850
Storage Controllers
-Intel(R) 82801HEM SATA RAID Controller
-Microsoft iSCSI Initiator
-Silicon Image SiI 3531 SATA Controller

---

### Post by WhyCantEveryOSBePerfect on 2008-10-02
Bump

---

