---
title: "Delete Items on Mounted SATA does not free up space, fstab settings?"
date: 2022-04-20
forum: New to Ubuntu
---

### Post by todolinuxvidz1 on 2022-04-20
Hello all,
I have a few internal SATA drives mounted in Ubuntu 20.04.4 LTS.
When I attempted to delete items on these drives I am given the message "cant be put in trash do you want to delete immediately" and "Unable to find or create trash directory for"

If I select Delete, the item goes away but the free space available on the drive remains the same.

I have done some digging around the web and a lot of the solutions I seem to find indicate that I likely do not have my fstab configured properly.
Here is what my fstab looks like
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=19cc6a19-6d93-4c25-8b28-649f28d86704 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=5ED2-7C80  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
UUID=809E09029E08F288 /media/soloman/Core     auto nosuid,nofail,x-gvfs-show 0 0

UUID=4C50E4AA50E49C48 /media/soloman/Box     auto nosuid,nofail,x-gvfs-show 0 0


```

I was hoping to get some clarity on what I needed to add to fstab before I started fiddling with this, since Ive seen a few different suggestions on how to configure it.
The intention would be that these are permanently mounted drives.  Video editing etc, a lot of large files being created and deleted.

---

### Post by TheFu on 2022-04-20
If there isn't a trash directory on the file system, then it just takes a few minutes for the changes to be written. Check in 2 min. See if the space is freed.

When troubleshooting issues like this, test without the GUI.  That would determine if it is a file system or shell program issue -----OR----- more likely a GUI program problem.

The ftab above has some things that I'd never use, but if the mounts are there, then in is working.
I'm guessing 2 of the /media storage mounts are NTFS. I'd never do that without specifying ntfs as the type and these options:
```
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002
```

If the storage absolutely doesn't need to be NTFS, use a native Linux file system.  If the storage will be accessed over a network by Windows, not directly plugged in, then you don't need/want NTFS. Use ext4 unless you have a specific need to use some other native file system like ZFS, XFS, f2fs.  And if you to switch to any of those, you'll likely want to change the last '0' on the line to be a '2'.

The **fstab** manpage explains the 6 fields. **man fstab** will show it. Or use **xman**.

If the storage is external, say USB connected, then I'd use **autofs**, not the fstab.

But only you can decide the appropriate options and file system(s) to be be used.

---

### Post by ActionParsnip on 2022-04-21
Are you dual booting the system?

---

### Post by todolinuxvidz1 on 2022-04-26
> **TheFu said:**
> If there isn't a trash directory on the file system, then it just takes a few minutes for the changes to be written. Check in 2 min. See if the space is freed.

```
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002
```

If the storage absolutely doesn't need to be NTFS, use a native Linux file system.  If the storage will be accessed over a network by Windows, not directly plugged in, then you don't need/want NTFS. Use ext4 unless you have a specific need to use some other native file system like ZFS, XFS, f2fs.  And if you to switch to any of those, you'll likely want to change the last '0' on the line to be a '2'.

The **fstab** manpage explains the 6 fields. **man fstab** will show it. Or use **xman**.

If the storage is external, say USB connected, then I'd use **autofs**, not the fstab.

But only you can decide the appropriate options and file system(s) to be be used.

These drives were originally in a Window's system and one is a 16tb that is 85%-90% full so Ill need to purchase a backup to move the files before reformatting the drives.
Additionally I would like to share these drives with the other Windows machines throughout the house.

I tested out modifying the fstab for one of my drives as you described but that appear to have unmounted the drive. [EDIT:  I added nfts, in front of it and that appears to have remounted it like so > /media/soloman/Core   ntfs,nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002
Items are now deleted but do not go into the recycle bin, would there be an additional setting for that?

---

### Post by todolinuxvidz1 on 2022-04-26
> **ActionParsnip said:**
> Are you dual booting the system?

Yes but rarely.

---

### Post by TheFu on 2022-04-26
> **todolinuxvidz1 said:**
>  

I tested out modifying the fstab for one of my drives as you described but that appear to have unmounted the drive. [EDIT:  I added nfts, in front of it and that appears to have remounted it like so 
Items are now deleted but do not go into the recycle bin, would there be an additional setting for that?

The posted information doesn't show the complete fstab line that isn't working.  No way can I help without that.  But 
a) details matter.  "nfts" isn't a valid file system. It must actually be spelled correctly.
b) there must be 6 fields on each line in the fstab. If you don't have 6 fields, in the correct order, it doesn't work.  There's no "close enough" option. It is either correct or not. It either works or it doesn't.

You aren't any different than anyone else with the fstab. I remember struggling back in the olden days before cell phones.  Plus, NTFS drivers for Linux at the time were just as likely to destroy the files as work.

BTW, saw this today about the NTFS driver being unsupported: [https://www.phoronix.com/scan.php?page=news_item&px=NTFS3-Linux-Driver-2022-Sad](https://www.phoronix.com/scan.php?page=news_item&px=NTFS3-Linux-Driver-2022-Sad)   I should also say that I had to reformat an NTFS partition that is only used by Linux and a video recorder (it only supports USB NTFS/FAT32) due to corruption yesterday. Lost a day of recordings due to that corruption.

---

### Post by todolinuxvidz1 on 2022-04-26
> **TheFu said:**
> If there isn't a trash directory on the file system, then it just takes a few minutes for the changes to be written. Check in 2 min. See if the space is freed.

When troubleshooting issues like this, test without the GUI.  That would determine if it is a file system or shell program issue -----OR----- more likely a GUI program problem.

The ftab above has some things that I'd never use, but if the mounts are there, then in is working.
I'm guessing 2 of the /media storage mounts are NTFS. I'd never do that without specifying ntfs as the type and these options:
```
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002
```

If the storage absolutely doesn't need to be NTFS, use a native Linux file system.  If the storage will be accessed over a network by Windows, not directly plugged in, then you don't need/want NTFS. Use ext4 unless you have a specific need to use some other native file system like ZFS, XFS, f2fs.  And if you to switch to any of those, you'll likely want to change the last '0' on the line to be a '2'.

The **fstab** manpage explains the 6 fields. **man fstab** will show it. Or use **xman**.

If the storage is external, say USB connected, then I'd use **autofs**, not the fstab.

But only you can decide the appropriate options and file system(s) to be be used.

> **ActionParsnip said:**
> Are you dual booting the system?

> **TheFu said:**
> The posted information doesn't show the complete fstab line that isn't working.  No way can I help without that.  But 
a) details matter.  "nfts" isn't a valid file system. It must actually be spelled correctly.
b) there must be 6 fields on each line in the fstab. If you don't have 6 fields, in the correct order, it doesn't work.  There's no "close enough" option. It is either correct or not. It either works or it doesn't.

You aren't any different than anyone else with the fstab. I remember struggling back in the olden days before cell phones.  Plus, NTFS drivers for Linux at the time were just as likely to destroy the files as work.

BTW, saw this today about the NTFS driver being unsupported: [https://www.phoronix.com/scan.php?page=news_item&px=NTFS3-Linux-Driver-2022-Sad](https://www.phoronix.com/scan.php?page=news_item&px=NTFS3-Linux-Driver-2022-Sad)   I should also say that I had to reformat an NTFS partition that is only used by Linux and a video recorder (it only supports USB NTFS/FAT32) due to corruption yesterday. Lost a day of recordings due to that corruption.

Ill take a look at that link you share here is my full fstab sorry tried to take a shortcut to just show what was added.   
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=19cc6a19-6d93-4c25-8b28-649f28d86704 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=5ED2-7C80  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
UUID=809E09029E08F288 /media/soloman/Core   ntfs,nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002

UUID=4C50E4AA50E49C48 /media/soloman/Box     auto nosuid,nofail,x-gvfs-show 0 0

```

