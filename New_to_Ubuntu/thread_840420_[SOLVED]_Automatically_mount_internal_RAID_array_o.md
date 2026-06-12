---
title: "[SOLVED] Automatically mount internal RAID array on startup"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by batfastad on 2008-06-25
Hi everyone
I've been messing about with Ubuntu Server edition this past week and I'm gradually getting the hang of it.
Eventually I want to set up this server from scratch again, and use it as a NAS in a small business environment

I have a RAID 6 array inside this server that will have various shares that will be shared out through Samba. I'm using a 3Ware 9690SA RAID card and it seems to be working excellently so far.

If the machine restarts for whatever reason, I would like it to have /dev/sda automatically mounted on restart, so that the Samba shares can be accessed without any admin intervention.

I assume this is possible, anyone know how/where I need to edit to get this done?

I had some problems creating the partition in the first place (I found out GParted has trouble with partitions >1TB) but I used cfdisk to make one large partition of 1.4TB, then mkfs to format it as ext3

Thanks, B

---

### Post by cozmicharlie on 2008-06-25
You need to edit etc/fstab.  This should help [http://ubuntuforums.org/showthread.php?t=802699](http://ubuntuforums.org/showthread.php?t=802699)

My Raid is set up as follows in fstab:
/dev/md1 /media/music ext 2 defaults 0  2

Where:
/dev/md1 is the raid device
/media/music is the mount point
ext2 is the file sytem

You will need to change these for your set up.

---

### Post by batfastad on 2008-06-25
Ok that's brilliant help right there! :)
I also see it's recommended to use /media for mountpoints rather than /mnt. This must be different because when I used RedHat on a PS2 I think that was all based around /mnt
Anyway...

There might be a problem that I need to solve first though.
When I do:
```
sudo fdisk -l
```

I get the following notification from fdisk:
Disk /dev/sda doesn't contain a valid partition table
Then fdisk goes on to list my other drive, which has Ubuntu installed on it.

I created the partition using cfdisk, and then formatted it as ext3 with mkfs
Couldn't use GParted because it was giving me errors... I think because I was trying to create partitions >1TB in size. Also I always try and use command-line for things like this whenever possible.

There's no data on this RAID array yet.

What's the best way to create one massive partition on this RAID array at /dev/sda and format it?
cfdisk has clearly created something that fdisk doesn't like, although it works perfectly well mounting/umounting and storing data

Also, this drive will eventually contain data shared out to Windows and Macs using Samba/Netatalk respectively.
What file system should I use?

Is ext3 any better than ext2, or will both be fine?

Thanks, B

---

### Post by MasterSander on 2008-06-25
ext3 has journaling as well. For sharing between mac and windows and linux, ntfs is preferred. Mac has problems with ext3 and windows as well. ntfs is supported by mac and linux at install.

---

### Post by cozmicharlie on 2008-06-25
Glad the thread helped you.   

If it works perfectly mounting and unmounting I would not worry about the message.   

ext3 should work for you.  I don't have any problems with my device being accessed in Windows.  It should mount in Windows as a Samba share. Personally, I prefer ssh over Samba from Windows (I use tunnelier on windows and open ssh on Ubuntu) but everyones needs are different. 

As per the partitions - did you build it with multiple partitions?  You may want to consider LVM on Raid for managing partitions.  This has a good explanation [http://linux-raid.osdl.org/index.php/Linux_Raid](http://linux-raid.osdl.org/index.php/Linux_Raid)

---

### Post by batfastad on 2008-06-25
What would be the best way to make that partition?
I want to make sure I get it perfect, before it's filled with data and then impossible to move around!

I thought the filesystem was irrelevant from the sharing point of view, since it gets shared out using whatever protocol.

It sounds like ext3 is the one. The RAID 6 array is tied to the controller so it's not like it will be moved onto a different machine/OS.

I want that RAID 6 array to be 1 massive partition. I'll then be setting up various shares for PC and/or Mac within that. Need to use Samba and Netatalk... not sure our users will appreciate having to use SSH.

Does that LVM RAID thing involve using Linux to manage the RAID? We have a hardware RAID controller that currently takes care of that.

So many questions :D

Cheers, B

---

### Post by cozmicharlie on 2008-06-25
LVM does involve Linux (LVM has been in the stable Linux kernel series for a long time now)- usually set up along with software raid.  LVM is basically just a virtual partitioning system so if your hardware does it, you should not need it.

---

