---
title: "baffled!"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by gatordoc on 2008-08-19
Ok this is a different thread, but similar to what i've been trying to figure out.
I just installed a fresh hardy heron onto my computer which was working before I moved. For whatever reason it would finish loading up the GUI so i had to redo everything...fine.

So i have 2 HD's each 250GB, one is SATA the other is an IDE slave to the DVDROM (which i use as a backup)

i unplug the IDE HD to install and everything is great. after doing all the updates..etc i then turn off everything and replug the IDE HD back in

it finds it NP upon boot up as /media/disk and an icon pops up as 250.1MB Media and I can see my contents no problem.

OK I do df
then fdisk -l

and it tells me that i have a HD on sdb1..etc (the boot HD ..SATA)
and that there is one on sda1 as the other, IDE disk.

fine

I now do gedit /etc/fstab to give the other HD a permanent home
i create in / the folder "backup"
i put in

/dev/sda1   /backup     auto    defaults 0 0

I reboot

i do df, then fdisk-l and magically the SATA HD is now sda1 and the other on is sdb1 but the mount is just for the sda1 so if i do 

cd /backup

it comes up as the same thing that is in the home /

So i do the same thing and change the names

reboot

same freakin thing!!

wtf

why cant i dictate what HD i want to be sda1 or sdb1 or shouldnt it freakin keep them the same ???

Please for the love of god help me.. i never had this issue with gutsy or feisty...

I need this CPU up and running bc i have to reinstall ALL of my freakin programs and test them to see that they work before i can continue working with them.

thanks ubuntu community..

ps here is my last fdisk -l

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61af3f30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c59a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29644   238115398+  83  Linux
/dev/sdb2           29645       30401     6080602+   5  Extended
/dev/sdb5           29645       30401     6080571   82  Linux swap / Solaris


and df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            234378684   4566472 217906444   3% /
varrun                 1037712       100   1037612   1% /var/run
varlock                1037712         0   1037712   0% /var/lock
udev                   1037712        52   1037660   1% /dev
devshm                 1037712        12   1037700   1% /dev/shm
lrm                    1037712     39760    997952   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb1            234378684   4566472 217906444   3% /backup
gvfs-fuse-daemon     234378684   4566472 217906444   3% /root/.gvfs


so you can see that backup and / are the same freakin folder

---

### Post by silkstone on 2008-08-19
As far as I know, drives have to be mounted under either /mnt or /media, so your new mount point 'backup' should be created under either of those - e.g. /media/backup

If you mount under /mnt the drive icon will not show on the desktop. If you mount under /media it will.

---

### Post by gatordoc on 2008-08-20
It will not allow me to mount something that is in /media/disk

also this doesnt explain why doing fdisk..etc shows that the main HD is mounted on sda1 on one boot up then sdb1 the next time I boot...

---

### Post by gatordoc on 2008-08-20
[//http://ubuntuforums.org/showthread.php?t=802699&highlight=hard+drive+mounting]("http://ubuntuforums.org/showthread.php?t=802699&highlight=hard+drive+mounting")

I found an answer here

Using th UUID number I can now mount properly. Thanks people in that post!

---

