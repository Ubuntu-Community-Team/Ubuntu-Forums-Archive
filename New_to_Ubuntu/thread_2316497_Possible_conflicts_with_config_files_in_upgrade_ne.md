---
title: "Possible conflicts with config files in upgrade new install?"
date: 2016-03-08
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2016-03-08
Using BackInTime, last night I backed up my /home in preparation of an upgrade from 12.04 fall-back to 14.04 Ubunutu Mate. Currently / and /home are on one of three 37 GiB partitions of an SSD, but in the new install, /home will be placed on the HDD in this computer. First question is, can I just copy/restore the backup to the new /home on the HDD after the install?

A second question is whether there are config files contained in (my current) /home that would have been backed up last night and will be written to the new /home (in which case might there be conflicts with the config files placed in the new /home partition in the new install?). 

As you can tell, I don't know much about config files, and there are 26 folders in the current /home which start with "."  Do all of these contain config files?

---

### Post by ajgreeny on 2016-03-08
Most if not all of them contain configuration for your various applications, and many of them are named as you might expect, eg the configuration for thunderbird is all contained in ~/.thunderbird folder.  Many are in subfolders of the ~/.config folder as well.

It is always possible to get some conflicts when moving from one Ubuntu version to another, but in the several years that I have been updating with a separate /home folder, never removing any of those old configuration folders first, I have not seen any problems that can not be overcome after the event simply by renaming the old folder as a backup.

Renaming the old folder gives you the opportunity of restoring some of the subfolders or files from the old version if you need to, so is a better choice than deletion of the old version.  You should, however, always have backups anyway when reinstalling or version upgrading so deletion of the old version may be an option if your backups are all in  order.

---

### Post by SeijiSensei on 2016-03-08
You can use rsync to transfer the directories in /home to the new drive.  If you plan to mount the new drive as /home, transfer just the directories themselves and not the /home prefix like this:
```

sudo mount /dev/sdb1 /mnt
cd /home
sudo rsync -av . /mnt
cd /
sudo umount /mnt
sudo mv home home.old
sudo mkdir home
sudo mount /dev/sdb1 /home

```
That assumes the new hard drive appears as /dev/sdb and you want to move /home to the first (or only) partition on the drive.  It should be formatted with ext4 before you begin the transfer
```
sudo mkfs -t ext4 /dev/sdb1
```
The rsync command I gave will print out a list of all the files it copies. You can turn that off by using just "-a", or you can leave it in verbose mode and save the list of transferred files to a file like this:
```
sudo rsync -av . /mnt > /root/filelist
```
In the line above this command, I use "cd /home" to put you at the top of the homes directory.  The period represents all files and directories below your current location.  That way when you mount the new drive as /home, the usernames will be in the same relative position in the filesystem.  I included ajgreeny's suggestion that you preserve the original /home for a while.  You'll see I renamed it /home.old, then made a new /home mount point for the new device.

---

### Post by Odyssey1942 on 2016-03-09
S.S. Thanks for the step by step. To ensure that I understand each step, I have written above each line of code what I think it is doing, plus in a case or two have added additional commentary after the code line. In preparation for my next question, could I ask you to read through this and note my misunderstandings (and adding a short explanation of my error)? I am documenting everything that I have been doing so far and want to it be not only informative to me for next time, but correct. Writing all this down will help me learn it. Your help much appreciated.

Before beginning be sure to:
-determine which partition is to be the place for /home
-that the partition is formatted EXT4 . If not already use:
```
sudo mkfs -t ext4 /dev/sdb1
``` ("sdb1" may differ depending on the computer)

Creates mount point
```
sudo mount /dev/sdb1 /mnt
```
(the effect of this is that /mnt now refers everything to sbd1)

Change to (top of) home directory in prep for transferring all user home directories to newly created mount point
```
cd /home
```
(At this point, everything under top /home is still on sda)

