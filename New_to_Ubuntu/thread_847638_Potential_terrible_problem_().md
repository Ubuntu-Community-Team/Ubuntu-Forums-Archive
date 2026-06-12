---
title: "Potential terrible problem (?)"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by pensaer on 2008-07-02
Hey guys,
I'm trying to get 8.04 on my computer dual booted with windows xp, but i'm stuck in the early steps because when i run chkdsk in windows i get the following:

WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.

 - it then completes the scan, when i try to run chkdsk /f to fix whatever problem i may have, it displays:

Cannot lock current drive.
Chkdsk cannot run because the volume is in use by another process.  Would you like to schedule this volume to be checked the next time the system restarts?  (Y/N)


Any ideas?
I'm trying to repartition a raid 0 array, running an Abit IP35 pro mobo, intel core 2 duo, and two seagate barracuda 250 gig sata drives as SCSI.

Thanks in advance for your advice, I'm really excited to get on ubuntu and involved in the community.

---

### Post by tjwoosta on 2008-07-02
> Chkdsk cannot run because the volume is in use by another process. Would you like to schedule this volume to be checked the next time the system restarts? (Y/N)


I would suggest following what it says and just schedual the scan to run on reboot

(the reason it cant check the disk is because its currently mounted) (your using it)

---

### Post by pensaer on 2008-07-02
thanks for the quick response, i'm rebooting to scan now...

---

### Post by sayakb on 2008-07-02
Shouldn't this make chkdsk run on Windows boot? Doesn't it run there? Also, you may not run chkdsk on partitions on which you have Windows installed/pagefile or hiberfile created.

EDIT: w00t, you guys are fast..

---

### Post by pensaer on 2008-07-02
alright, i set chkdsk to scan on reboot and rebooted, everything went fine there.   i then rebooted again, booted up the live cd, and i get this error when attempting to start to resize the partition:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4b8b4b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo ntfsresize --info /dev/sda1
ntfsresize v2.0.0 (libntfs 10:0:0)
$MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
Failed to startup volume: Input/output error.
ERROR(5): Opening '/dev/sda1' as NTFS failed: Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.


i did reboot twice, btw...

---

### Post by jimv on 2008-07-02
Get a copy of Paragon Partition Manager.  One of the best I've used.

---

### Post by pensaer on 2008-07-02
and it gets worse... ](*,)

i gave up on the raid attempt and decided to reinstall windows on one HD and leave space for installing ubuntu on the other.  i ran the install from the windows disc, it prompted me to download some new updates (of course), and upon rebooting after installation of those updates the computer now goes into the blue screen of death and gives me an error message saying that i need to run chkdsk /f to search for viruses, etc.

so i can't get into windows, and i can't access my raid controller (won't recognize keyboard after hitting ctrl-i to bring up the screen)...

so i'm wondering how i can do a clean install on sda1 of ubuntu off the live cd, keeping in mind that i can't resize the ntfs partition with ntfsresize (see above posts).  i've noticed that when i try to add a disk label to one of the disks in gparted it gives me a warning that this will erase all data on the disk.  so can i just use gparted to do that to set up ubuntu on sda1?  and will the raid array still be active and messing with me once i do this?

thanks so much for your help guys, i never thought it would be this much of a problem right off the bat :)

---

### Post by pensaer on 2008-07-02
forgot to add this:

right now in gparted both disks read as unallocated and have no disklabels.

---

