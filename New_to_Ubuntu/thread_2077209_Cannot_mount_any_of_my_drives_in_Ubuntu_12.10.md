---
title: "Cannot mount any of my drives in Ubuntu 12.10"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by Pittip on 2012-10-28
Hi,
I recently upgraded my ubuntu from 12.04.1 to 12.10. Post upgrade, I am not able to mount any of my drives. It gives me the following error message everytime I try to open one of the drives:
"**Adding read ACL for uid 1000 to `/media/*username*' failed: Operation not supported**"
I tried googling it but all in vain.
Any help in this regard is highly appreciated.

---

### Post by Pittip on 2012-10-28
Found the solution on [http://askubuntu.com/](http://askubuntu.com/)
It definitely works!!!

Just run these two lines in the terminal as it is:
[B]sudo mkdir /media/$USER
sudo chown $USER.$USER /media/$USER[/B]

---

### Post by Bashing-om on 2012-10-28
should not the chown command be "$USER:$USER ...note with a colon not a period separator.

---

### Post by redmk2 on 2012-10-28
> **Bashing-om said:**
> should not the chown command be "$USER:$USER ...note with a colon not a period separator.

Both the period and colon separator will work in this instance.

---

### Post by NMeyne on 2012-11-24
I think a proper fix has just been released.

[https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1048059](https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1048059)

Workarounds did not work for me.  I was trying to re-use some ext2 filestore when I installed, using the 'anything else' option.  I didn't bother to reformat.  Seems that the earlier ext2 does not support the access control..  so I guess for upgraders, apply the latest fix which ignores the ACL, or re-install from scratch.  Which I will try now!

---

### Post by Agbeard on 2013-02-20
> **Pittip said:**
> Found the solution on [http://askubuntu.com/](http://askubuntu.com/)
It definitely works!!!

Just run these two lines in the terminal as it is:
[B]sudo mkdir /media/$USER
sudo chown $USER.$USER /media/$USER[/B]

I have this exact problem on a 12.04 HDD installation. No HDD partitions, no USB devices showing, let alone mountable.

I tried the fix on a live usb of 12.10, and it fixed the problem, but it's not fixing it on my 12.04 installation.

fdisk -l can see them all, but they're not visible in the sidebar or in the computer browser window.

Any other ideas?

---

### Post by Bashing-om on 2013-02-21
Agbeard; Hi Welcome to the forum.

In order for the partitions on your hard drive to be recognized they must be mounted. The mounting may be done either manually for discretionary mounting or via /etc/fstab for auto mounting.
Optical devices must have a disk inserted to gain recognition.

That said, how may we help you ?

[INDENT][INDENT]best regards

[/INDENT][/INDENT]

---

### Post by Agbeard on 2013-02-23
> **Bashing-om said:**
> Agbeard; Hi Welcome to the forum.

In order for the partitions on your hard drive to be recognized they must be mounted. The mounting may be done either manually for discretionary mounting or via /etc/fstab for auto mounting.
Optical devices must have a disk inserted to gain recognition.

That said, how may we help you ?

[INDENT][INDENT]best regards

[/INDENT][/INDENT]

Hi Bashing-om. Thanks for your response.

I have a Windows 7 dual boot machine with a recovery partition on sda1, Windows on sda2 (the boot partition), another ntfs partition at sda3, Ubuntu 12.04 on sda6.  I have inserted a flash drive which appears at sdb1.

No icons for these appear in the side bar, or on the desktop, or in the side bar of Nautilus for me to click on to mount, yet they are listed when I look in the terminal with sudo fdisk -l.

I've created the /media/me folder and done the chown on it as described earlier, rebooted, but still nothing -- no HDD partitions, and no flash drive.

I've made a persistent live Ubuntu 12.10 flash drive, and booting to that had the same problem, but after running the two sudo commands on the /media directory, I now have icons for the HDD partitions and the flash drive in the sidebar and in Nautilus, so I can just click on them to mount them.  I just can't get this to work on my 12.04 installation.

If I need to edit /etc/fstab manually, what entries do I need to put in there?

Sorry for the long post.... :grimace:

---

### Post by Bashing-om on 2013-02-23
Agbeard;

Well, let's look and see what we have to work with.
Is the package "ntfs-3g" installed (required for ubuntu to cope with ntfs)? 
terminal code:
```
 which ntfs-3g
```With the flash drive inserted post the output of the terminal code:
```
sudo fdisk -lu
mount
ls -l /media
ls -l /mnt

```and post the results of terminal code:
```
 cat /etc/fstab
```[INDENT][INDENT]the tale will be told

[/INDENT][/INDENT]

---

### Post by Agbeard on 2013-02-24
Here it all is:

```
chris@chris-N50Vc:~$ which ntfs-3g
/bin/ntfs-3g
```

```
chris@chris-N50Vc:~$ sudo fdisk -lu
[sudo] password for chris: 
omitting empty partition (5)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    24579449    12289693+  1c  Hidden W95 FAT32 (LBA)
Partition 1 does not start on a physical sector boundary.
/dev/sda2   *    24579450  1568825343   772122947    7  HPFS/NTFS/exFAT
Partition 2 does not start on a physical sector boundary.
/dev/sda3      1568825344  1953521663   192348160    f  W95 Ext'd (LBA)
/dev/sda5      1568827392  1709878028    70525318+   b  W95 FAT32
/dev/sda6      1709881344  1919172607   104645632   83  Linux
/dev/sda7      1919174656  1935945727     8385536   82  Linux swap / Solaris
/dev/sda8      1935947776  1953521663     8786944   82  Linux swap / Solaris

Disk /dev/sdb: 7860 MB, 7860125696 bytes
155 heads, 31 sectors/track, 3194 cylinders, total 15351808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2800    15351807     7674504    c  W95 FAT32 (LBA)
```

```
chris@chris-N50Vc:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
```

```
chris@chris-N50Vc:~$ ls -l /media
total 8
drwxr-xr-x 2 chris chris 4096 Feb 21 13:31 chris
drwxr-xr-x 2 chris chris 4096 Feb 21 08:04 usb

chris@chris-N50Vc:~$ ls -l /mnt
total 0
```

```
chris@chris-N50Vc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=8fc2877f-1aec-41ad-a9dd-78023ad5cac2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9d51e1ec-15e3-465c-bae3-ee9badbd17d0 none            swap    sw              0       0
```

Thanks again for looking at all this.

I'm sort of tempted to fix it by just upgrading to 12.10, but feel there's a good learning opportunity here.  :)options

---

### Post by Bashing-om on 2013-02-24
Agbeard;

I can not imagine how this came about:
mount shows root as partition sda6;
fstab shows root as partition sda8;
fdisk shows sda7 AND sda8 as swap partitions.
Don't have a clue, but, definitely need to get things straightened out.

Let's begin by looking at the uuids the system has assigned.
Post the output of terminal commands:
```
 ls -l /dev/disk/by-uuid/
 sudo blkid
```[INDENT]we will see what can be done
[/INDENT]

---

### Post by Agbeard on 2013-02-27
> **Bashing-om said:**
> Agbeard;

I can not imagine how this came about:
mount shows root as partition sda6;
fstab shows root as partition sda8;
fdisk shows sda7 AND sda8 as swap partitions.
Don't have a clue, but, definitely need to get things straightened out.

Let's begin by looking at the uuids the system has assigned.
Post the output of terminal commands:
```
 ls -l /dev/disk/by-uuid/
 sudo blkid
```[INDENT]we will see what can be done
[/INDENT]

Heheh...  :D

Yes, this HDD has a bit of history, as you so rightly perceive.

It was originally a Vista machine (a nice ASUS N50Vc laptop), and it has the usual laptop type setup of partitions.  I installed an older version of Ubuntu alongside Vista.

I use Paragon Hard Drive Manager to take full images, and (sometime after upgrading to Windows 7) I bought a new larger HDD, and used Paragon to image the new HDD with the whole dual boot system.  This went entirely without a hitch.

The doubling up of the swap partitions came about after I trashed an Ubuntu installation (probably 10.04) and reinstalled it with 11.04.  I used Paragon to wipe the partition first, and that left the old swap partition behind.  The new install, instead of using the old swap partition, just made itself a new one.

As I think back, I must have done this a couple of times, because there were three swap partitions, and I deleted what I assumed was an unused swap partition, only to find that Grub bootloader could no longer find its configuration files, and all I could get was Grub repair.  I worked out how to use this, and successfully got the machine booting again, and updated Grub.  I wasn't game to try that again, hence two swap partitions!

Anyway, sorry for the long story, but I thought it worth telling.  I guess you will glean much of the above from the following:

```
chris@chris-N50Vc:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Feb 28 13:08 229CBC849CBC53CF -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb 28 13:08 38216d10-2424-434a-9269-dcc261cf0ebd -> ../../sda7
lrwxrwxrwx 1 root root 10 Feb 28 13:08 3C98-AC5D -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 28 13:08 777801C9B91F0415 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb 28 13:08 8fc2877f-1aec-41ad-a9dd-78023ad5cac2 -> ../../sda6
lrwxrwxrwx 1 root root 10 Feb 28 13:08 9d51e1ec-15e3-465c-bae3-ee9badbd17d0 -> ../../sda8
```
```
chris@chris-N50Vc:~$ sudo blkid
[sudo] password for chris: 
/dev/sda1: LABEL="RECOVERY" UUID="3C98-AC5D" TYPE="vfat" 
/dev/sda2: LABEL="VistaOS" UUID="229CBC849CBC53CF" TYPE="ntfs" 
/dev/sda5: LABEL="DATA" UUID="777801C9B91F0415" TYPE="ntfs" 
/dev/sda6: UUID="8fc2877f-1aec-41ad-a9dd-78023ad5cac2" TYPE="ext4" 
/dev/sda7: UUID="38216d10-2424-434a-9269-dcc261cf0ebd" TYPE="swap" 
/dev/sda8: UUID="9d51e1ec-15e3-465c-bae3-ee9badbd17d0" TYPE="swap"
```

Thanks once again for taking the time and trouble to look at this issue for me.DATA

---

### Post by Bashing-om on 2013-02-28
Agbeard;

Good news is that the uuid"s - that long string of numbers - agree with what is in the configuration file "fstab"; requiring only minor edits to the descriptive fields to show the correct locations.
Then  add the appropriate entries for the ntfs partitions:
[https://help.ubuntu.com/community/NewDocs](https://help.ubuntu.com/community/NewDocs) -> "m" ->35. [Mount Ntfs On Boot]("https://help.ubuntu.com/community/MountNtfsOnBoot") -yields this tutorial on how to accomplish:
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot)
(assuming you desire to automount the ntfs partitions on boot, a manual ondemand method may better suit [?])
Delete one of the remaining swap partitions - to be determined by future use intent. 
Get this done then look at the usb device mounting.

Not so good news - It is late here and past my sleep time, I am tired and not think'n real clear.
My Daughter is undergoing major surgery and we will be with her - out of town - for an unknown amount of time. I will check back with you at the earliest opportunity.

So will continue this at a later time.[INDENT]look'n up - prospects are good

[/INDENT]

---

### Post by Agbeard on 2013-02-28
Thanks, I'll work with your advice up there and let you know how it goes.  Thanks very much for your help.

All the best with your daughter as well.  I wish you (and her) all the best for a successful procedure and a speedy recovery.  Not an easy time for you.

---

### Post by Bashing-om on 2013-02-28
Agbeard;

Ok I am back for a little time. You do the homework yet ? Got a comprehension of editing the fstab file to include your window's partitions?
In other words - How can I help at this time ?

Daughter went through surgery well, Doc says she is doing well and may be able to leave the hospital early maybe midweek, next week.

Appreciate your condolences.

---

### Post by Agbeard on 2013-03-02
Hi again, Bashing-om. Thanks for your help again here, and sorry about the delays in getting back to this -- I have a pretty hectic working life, teaching instrumental music in a couple of schools, and being involved in several ensembles as well.

I've had a read through, and I'm pretty sure I understand the basics of fstab, if not what the switches (I assume) after each entry mean.

What I'm wanting to achieve her is for the other partitions' icons to appear unmounted in the left pane of Nautilus so I can click on them to mount them, and for usb drives to appear in the left pane, but mounted.  I'm pretty sure they used to be that way in earlier installations, and I don't know when that all disappeared.

Also, getting rid of that extra swap partition and assigning its space to the main partition would be a bonus!

---

### Post by Bashing-om on 2013-03-02
Agbeard;
 I may be a bit out of my depth, I left Windows several years past and have never had ntfs partitions on any of my boxes since. All my partitions (linux formats all) all appear in nautilus; even those I do not mount . Will require me to do some research on nautilus-mounting processes to understand what is going on to get that ability.

usb devices normally do not have an icon in nautilus untill the drive is inserted. The funcionality you desire is achievable with a line added for the usb device in /etc/fstab.

Maybe we can do the same for the ntfs partitions (???) an interesting idea.

For now I can offer two option for the ntfs partitions.
a) Automount the partitions you want on startup in /etc/fstab;
b) Mount on demand through a mount point (directory in /mnt) and a command line entry to do the actual mount and MUST be (un)mounted when done prior to shut down of the system.

