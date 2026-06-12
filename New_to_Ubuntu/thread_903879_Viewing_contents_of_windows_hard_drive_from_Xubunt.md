---
title: "Viewing contents of windows hard drive from Xubuntu livecd"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by dementedherring on 2008-08-28
I'm trying to resurrect an old laptop to run a flavour of linux. I tried the ubuntu livecd and viewing the windows files on the installed hard drive was simple as there's a desktop icon saying 30gb drive.
I then read that Xbuntu was a speedier on lower spec machines and as the laptop only has 512mb ram I thought I'd try this.
When running the xbuntu livecd there's no desktop icon for this drive and using Thunar File Manager I can't find the hard drive.

I realise this is an incredibly basic problem even for the absolute beginner talk but I can't seem to find the answer on the xbuntu help or searching so any advice gratefully recieved.

---

### Post by Pro-reason on 2008-08-28
If Xfce (Xubuntu) doesn't automount the drive, then mount it manually.

Create a mount point (e.g. with *mkdir ~/Desktop/Windows*); work out the name of your drive (e.g. with *sudo fdisk -l*); then mount it (e.g. with *sudo mount /dev/sdb ~/Desktop/Windows ntfs-3g*).  The exact command depends on the filesystem on the Windows partition, etc.

You might also want to make sure that your /etc/fstab file has an entry for that partition.

There are various guides for this sort of thing, e.g. [https://help.ubuntu.com/community/MountDevicesTroubleshooting](https://help.ubuntu.com/community/MountDevicesTroubleshooting)

---

### Post by nicedude on 2008-08-28
You could also use pysdm to mount it for you

COMMAND TO INSTALL IT

sudo apt-get install pysdm

COMMAND TO RUN IT

sudo pysdm


Then pick the drive and press mount and see if it does it for you. Also you might want to look at getting a program called Tweak Ubuntu as I think it works with Xubuntu and it has settings for allot of stuff including to have drives display on the desktop when mounted.

---

### Post by dementedherring on 2008-08-31
Thanks for the helpful advice, after a while playing with ubuntu and xbuntu I decided that although the speed of xubuntu was appealing I don't think *I'm* ready for the extra learning curve. So I've installed ubuntu and so far it's working beautifully it's recognised some of my older hardware which XP was a complete pain to setup :)

---

