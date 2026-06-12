---
title: "Dual boot and partitions?"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by ABSMystery on 2013-07-07
Heads up: I've never had to partition anything before, so I'm new on the concept.  Also this isn't really a big deal, just a little organization thing that I want to work out before I start doing anything big with the OS.

I installed Ubuntu 13.04, and I'm just looking through all the features.  Once thing I noticed is the fact that I can access all of my Windows files from Ubuntu, even though I set up a separate partition in Windows beforehand.  This is great, since I thought I would have to redownload a bunch of things and use extra space, but now I'm wondering whether or not the partition is even necessary?  Going back onto Windows 7, it seems Ubuntu is occupying the partition that was previously labeled "Empty partition" (or something like that) with two of its own partitions, but it obviously isn't limited to those partitions alone.  Should I keep the partitions the way they are, or should I opt for a single partition (aside from the backup partitions, etc)?  If so, how do I go about doing that without screwing everything up?

---

### Post by sandyd on 2013-07-07
> **ABSMystery said:**
> Heads up: I've never had to partition anything before, so I'm new on the concept.  Also this isn't really a big deal, just a little organization thing that I want to work out before I start doing anything big with the OS.

I installed Ubuntu 13.04, and I'm just looking through all the features.  Once thing I noticed is the fact that I can access all of my Windows files from Ubuntu, even though I set up a separate partition in Windows beforehand.  This is great, since I thought I would have to redownload a bunch of things and use extra space, but now I'm wondering whether or not the partition is even necessary?  Going back onto Windows 7, it seems Ubuntu is occupying the partition that was previously labeled "Empty partition" (or something like that) with two of its own partitions, but it obviously isn't limited to those partitions alone.  Should I keep the partitions the way they are, or should I opt for a single partition (aside from the backup partitions, etc)?  If so, how do I go about doing that without screwing everything up?

can you post a copy of
```

sudo fdisk -l
mount -l
```
While you are accessing the windows disk from linux?

It will give us a better view of your current disk structure.

---

### Post by ABSMystery on 2013-07-07
> **sandyd said:**
> can you post a copy of
```

sudo fdisk -l
mount -l
```
While you are accessing the windows disk from linux?

It will give us a better view of your current disk structure.

fdisk:

> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xea89b52b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    29044735    14481408    7  HPFS/NTFS/exFAT
/dev/sda3        29044736  1134321663   552638464    7  HPFS/NTFS/exFAT
/dev/sda4      1134323710  1953523711   409600001    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1134323712  1936949247   401312768   83  Linux
/dev/sda6      1936951296  1953523711     8286208   82  Linux swap / Solaris

mount:

> /dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/austin/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=austin)
/dev/sda3 on /media/austin/OS type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096) [OS]

EDIT: The OS launcher to the file system starts in the same place as Window's C:\ by the way, as if they're sharing the original partition.

---

### Post by Impavidus on 2013-07-07
/dev/sda5 and 6 are your Linux partitions. sda5 is for storing all files, sda6 ia a swap partition. /dev/sda2 and 3 are your Windows partitions. Ubuntu can read and write to your Windows partitions, although with some limitations, but Windows does not natively understand the Linux partitions. The limitations are that Ubuntu cannot fix Windows file systems when they are damaged, some people have reported problem when using Ubuntu to write to the Windows C partition (but other partitions, D or whatever they are called, are save) and Ubuntu cannot be installed in a Windows partition because the ntfs file system doesn't support Unix permissions, which are needed by the OS. So you definitely need separate partitions for the two.

As far as I can see the partitions as present on your hard drive are OK. Maybe not perfect in terms of flexibility, but this will work fine and there is no need to change it before you decide to install from scratch at a later date.

You can use the file manager to mount and browse your Windows partitions. They won't show up at the base of the file system, which is the root directory or /. It contains a small and relatively fixed set of directories:```
$ ls /
bin    etc             lib         opt   sbin     tmp      vmlinuz.old
boot   home            lost+found  proc  selinux  usr
cdrom  initrd.img      media       root  srv      var
dev    initrd.img.old  mnt         run   sys      vmlinuz

```
When mounted, your windows file system will be present at /media/something/.

---

### Post by ABSMystery on 2013-07-07
> As far as I can see the partitions as present on your hard drive are OK. Maybe not perfect in terms of flexibility, but this will work fine and there is no need to change it before you decide to install from scratch at a later date.

What would be more flexible?  I gave the Ubuntu partition around 400 gb, so it can definitely handle anything I install on it.  I usually plateau at around 200 GB usage for my Hard Drives, and I have an external drive on top of that.

Otherwise, this explains everything.

---

### Post by su:bhatta on 2013-07-07
ok.. herez a suggestion... this is how i partition disks:

1) Give Windows7 around 50~100GB(NTFS Format)
2) Give Ubuntu  50~100GB( EXT4 Format)
3) SWAP Partiton, (generally i keep 4~5GB)
4) Keep the rest of HDD as storage space for all Data
(Make this a Logical partition n format it NTFS, since both Windows7 & Ubuntu can read NTFS, u can access this drive for data from both the OS's)

One thing i do, i never touch my Windows8 partition from my Ubuntu...( never mount it, or use it to store anything)

Then I maybe totally wrong with my idea or understanding but this is how i've set up all my friends & my machines...

any problems with that or recommendations, i would love to know...

---

### Post by Impavidus on 2013-07-07
As for flexibility...
Many people recomment having separate partitions for the system (/) and user files (/home), allowing for easier reinstalling in case anything goes wrong (never happened to me) and some extra safety when your hard drive dies (never happened to me either; guess I must be lucky). You can also leave some free space inbetween the partitions, so you can add it later to either of them without first having to shrink the other one (that's what I did).

It isn't really that important. I think you can leave everything as it is now.

---

### Post by farrinux on 2013-07-08
> **Impavidus said:**
> As for flexibility...
Many people recomment having separate partitions for the system (/) and user files (/home), allowing for easier reinstalling in case anything goes wrong (never happened to me) and some extra safety when your hard drive dies (never happened to me either; guess I must be lucky). You can also leave some free space inbetween the partitions, so you can add it later to either of them without first having to shrink the other one (that's what I did).

It isn't really that important. I think you can leave everything as it is now.

I actually do above because it does make reinstallation - upgrade much easier.  For a truly bullet proof dual boot.  Put Ubuntu and grub on their own hard drive.  Reason the first time you wanker Ubuntu or you corrupt grub you will not be able to access windows until you repair it's master boot file. The same is true if you wanker the windows intsall.  Goodbye Ubuntu!  Using two hard drives  you will make the one with Ubuntu and grub first boot priority in BIOS.  If you screw up and trash grub and can't access windows. All you have to do is change your boot priority in BIOS until such time as you fix ubuntu and hello windows. The same is true if you trash windows, however since you are booting off the ubuntu drive it will not even know it  Believe me it is well worth the money to put ubuntu and grub on their own hard drive.  Especially when you manage to trash grub or windows when its on the same drive as windows. You won't get into windows. 

P.S. we all know how easy windows gets trashed. (Virus, bad install etc.)

---