Extra swap partition, No biiggy to get rid of it. Look at the disk's partition layout, decide which one to eliminate, verify the correct UUID in /etc/fstab, decide what to do with that old partition;
a) Expand a partition into that space;
b) Use that space as a small "data" partition (shared or dedicated ??)

I work best one item at a time. What now do you want to tackle first ?[INDENT=2]

try'n to help

[/INDENT]

---

### Post by Agbeard on 2013-04-01
Hi Bashing-om.  Apologies for disappearing for a bit there -- end of school term got a bit out of hand!  :)

The first thing I'd like to clean up is the extra swap partition.  I deleted one of these once before (they're the legacy of multiple Linux installs on the partition) and lost grub's reference files.  Learnt a bit about grub-rescue with that one.

Anyway, looking back, the two offending partitions appear to be sda7 and sda8:

```
chris@chris-N50Vc:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Feb 28 13:08 38216d10-2424-434a-9269-dcc261cf0ebd -> ../../sda7
lrwxrwxrwx 1 root root 10 Feb 28 13:08 9d51e1ec-15e3-465c-bae3-ee9badbd17d0 -> ../../sda8

chris@chris-N50Vc:~$ sudo blkid
/dev/sda7: UUID="38216d10-2424-434a-9269-dcc261cf0ebd" TYPE="swap" 
/dev/sda8: UUID="9d51e1ec-15e3-465c-bae3-ee9badbd17d0" TYPE="swap"
```