So both the drive called Box and Core are mounted but they seem to essentially have the same level of access, where files are deleted and go no where (I was hoping I could at least have them go to the recycle bin)
(I will save the whole network access issue for another thread)

---

### Post by TheFu on 2022-04-26
```
UUID=809E09029E08F288 /media/soloman/Core   ntfs,nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002
```
isn't valid. It only has 3 fields. There must be 6, in the correct order, all on a single line.

```
UUID=809E09029E08F288 /media/soloman/Core   ntfs       nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002    0   0
```
is probably what you want.

Details matter.  The manpage for fstab explains each field. It is a simple read. Worth the time.

As for a trash bin, I don't know. Don't use them myself.  I know that ext4 supports trash bins on the different file system mounts. Don't know about NTFS, since it isn't a native file system to Linux.

---

### Post by ActionParsnip on 2022-04-27
If it is NTFS, you may want to boot to Windows and run a full chkdsk on the data to make sure it is complete and consistent. NTFS is a proprietary file system and only Microsoft knows how it truly works.

---

### Post by todolinuxvidz1 on 2022-04-27
> **TheFu said:**
> ```
UUID=809E09029E08F288 /media/soloman/Core   ntfs,nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002
```
isn't valid. It only has 3 fields. There must be 6, in the correct order, all on a single line.

