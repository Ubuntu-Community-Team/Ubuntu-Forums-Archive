---
title: "Recover partition"
date: 2008-10-28
forum: Philippine Team
---

### Post by Recursion_1209 on 2008-10-28
Last night I was trying to install ArchLinux on my other pc and acidentally selected my data partition (ext3) to be used and change to reiserfs. 

I didn't push thru with the install because of some problem with missing package source. I only realize this problem this morning when I was trying to install Ubuntu 8.10.

Can I still recover this partition? How?

---

### Post by WWSmith36 on 2008-10-28
You might want to see if TestDisk can rebuild/recover the partition for you.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It can be found on many of the LiveCD´s
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

If you cannot recover the partition.  You could use a file recovery tool to extract as much data you can off the partition.

---

### Post by caljohnsmith on 2008-10-28
How about first posting:
```
sudo fdisk -lu
sudo blkid
```
And if your ext3 data partition is now marked as ReiserFS, you can use fdisk to change the partition type back to ext3. Just do:
```
sudo fdisk /dev/sda
```
Or replace sda with your drive, then press "t", then type the partition number (sda2 = "2" for example), then type "83" for the partition type, then "w" to write the change to disk. After that try:
```
sudo fsck -y /dev/sdX
```
And change sdX to your data partition. If that works you could then try and mount it:
```
sudo mount /dev/sdX /mnt
ls -l /mnt
```
Please post the output of all the above commands. :)

---

### Post by Recursion_1209 on 2008-10-29
Sorry, I wasn't able to capture the output after the commands on my first try. I still cannot see the data. The partition was already mounted by Ubuntu after restart. If I do it now here is what I got:

**sudo fdisk -lu:**

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd052d052

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    19535039     9767488+  83  Linux
/dev/sda2        19535040    27342629     3903795   82  Linux swap / Solaris
/dev/sda3        83891430   234436544    75272557+  83  Linux
/dev/sda4        27342630    83891429    28274400   83  Linux

sudo blkid
/dev/sda1: UUID="9281223b-c88a-41c4-b1b7-449a00b816cf" TYPE="jfs" 
/dev/sda2: TYPE="swap" UUID="f6325c06-7eec-4956-87ee-c6e81a202998" 
/dev/sda3: UUID="00297c68-b3f1-43ff-aee0-7cb7efb209b2" TYPE="reiserfs" 
/dev/sda4: UUID="e8423a8f-b2d3-42c5-9fa2-9ddece0505d1" TYPE="jfs" 

**sudo fdisk /dev/sda:**

The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): t
Partition number (1-4): 3
Hex code (type L to list codes): 83

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

**fsck -y /dev/sda:**
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
recursion@recursion-laptop1:/media/disk$ 

[B]sudo mount /dev/sdX /mnt
ls -l /mnt:[/B]
recursion@recursion-laptop1:/media/disk$ sudo mount /dev/sda3 /mnt
recursion@recursion-laptop1:/media/disk$ ls -l /mnt
total 0
recursion@recursion-laptop1:/media/disk$

---

### Post by caljohnsmith on 2008-10-29
My mistake, that fdisk procedure I gave won't change the file system back to ext3 since ext3 and ReiserFS are both considered file system type "83". Try doing the fsck on the partition to see what it reports; please post the output of:
```
sudo fsck /dev/sda3
```

---

### Post by Recursion_1209 on 2008-10-29
Here is the output:
fsck 1.41.3 (12-Oct-2008)
reiserfsck 3.6.19 (2003 [www.namesys.com](www.namesys.com))

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to [email]reiserfs-list@namesys.com[/email], **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  [www.namesys.com/support.html](www.namesys.com/support.html). **
*************************************************************

Will read-only check consistency of the filesystem on /dev/sda3
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
###########
reiserfsck --check started at Wed Oct 29 21:22:02 2008
###########
Replaying journal..
Reiserfs journal '/dev/sda3' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Comparing bitmaps..finished
Checking Semantic tree:
finished
No corruptions found
There are on the filesystem:
	Leaves 1
	Internal nodes 0
	Directories 2
	Other files 0
	Data block pointers 0 (0 of them are zero)
	Safe links 0
###########
reiserfsck finished at Wed Oct 29 21:22:09 2008
###########


Its still detects that it is reiserfs partition instead of a ext3 partition. I still cannot see any data.

---

### Post by caljohnsmith on 2008-10-29
There's probably some way to hack the partition back into being ext3 again without losing your data, but I don't know how off-hand. At this point, I would maybe use [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") to recover any important files you have in that partition. Or if you have another drive that has as much space as that partition, you could clone over the partition and have the freedom to try different methods of restoring it without worrying about permanently losing everything.

---

### Post by killer_d76 on 2008-10-29
is it not possible for you to try and run live cd like puppy linux? and access that particular partition and recover the files that you have?..

---

### Post by Recursion_1209 on 2008-10-30
@killer_d76 I can do that as well. How do I recover the files? What command/tool should I use?

Can I do this also using an Ubuntu Live CD?

---

### Post by tagabukid on 2008-10-31
I use system rescue cd. its a 220mb download only from [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) and runs from the cd and has testdisk preinstalled.

---

### Post by Recursion_1209 on 2008-10-31
Downloading System Rescue now. Hope it works...

---

### Post by killer_d76 on 2008-11-01
> **Recursion_1209 said:**
> @killer_d76 I can do that as well. How do I recover the files? What command/tool should I use?

Can I do this also using an Ubuntu Live CD?

yes you can.. no special command or tools to use bro, try running the Ubuntu Live CD and notice that you can access your HDD, just plug in an external HDD or USB Flash Drive or where ever you wish to save and copy all your important files! ;)

---

### Post by Recursion_1209 on 2008-11-03
I tried system rescue cd but it seems that it does not support recovery of Virtual Box Files. 

I am already thinking of giving up and just try to re-code  the VB source codes inside Virtual Box files that I want to recover.

---

### Post by Recursion_1209 on 2008-11-03
I tried system rescue cd but it seems that it does not support recovery of Virtual Box Files. 

I am already thinking of giving up and just try to re-code  the VB source codes inside Virtual Box files that I want to recover.

---

### Post by tagabukid on 2008-11-03
> **Recursion_1209 said:**
> I tried system rescue cd but it seems that it does not support recovery of Virtual Box Files. 

I am already thinking of giving up and just try to re-code  the VB source codes inside Virtual Box files that I want to recover.

sad to hear that. i hope you can find a better tool that would work for you.

---