Copies contents of /home to mount point, i.e. mnt (DON'T COPY TOP /home, ONLY CONTENTS, I.E., USER /HOMES). The "v" (verbose) in the code creates a list of files copied. The "> /root/filelist" part will save the names of the transferred files to "filelist" in /root
```
sudo rsync -av . /mnt > /root/filelist
```

change to root directory
```
cd /
```

Unmount the new mount point
```
sudo umount /mnt
```
(S.S. I don't understand why /mnt is unmounted?)

Renames top home as home.old, preserving the contents of the old /home
```
sudo mv home home.old
```

Makes new (top) home directory under root directory
```
sudo mkdir home
```

Effect of below is that anything directed to /home goes to sbd1
```
sudo mount /dev/sdb1 /home
```
(Do I understand that somehow everything previously transferred to sdb1 will now be underneath /home? If so, can't get my head around how this happens. I must tell you that I find the whole mount thing mysterious). Is it that /home is still on sda and any reference to it goes to sdb1 just as if all user directories were still on sda?

Edit: Forgot to ask if any additional steps needed to cause the mount point to be restored each time the computer is booted up?

---

### Post by SeijiSensei on 2016-03-09
> **Odyssey1942 said:**
> 
```
sudo mkfs -t ext4 /dev/sdb1
``` ("sdb1" may differ depending on the computer)

Yes, it will depend on how many devices are in the machine, and how they are enumerated by the BIOS.  If you have two drives, usually they will be /dev/sda and /dev/sdb.  If you don't know how your new drive is referenced, run the command
```
sudo blkid
```
and you'll get a complete census of the available filesystems like this:
```
/dev/sda1: LABEL="System Reserved" UUID="B46E78156E77CF1C" TYPE="ntfs" 
/dev/sda2: LABEL="Recovery" UUID="E414794C147922AA" TYPE="ntfs" 
/dev/sda3: LABEL="WIN7" UUID="1E1E81AF1E81808F" TYPE="ntfs" 
/dev/sda5: UUID="023e302e-6396-490a-aaab-f10845a312b4" TYPE="ext4" 
/dev/sda6: UUID="bba56ea0-3677-4846-957d-5c57a1927805" TYPE="swap" 
/dev/sda7: UUID="51e6ed63-c130-4961-b2f1-4eadc78bdca4" TYPE="ext4" 
/dev/sdb1: UUID="c1819109-dc17-4e82-95ad-04eb16a9a245" TYPE="ext4" 
/dev/sdb2: LABEL="BigNTFS" UUID="D054464154462A94" TYPE="ntfs" 

```
This shows I have two drives, /dev/sda and /dev/sdb.  The first has both NTFS filesystems and Linux filesystems.  That's because this is a "dual-boot" machine.

The second drive /dev/sdb, has two partitions, one formatted as ext4 and one formatted with NTFS and named "BigNTFS".

> (the effect of this is that /mnt now refers everything to sbd1
Yes, though it's sdb1.  The "sd" means a SCSI or SATA drive, "b" means it's the second drive, and "1" means the first partition on /dev/sdb.  (These days, /dev/sdX can refer to older IDE drives as well; they're not very common nowadays.)

> Unmount the new mount point
```
sudo umount /mnt
```
(S.S. I don't understand why /mnt is unmounted?)


Because we're going to remount it as /home.  In principle it's possible for the same filesystem to be mounted at different locations, but it's better to have each filesystem mounted in only one.

> (Do I understand that somehow everything previously transferred to sdb1 will now be underneath /home? If so, can't get my head around how this happens. I must tell you that I find the whole mount thing mysterious). Is it that /home is still on sda and any reference to it goes to sdb1 just as if all user directories were still on sda?

If you're coming from Windows where drives and partitions are referenced as drive letters, this can be confusing the first time around.  In Linux, and other Unix-flavored systems, there is one coherent directory structure rooted at /.  A directory like /home can either refer to files below the root directory on the same device, or you can "mount" a filesystem at that location in the filesystem instead.  Often these locations are called "mount points," though they are just empty directories to which a filesystem is attached.  

> Edit: Forgot to ask if any additional steps needed to cause the mount point to be restored each time the computer is booted up?

Yes, you need to edit the file /etc/fstab (as root with sudo) and create an entry for /home like this:

```
/dev/sdb1     /home     ext4     defaults     0 0
```

That tells Linux to mount /dev/sdb1 at /home during boot.  On a system with multiple drives and partitions, it's often preferable to use "UUIDs" rather than /dev/sdX references, since the former will remain unchanged even if you add other devices, like a USB thumb drive, to the system.  In my case the entry in /etc/fstab reads:
```
UUID=51e6ed63-c130-4961-b2f1-4eadc78bdca4 /home      ext4    defaults     0  0
```
You'll notice that the UUID for this device is the same as the one for /dev/sda7 above.  That's the partition that contains the home directories on my machine.

Don't worry about the two numbers at the end of the entry.  They are an artifact of early Unix systems.  Just use two zeroes, and you'll be fine.

---

### Post by Odyssey1942 on 2016-03-09
Thanks for such a clear and complete explanation. Yes I did know about sdb. The sbd was a typo. Not a great typist either.

The last question for this thread is if my new install puts / on sda and home on sdb, will I need to do the above, or will it all be done as part of the install, and mount automatically at each boot up?

---

### Post by SeijiSensei on 2016-03-09
If you're installing from scratch, you can set up everything if you pick the "something else" choice (I think that's what it's called) when you get to the partitioning stage.  Then you will see all the partitions on all the devices and can assign them to mount points.

---

