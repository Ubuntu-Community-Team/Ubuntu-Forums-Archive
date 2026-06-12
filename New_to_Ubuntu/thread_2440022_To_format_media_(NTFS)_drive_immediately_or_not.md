---
title: "To format media (NTFS) drive immediately or not"
date: 2020-04-04
forum: New to Ubuntu
---

### Post by purplegreendave2 on 2020-04-04
Hi, I'm effectively brand new to Linux - I've run some live USBs and VMs out of curiosity but never really did much with them. Please bear with/correct me as I'm sure to get some terminology confused if not outright wrong.

I'm running a Plex Server on Win 10, I've decided I want to scrap it and start up with Ubuntu.

Currently I have my OS & Apps on a 1TB drive (C:) and media on another drive (M:), both are obviously NTFS. The Media drive is getting close to full so I've ordered a new drive (which conveniently coincides with this whole software refresh). I have the C drive backed up and ready to wipe clean, I'll install Ubuntu on it (haven't decided if I want to use ZFS or EXT4 yet for this drive)

Then what I'm wrestling with is that other drive. I want to reformat it to EXT4. The new drive will also be EXT4 when it arrives and I'd like to set up SnapRaid and MergerFS (or something similar) when I'm up and running.

I don't know what the best way to get around formating the is. It goes without saying that I want to keep the data. Currently the options I'm playing with are:
[LIST=1]
[*]Install Ubuntu now. Mount the NTFS media drive. Shrink the partition as small as possible, make an EXT4 partition in the empty space. Copy over some data, shrink, expand etc. Sounds laborious but I could get it started this afternoon and realistically have it finished before the new drive shows up.
[*]Install Ubuntu now. Mount the NTFS media drive. When the new drive shows up format it as EXT4, copy everything onto it, format the old drive.
[*]Wait until the new drive arrives. Otherwise same process as #2
[/LIST]

Will the process of shrinking/expanding over and over again give as  "clean" a format as wiping the disk entirely? (If so then option 1 is  the winner and the rest of this doesn't matter other than as a thought exercise).

Part of (or my main) problem is I don't exactly understand how Linux handles drives other than knowing it doesn't assign drive letters like Windows. If I set up Plex to a point where it has indexed my files and I switch to another drive will everything go haywire?

A Windows example (in case I'm not explaining myself):
I have a drive (lets call it Disk1) and I assign it the letter M. On Disk1 there's a file and a folder - its path is M/Folder1/File1.
Next  I copy that file to another disk (Disk2) in the same folder structure. I swap disks in the machine. Maybe when I boot up Windows assigns it another letter, be that D or N or whatever. I fire up Disk Management, assign it the letter M and bam - apps don't know the difference they're just looking for M/Folder1/File1. 

I'm sure there's a way to make Ubuntu do this and maybe it will be obvious when I start giving it a try but I'd appreciate if someone could give me a decent springboard to start from.

---

### Post by TheFu on 2020-04-04
Shrink and shift is dangerous.  Wait for the new drive.
I&#8217;ve never used snapraid or mergefs.  
Every OS except Windows let's us mount storage - partition not drives - anywhere we need them.  Any empty directory works.  Don't confuse a drive with a partition.  On linux, that can wipe way too much data if you do.

Please make certain that you include some sort of backup solution with your storage plans.  No RAiD is any replacement for backups.

---

### Post by purplegreendave2 on 2020-04-04
> **TheFu said:**
> Shrink and shift is dangerous.  Wait for the new drive.
I thought that might be the case. I'll have to find some patience somewhere!

> **TheFu said:**
> Every OS except Windows let's us mount storage - partition not drives - anywhere we need them.  Any empty directory works.  Don't confuse a drive with a partition.  On linux, that can wipe way too much data if you do.
I understand the difference between drive and partition but I need to do some learning on how linux works with storage

> **TheFu said:**
>  Please make certain that you include some sort of backup solution with your storage plans.  No RAiD is any replacement for backups.
I've looked into cloud backup like backblaze as well as getting extra backup hard drives to stash at work as offsite backups. Honestly it's all just media, nothing that can't be found again. I've weighed the cost vs risks and I'm happy with a software parity drive. Any important documents are backed up on 2 cloud services.

---

### Post by TheFu on 2020-04-04
> **purplegreendave2 said:**
> I thought that might be the case. I'll have to find some patience somewhere!

Probably best.  The shift requires copying ALL THE DATA over, each time.

> **purplegreendave2 said:**
> 
I understand the difference between drive and partition but I need to do some learning on how linux works with storage

That can take a lifetime.  Linux storage can be easy or enterprise.  There isn't just 1 file system. There isn't just 1 volume manager.  We can have automatic replication between network storage, different computers, "snapshots" can send only changed data, of freeze all the storage blocked in used at this instant for some purpose, like backups, then forget they were frozen, all while the system keeps running without impacting storage performance. Also, we can say there's 50PB of storage when there's only 1TB so all the different programs are happy, until the storage runs out.  That's how all the online VPS guys do it.  They tell everyone you have 20TB or 20GB, but really on give everyone only what they use.

But in general, to keep it simple, create a partition, format that partition with a file system - ext4 - unless you have a specific reason to use something else, then mount the storage to any empty directory you like.  In general, any way that ext4 gets mounted is fine, but non-native file systems like NTFS or FAT-whatever, will have poor performance unless specific mount options are used which no GUI supports.  Also, NTFS or FAT-whatever don't support normal Unix permissions, so permissions for those are set only through the mount options and chmod/chown will not work.

When you mount storage, there are certain places to put it to avoid some issues with snap packages, but those places are NOT meant to be used for permanent storage based on the Linux standards.  But the Snap team decided they'd ignore those standards, so we all get to violate them or not have snaps work.  

The short answer is to mount your storage in /media/ somewhere.  For media servers, it is usually best to plan well for the future when you have more disks.
/media/D1
/media/D2
/media/D3
....
you get the idea.  Trust me.  I started with one 1TB disk.  Now I have over 32 TB and have bounced around a little on my mount locations.  Really wish I'd just done the D1, D2, D3, D4 .... thing.  Then below each of those, create directories for Movies, TV, Photos, Music, Videos, ....   Plex will merge all the storage together into a single view, so you don't need mergeFS or anything else.

> **purplegreendave2 said:**
> 
I've looked into cloud backup like backblaze as well as getting extra backup hard drives to stash at work as offsite backups. Honestly it's all just media, nothing that can't be found again. I've weighed the cost vs risks and I'm happy with a software parity drive. Any important documents are backed up on 2 cloud services.

I originally thought the same thing, then had a drive fail and lost all the data on may "parity" solution with 3 disks.  As I was putting stuff back (I was using optical media for backups), it was a huge waste of time. Many hours wasted.  Then I thought about how much a 4TB disk actually costs - today they are about $75, so less than 60 minutes of my rate.  It just wasn't worth my time NOT to have backup storage for media.  You'll have to figure the numbers for yourself.

The last 3 yrs or so, I've only been buying 8TB disks, but always setup LVs to be 4TB in size, never larger.  I use LVM.  An LV is sorta like a really smart, flexible, partition.  If you've ever use Veritas Volume Manager, that's what it is like.  LVM brings enterprise-class capabilities to our home storage systems.  ZFS does too, if you want to head in that direction.  ZFS on a single disk doesn't have all the same value that it does in a RAIDz2 setup.

Anyways, you don't need to learn all the storage stuff. There's much to be said for following the KISS method.

---

### Post by purplegreendave2 on 2020-04-06
> **TheFu said:**
> That can take a lifetime.  Linux storage can be easy or enterprise.  There isn't just 1 file system. There isn't just 1 volume manager.  We can have automatic replication between network storage, different computers, "snapshots" can send only changed data, of freeze all the storage blocked in used at this instant for some purpose, like backups, then forget they were frozen, all while the system keeps running without impacting storage performance. Also, we can say there's 50PB of storage when there's only 1TB so all the different programs are happy, until the storage runs out.  That's how all the online VPS guys do it.  They tell everyone you have 20TB or 20GB, but really on give everyone only what they use.
I'm learning that. Currently looking into the virtues (and complications) of zfs for the OS drive. I'm thinking as a complete newbie to Linux it's just another layer of things to learn so I'll probably start with ext4.

> **TheFu said:**
> The short answer is to mount your storage in /media/ somewhere.  For media servers, it is usually best to plan well for the future when you have more disks.
/media/D1
/media/D2
/media/D3
....
you get the idea.  Trust me.  I started with one 1TB disk.  Now I have over 32 TB and have bounced around a little on my mount locations.  Really wish I'd just done the D1, D2, D3, D4 .... thing.  Then below each of those, create directories for Movies, TV, Photos, Music, Videos, ....   Plex will merge all the storage together into a single view, so you don't need mergeFS or anything else.
My primary reason for wanting to use mergeFS isn't for Plex but for the downloaders, mostly Sonarr. My drive is almost full but I have several shows that aren't over. So much easier for Sonarr to have one directory hence the desire for mergefs.

I hear you on the capacities. I remember running XBMC way back when with 500gb and everyone thought I had so much storage. Then I got a 2tb external when I started with Plex. Upgraded to a 3.5" 6TB NAS drive and that's now full so I have an 8TB MyBook on its way to be shucked.


> **TheFu said:**
> I originally thought the same thing, then had a drive fail and lost all the data on may "parity" solution with 3 disks.  As I was putting stuff back (I was using optical media for backups), it was a huge waste of time. Many hours wasted.  Then I thought about how much a 4TB disk actually costs - today they are about $75, so less than 60 minutes of my rate.  It just wasn't worth my time NOT to have backup storage for media.  You'll have to figure the numbers for yourself.
The drive I just bought worked out to about $200 (Canadian prices). That's ~13 hours at my current wage. If it goes down it goes down. I still have Prime and Netflix, this is just a hobby. With SnapRaid I can buy a new drive and rebuild when it arrives. If that happens once every 2.5 years it's cheaper than backblaze and I can upgrade capacity at the same time[/QUOTE]

---

### Post by TheFu on 2020-04-06
You can move show directories. Not a big deal.

i wouldn't use ZFS for the OS.  Just data.  No way would i span storage volumes across different physical drives.  I&#8217;ve learned my lesson.

Downloading copyrighted material is illegal where i live.  Recording broadcasts is legal, however.

Today, saw a WD 12TB USB3 HDD for US$180. Considered it, but regardless, I&#8217;d split it into 4TB chunks for backup consistency.

---

### Post by Tadaen_Sylvermane on 2020-04-08
I use mergerfs & snapraid for my media. Currently just 2 2tb drives with a single parity. I'm fairly sure they will work fine with ntfs drives, but it is much better overall to have them all native to the system. I'm currently using ext4. Depending on your expected I/O that will likely be enough for you. I seem to be able to run 4 simultaneous reads mergerfs pool without issue from my server, possibly a few more. I do notice that very rarely if I try to write to the pool while something is actively running to one of my kodi machines the playback will stop. Restart and it's good. Little frustrating but for my layout here at my house / property it's mostly a non issue. I do my media uploads to the server middle of the night or when I know everyone that has a box is gone or otherwise occupied. They are simple, and effective for a small setup. 

If I had the funds though I would admittedly do a raid 6 or zfs raidz2 with 6 drives but as it stands now I'm not even close to reaching my current capacity and the way the world has all but shut down it won't be any time soon.

* EDIT * I missed the part about having a 1tb drive for os and apps. You will have a ton of free space left because an Ubuntu install + whatever doesn't take up much. You can use all of that free space for media storage with mergerfs and snapraid as it works based on directories, not devices.

---

