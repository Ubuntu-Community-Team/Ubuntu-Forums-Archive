---
title: "[SOLVED] 2nd Hard Drive"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Unotforme on 2008-07-14
Hi there,

I'm completely new to Linux, but I've heard lots of good things about it, so I decided to go all in. I've managed to get Ubuntu installed and running. I have an older PC. I have a P4 2.6, 1 gig ram, and 2 40 GB hardrives. I've gone to Places>Computer and can see my second hard drive, but I can't access it (Error states 'unable to mount location'). I've tried right clicking the drive and try the mount option but still to no avail. How do I access this drive?

---

### Post by Inxsible on 2008-07-14
> **Unotforme said:**
> Hi there,

I'm completely new to Linux, but I've heard lots of good things about it, so I decided to go all in. I've managed to get Ubuntu installed and running. I have an older PC. I have a P4 2.6, 1 gig ram, and 2 40 GB hardrives. I've gone to Places>Computer and can see my second hard drive, but I can't access it (Error states 'unable to mount location'). I've tried right clicking the drive and try the mount option but still to no avail. How do I access this drive?What is the filesystem on that drive? Which version of Ubuntu did you install?

Can you open up a terminal and issue this command and post back the results```
sudo fdisk -l
```

---

### Post by BGFG on 2008-07-14
Hi, was the drive ntfs formatted ?

---

### Post by Unotforme on 2008-07-14
I've installed Ubuntu 8.04

Here is the result from the command you gave me:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41172ba5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc421224

   Device Boot      Start         End      Blocks   Id  System

The drive is a slave, and was used under XP (NFTS)

---

### Post by Inxsible on 2008-07-14
> **Unotforme said:**
> I've installed Ubuntu 8.04

Here is the result from the command you gave me:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41172ba5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc421224

   Device Boot      Start         End      Blocks   Id  System

The drive is a slave, and was used under XP (NFTS)
That doesn't look right !!!

It says that there are no partitions on the drive sdb...so maybe its unformatted.

Can you boot into your XP ?

---

### Post by Unotforme on 2008-07-14
Ubuntu is the sole OS on my system, so no, I can't get into XP.

---

### Post by BGFG on 2008-07-14
Try 
```
 sudo nautilus
```

and try to mount it. if not then maybe you should allow your machine to update itself. if it's a fresh install there's some samba and NTFS utilities updates you may need.

---

### Post by Unotforme on 2008-07-14
This is what I get:

seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:8096): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I guess I'll try the update and see what happens.

---

### Post by Inxsible on 2008-07-14
> **Unotforme said:**
> Ubuntu is the sole OS on my system, so no, I can't get into XP.Then all you need to do is simply format the second drive using Gparted and make some partitions on it.

---

### Post by BGFG on 2008-07-14
Yup, allow your system to update then format the second drive's butt.

---

### Post by Unotforme on 2008-07-14
This is what I ran in Terminal:

sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  jfsutils ntfsprogs reiser4progs xfsprogs
The following NEW packages will be installed:
  gparted
0 upgraded, 1 newly installed, 0 to remove and 224 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Looked good until the last two lines...

---

### Post by AnLGP on 2008-07-14
I don't think this has anything to do with the HD but do a 

sudo apt-get install update
sudo apt-get install upgrade

it says you have 255 packages not upgraded.  I don't think that has anything to do with your issue at hand, though.

---

### Post by Inxsible on 2008-07-14
> **Unotforme said:**
> This is what I ran in Terminal:

sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  jfsutils ntfsprogs reiser4progs xfsprogs
The following NEW packages will be installed:
  gparted
0 upgraded, 1 newly installed, 0 to remove and 224 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Looked good until the last two lines...you probably have another package manager like Synaptic or Add/Remove open. I would also advise to use the GParted that is on the live Cd.

Its much easier that way. The drive that you are formatting should not be mounted while performing operations on it. I find that the Live CD version is best for doing things like these once in a while.

---

### Post by Unotforme on 2008-07-14
I'm told there are 233 updates available, should I install them all (I don't know what most of them are)?

---

### Post by Inxsible on 2008-07-14
> **Unotforme said:**
> I'm told there are 233 updates available, should I install them all (I don't know what most of them are)?Yes. Updates are mostly good unless they break your system of course ;)

Just click yes, enter your administrative password and sit back and relax....its gonna take a while to download and install depending on your internet connection.

---

### Post by Unotforme on 2008-07-14
Ok I'll run the updates through the night (I have a slower net connection) and see if I can get anywhere tomorrow. Thanks everyone for your help.

---

### Post by BGFG on 2008-07-14
Will look out for your progress tomorrow.

---

### Post by Unotforme on 2008-07-14
Ok. All my updates are in and didn't crash my system\\:D/ I've got gparted installed. But when I run it I'm told I'm not in root. How do I get there? Is there a help command for gparted (gparted -h)?

---

### Post by Inxsible on 2008-07-14
> **Unotforme said:**
> Ok. All my updates are in and didn't crash my system\\:D/ I've got gparted installed. But when I run it I'm told I'm not in root. How do I get there? Is there a help command for gparted (gparted -h)?Are you trying to run from a terminal?

In that case you need to issue ```
sudo gparted
``` Else if you select it from the menu, it should ask you for your administrative password

---

### Post by Unotforme on 2008-07-14
Ok. I'm running gparted (partiton editor) from system>administration. I've can see my second hard drive (/dev/sbd). It shows partiton unallocated and file system unallocated. Do I select Partiton>New and go from there?

---

### Post by fenian on 2008-07-14
Yes be sure to choose a more linux friendly format ext3 is a safe choice though I prefer to use XFS on m drives where I store audio/video files.

---

### Post by Unotforme on 2008-07-14
Should I have the 2nd drive as extended or a partiton on it's own?

---

### Post by Unotforme on 2008-07-14
Logical partition is not an option. Also XFS is unavailable (as are several others).

---

### Post by Inxsible on 2008-07-14
> **Unotforme said:**
> Ok. I'm running gparted (partiton editor) from system>administration. I've can see my second hard drive (/dev/sbd). It shows partiton unallocated and file system unallocated. Do I select Partiton>New and go from there?
Yes !! :)

---

### Post by Inxsible on 2008-07-14
D'oh !!! #-o

didn't see the third page

---

### Post by Unotforme on 2008-07-14
All righty, looks like I've got my 2nd HD up and running. Thanks for the help.

---

