---
title: "Putting home on SD card (eeePc)"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by perfectturmoil on 2008-06-26
Hey all -

I'm having a bit of trouble.  I have an eeePc runing UbuntuEEE 8.04 (from what it seems, pretty much normal Ubuntu w/ a few graphic adjustments and tweaks for power usuage and whatnot - I still had to run a few of the tweak scripts to get appropriate power off..)

Anyways, since its only got a 4gb hard drive and since I have a 8gb SD card, I want to have /home be the card.. I formated the card FAT32 so that I would potentially be able to drop my files to windows easily (if necessary).  I guess that could be my first mistake.. 

I sorta followed the guide here (linked to by someone on this forum):  [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I didn't need to do any of the partitioning stuff.

So I did: find . -depth -print0 | sudo cpio --null --sparse -pvd /mnt/mount while my SD card /dev/sdb1 was mounted at /mnt/mount

Then moved my old home to backup and made a new home and attempted to add the mount stuff to /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=63670b60-929a-4cc0-a748-db192a265190 /               ext2    noatime,errors=remount-ro 0       1
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdb1     	/home 	auto	 nodev,nosuid 0 2
#/dev/sdb1	/home	auto	user,noauto,exec,utf8	0	0

#added per ubuntu-eee.com 
tmpfs     /var/log       tmpfs     defaults,noatime        0 0
tmpfs     /tmp           tmpfs     defaults,noatime        0 0
tmpfs     /var/tmp       tmpfs     defaults,noatime        0 0

```

First /dev/sdb1 was ubuntu's incorrect assumption during install that the card was a DVD (had the eee windows driver dvd copied on it)

Second /dev/sdb1 is pretty similar to what is listed on the help website but changed the type to auto instead.

Thrid /dev/sdb1 is how I used to have the card mounted at /mnt/mount just changed for home.

Second /dev/sdb1 entry allowed me to boot, but gave some read write errors for /home/perfectturmoil/.[filename] saying that the files should be owned by the user and should have permission 644.

Third /dev/sdb1 entry did not work saying that there should be a /home/perfectturmoil and that it couldn't find it.  

I've moved everything back for now.. It seems to be a file permission thing, either with the 'copy' command or the mounting in fstab.

Help would be much appreciated since I'd like to be able to hold a few programs and maybe an MP3 or two on this thing :- ]

---

### Post by perfectturmoil on 2008-06-27
Wow this forum moves fast - Already down like 5 pages...

Is bumping threads allowed?  Hope so.. Would definitely like to figure this one out...

Thanks
Dan

---

### Post by gn2 on 2008-06-27
I would suggest leaving things as they are.
If you move /home to the card, it will have to remain in the Eee all the time.
Better to just store your data files on the card and point your applications to it as required.
That way all your hidden .config files will remain in /home on the Eee internal storage and you will still be able to hot-swap the card.

---