My partition table reads as follows:
```
(parted) print
Model: ATA Hitachi HTS54101 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  12.6GB  12.6GB  primary   fat32           hidden, lba
 2      12.6GB  803GB   791GB   primary   ntfs            boot
 3      803GB   1000GB  197GB   extended                  lba
 5      803GB   875GB   72.2GB  logical   ntfs
 6      875GB   983GB   107GB   logical   ext4
 7      983GB   991GB   8587MB  logical   linux-swap(v1)
 8      991GB   1000GB  8998MB  logical   linux-swap(v1)
```

I'm thinking no. 7 was the last one created, and the one in use as swap for this installation, as I would have installed to the existing partition, and I assume the installer would have created a new swap partition in the partition the installation was pointing to.

I'm also thinking that last time I deleted a stray swap partition, I was working under the same assumption, and then had the grub troubles, so I'm thinking that grub's information is on the other swap partition.  I would've expected it to be on the main installation partition, however -- i.e., sda6.

Anyway, if that is coherent enough, I'd like to tidy up the partition mess first.  I use Paragon Partition Manager under Windows for this stuff, btw, but I'm open to using a nice graphical Ubuntu one.

Thanks again for your help.

---

### Post by Bashing-om on 2013-04-01
Agbeard;

It's like this, Windows' tools for windows problems, ubuntu tools for ubuntu situations. In this instance of messing with ubuntu partitions let us use ubuntu's most excellent partition editor :GParted". Available on the liveCD, with fairly decent documentation.
Now we want to identify our partitions in reference to their UUID's:
terminal codes:
```
sudo blkid
sudo fdisk -lu
```
and compare that output to what ubuntu is mounting in the file system table:
```
cat /etc/fstab
```
Then make a determination on which swap partition to keep and which to delete.[INDENT=2]
it's all a learning experience