```
UUID=809E09029E08F288 /media/soloman/Core   ntfs       nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002    0   0
```
is probably what you want.

Details matter.  The manpage for fstab explains each field. It is a simple read. Worth the time.

As for a trash bin, I don't know. Don't use them myself.  I know that ext4 supports trash bins on the different file system mounts. Don't know about NTFS, since it isn't a native file system to Linux.

Your suggestion for fstab works great, thank you very much.   I will sideline the recycle bin issue for now.   I suspect what I will need to do is purchase an additional 20tbs of storage, format it in ext4, then back up the NTFS data on the ext4 drives, then figure out what Ill do with these NTFS drives after the fact.


> **ActionParsnip said:**
> If it is NTFS, you may want to boot to Windows and run a full chkdsk on the data to make sure it is complete and consistent. NTFS is a proprietary file system and only Microsoft knows how it truly works.
Thanks for the response the storage not freeing up after deletion portion of this problem has been resolved.

---

### Post by TheFu on 2022-04-27
You know that changing from NTFS to a native Linux file system can be tested using a small flash drive for a day, right?  Check that it works the way you want before blowing $500.  

If it works the way you need, then  ....
If you don't have use for the 2 NTFS drives, you can just buy 1 sized to replace the larger, format it with a native linux file system, then move the files from 1 drive onto it, now you have 2 spare drives. Format the now empty NTFS to a drive native linux file system, then move the files from the other NTFS drive.

BTW, if you can't backup the data currently, that's a pretty big problem.  All HDDs fail.  About 1-2% fail pretty early. They all fail, eventually.  Hopefully, that's after 15 yrs of use, but statistics and HDD manufacturer warranties suggest they fail much faster for drives with less than 5 yr warranties.  For drives with 5 yr warranties, I've seen NONE - ZERO - fail in use at home, 24/7/365 for over 10 yrs.  None.  For drives with 1 and 3 yr warranties, most fail before 5 yrs. Seagates HDDs since 2007 have all failed within 1-13 months of the warranty end.  Oddly, I have some older Seagate drives that had 5 yr warranties from around 2006 which are still working perfect.  They are just a hassle due to small, for today, storage capacities.

ext4 is just one option. There are probably 20 native Linux file systems that can be used. If you don't have a specific need for a specific file system, **ext4** is a good, general purpose, choice. It is what I use, though I've been tempted to use zfs for data-only disks multiple times.  For flash storage only used by Linux, I use **f2fs**.  I see little reason to use xfs or btrfs, though for specific purposes those can be fantastic choices.  xfs is a tiny bit faster than ext4, but it lacks some capabilities I've needed.  btrfs has catastrophic failure modes if more than 1 disk is used and virtual machines don't like the CoW file system, so for a laptop with a single storage device, never using any virtualization, it should be fine.  I've been tempted to install btrfs on a slow laptop just to see and learn.

I want to confirm that the OS native to a file system should be used to maintain, manage and validate that file system.  NTFS, FAT32, exFAT all need Windows for file system validation.

---

### Post by todolinuxvidz1 on 2022-04-27
Is there something with the way that these drives are mounted that would prevent Network sharing?
Reason I ask is I am able to share folders fine from my ext4 drive that the OS is on and access them with a Windows computer.
But these newly mounted drives the network drives dont seem to open, they are detectable but will not open.

---

### Post by todolinuxvidz1 on 2022-04-27
> **TheFu said:**
> You know that changing from NTFS to a native Linux file system can be tested using a small flash drive for a day, right?  Check that it works the way you want before blowing $500.  

If it works the way you need, then  ....
If you don't have use for the 2 NTFS drives, you can just buy 1 sized to replace the larger, format it with a native linux file system, then move the files from 1 drive onto it, now you have 2 spare drives. Format the now empty NTFS to a drive native linux file system, then move the files from the other NTFS drive.

BTW, if you can't backup the data currently, that's a pretty big problem. 


Oh I understand I need to back this up.   One of these drives was a 16 terabyte drive that I filled up in a year digitizing old video footage and transferring things from old external drrives (the 16 tb drive is about a year old).  So things have been ballooning data wise very quickly.   I think ultimately Ill have to migrate to some other type of solution.  Was looking at maybe purchasing 72 terabytes of additional storage for both backing up existing and being able to store additional footage right now Im basically maxed out.

---

### Post by TheFu on 2022-04-27
> **todolinuxvidz1 said:**
> Is there something with the way that these drives are mounted that would prevent Network sharing?
Reason I ask is I am able to share folders fine from my ext4 drive that the OS is on and access them with a Windows computer.
But these newly mounted drives the network drives dont seem to open, they are detectable but will not open.

Best to create a new thread for that question.  It is too different from fstab issues.  In the other thread, you'll want to be very specific on the protocol used. I generally help with NFS, but have backed off any samba/cifs help, since it isn't my expertise.  But NFS isn't so good from Windows.

---

### Post by TheFu on 2022-04-27
> **todolinuxvidz1 said:**
> Oh I understand I need to back this up.   One of these drives was a 16 terabyte drive that I filled up in a year digitizing old video footage and transferring things from old external drrives (the 16 tb drive is about a year old).  So things have been ballooning data wise very quickly.   I think ultimately Ill have to migrate to some other type of solution.  Was looking at maybe purchasing 72 terabytes of additional storage for both backing up existing and being able to store additional footage right now Im basically maxed out.

If you are going that direction, then you really should check out ZFS.  I have about 40TB here and rather than expand, I'm deleting things based on household importance.  About 50% of the saved recordings will never be looked at again, so what's the point in saving it?  I got into a data hoarding mode ... but now that it will cost $350+ to expand, there are other things we'd rather do with that cash.  Everyone needs to figure out their limits for themselves.  Some people think 2TB is way too much, so all perspectives are valid.

When I buy storage, I buy pairs. If I can't backup the data, then it isn't important enough to keep at all. It's a mindset.  About 20 yrs ago, I lost 80% of our data. It took a few more years, but eventually I got backup religion. 

I have 2 types of backups.  Daily, automatic, versioned backups for typical computer stuff - docs, settings, email, normal stuff.  Minimum is 90 days, but for high risk stuff, it is 180 days.  

Then there's the media backups for huge files. That's video and audio stuff.  Those are just an rsync mirror, created a few times a week, after new content is added.  I've had enough disk failures over the decades to know what is truly important and what is nice to have and what is just eating storage, completely unimportant.  

There are some storage areas that are never, ever, backed up. Never. That's a deliberate choice. Mainly areas on a laptop that is a copy of entertainment files for travel and no other purpose.

---

### Post by todolinuxvidz1 on 2022-04-27
Thanks all for your help.

---