[/INDENT]

---

### Post by Agbeard on 2013-04-01
> **Bashing-om said:**
> Agbeard;

 It's like this, Windows' tools for windows problems, ubuntu tools for ubuntu situations. In this instance of messing with ubuntu partitions let us use ubuntu's most excellent partition editor :GParted". Available on the liveCD, with fairly decent documentation.
:)  Interestingly, Paragon handles all partition types, including up to ext4.  It's a whole HDD utility.  I always use its bootable CD for partition work, and that's Linux based (of course!).  Ironically, when I used it to clone the old HDD to the current one, the only thing that complained about suddenly finding itself living on a new HDD was Windows;  Ubuntu wasn't in the least bit concerned.

Anyway,
```
chris@chris-N50Vc:~$ sudo blkid
[sudo] password for chris: 
/dev/sda1: LABEL="RECOVERY" UUID="3C98-AC5D" TYPE="vfat" 
/dev/sda2: LABEL="VistaOS" UUID="229CBC849CBC53CF" TYPE="ntfs" 
/dev/sda5: LABEL="DATA" UUID="777801C9B91F0415" TYPE="ntfs" 
/dev/sda6: UUID="8fc2877f-1aec-41ad-a9dd-78023ad5cac2" TYPE="ext4" 
/dev/sda7: UUID="38216d10-2424-434a-9269-dcc261cf0ebd" TYPE="swap" 
/dev/sda8: UUID="9d51e1ec-15e3-465c-bae3-ee9badbd17d0" TYPE="swap"
```
```
chris@chris-N50Vc:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    24579449    12289693+  1c  Hidden W95 FAT32 (LBA)
Partition 1 does not start on a physical sector boundary.
/dev/sda2   *    24579450  1568825343   772122947    7  HPFS/NTFS/exFAT
Partition 2 does not start on a physical sector boundary.
/dev/sda3      1568825344  1953521663   192348160    f  W95 Ext'd (LBA)
/dev/sda5      1568827392  1709878028    70525318+   b  W95 FAT32
/dev/sda6      1709881344  1919172607   104645632   83  Linux
/dev/sda7      1919174656  1935945727     8385536   82  Linux swap / Solaris
/dev/sda8      1935947776  1953521663     8786944   82  Linux swap / Solaris
```
```
chris@chris-N50Vc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=8fc2877f-1aec-41ad-a9dd-78023ad5cac2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9d51e1ec-15e3-465c-bae3-ee9badbd17d0 none            swap    sw              0       0
```
So, the fstab data has me confused.  Is it saying that sda6 (now the installation partition) was the swap partition during install, and sda8 (now the swap partition) was the install partition? :confused:

---

### Post by Bashing-om on 2013-04-01
jimafternoon;
fstab does tell a tale huh ? In answer to your question yes, at some point root (/) was installed on sda8 and is now sda6, vice the versa for swap. It workie great and last long time ! So, I suggest we leave it as is and look at what you want to do with partition sda7 ? Expand root into it or make a small data partition  (shared with windows ??) ?
In reference to loosing data [grub], any time data is moved about there is a chance of data loss, especially when the partition is moved to the left as the partition meta data is more prone to corruption. (disk header data) To the right is less likely but one should back up one's data just in case.
[INDENT=2]
what to do, oh what to do 
[/INDENT]

---

### Post by Agbeard on 2013-04-02
> **Bashing-om said:**
> 
what to do, oh what to do 


I'm thinking of deleting sda7 and allocating its space to sda6.  I've used grub-rescue once, I can use it again if it all goes pear-shaped.  What do you think?

---

### Post by Bashing-om on 2013-04-02
Agbeard;
Sounds good. Should be a walk in the park in comparison to other options. In GParted just delete the sda7 partition and expand the present sda6 into the unallocated space. I prefer to leave just a tad of space between my partitions as it can help in housecleaning and overhead issues.
As always there does exist the possibility of the files getting corrupted with the resize exercise. Back up any data you can not replace !

From BlikinCat's wiki - NewDocs - -> partitioning:
[https://help.ubuntu.com/community/P](https://help.ubuntu.com/community/P)

As an aid to your considerations.[INDENT=2]
best regards

[/INDENT]

---

### Post by Agbeard on 2013-04-02
Sounds like a good time to update my full drive image!  It's something I like to do before doing any partition stuff.  I'll set that up for overnight tonight, then start into the partition rearranging tomorrow.

---

### Post by Bashing-om on 2013-04-02
Agbeard; Excellent time indeed.
Once you have some experience with partitioning, you are done in just a matter of minutes// dependent only on how much data needs to be moved. There is an adage in the carpentry trade " measure twice and cut once"; here let's look three times, think about it a fourth and only move once ![INDENT=2]
good luck, I look forward to a successful (re-)partitioning

[/INDENT]

---

### Post by Agbeard on 2013-04-03
Ok, mixed success there.  :)  Ended up in grub rescue, but solved it successfully, and fixed grub with boot-repair.  I think I'll put off taking a new image for a bit, though -- see if other things can be fixed first.

 I've been a bit inclined to see if upgrading to 12.10 fixes the problem (running it live seems to work ok), but then (*checks calendar*) maybe I should wait until 13.04 comes out.  On the other hand, I'm fairly keen to use this as a bit of advanced Linux learning.

---

### Post by Bashing-om on 2013-04-03
Agbeard; Shucks, 

What I do not know fills a much larger book than one filled with what I do know. All I can think of that happened is Windows got unhappy moving the boot loader(??) about ...


Gained experience: mine, with good backups and a liveCD, one can fix/resolve any predicament. I have broke my system many times attempting to learn it -> learned the value of backups and procedures to restore my operating system. One of the forum members adage "if it ain't broke you ain't tweeked it enough" ! // What I am saying is that with gained experience breaking your system is not a great big deal. ubuntu, it's fixable .

Nother thought ... dual boot 'buntu on different hard drives, both bootable thus there exist a means for whatever. I often mount another operating system from the one I am in. Sometime this month I intend to remove 10.04 version -been a good distribution for long long time, bye bye- and install 13.04, keeping up with what changes. I will keep 12.04 as my primary system.

on topic: What other problems are you having ?... How can I help ?
[INDENT=3]
it's all a learning experience

[/INDENT]

---

