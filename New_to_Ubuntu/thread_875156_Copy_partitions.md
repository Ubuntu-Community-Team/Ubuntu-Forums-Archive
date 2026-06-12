---
title: "Copy partitions"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by pgte3 on 2008-07-30
I have a hard drive with the following partitions:

pgte3@pgte3-laptop:~$ sudo fdisk -l
[sudo] password for pgte3: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed8eed8e

Device Boot Start End Blocks Id System
/dev/sda1 1 192 1536000 27 Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 192 11316 89358398+ 7 HPFS/NTFS
/dev/sda3 11317 19457 65392582+ 5 Extended
/dev/sda5 14047 19229 41632416 83 Linux
/dev/sda6 19230 19457 1831378+ 82 Linux swap / Solaris
/dev/sda7 11317 13927 20972794+ 83 Linux
/dev/sda8 13928 14046 955836 82 Linux swap / Solaris

/dev/sda7 and /dev/sda8 are a 32 bit install of Ubuntu 8.04.

/dev/sda5 and /dev/sda6 are a 64 bit install of Ubuntu 8.04.

How can I copy my 32 bit install from /dev/sda7 and /dev/sda8 to /dev/sda5 and /dev/sda6? I would like to have two versions of the same 32 bit install, both with all the modifications I have made to the original on /dev/sda7 and /dev/sda8.

P.S. I don not know what /dev/sda1 is.

---

### Post by LinuxRocks713 on 2008-07-31
**WARNING: Data loss may occur! Do not switch off the power.**

To copy /dev/sda7 to /dev/sda5, use this (provided you are part of the disk group):
```

dd if=/dev/sda7 of=/dev/sda5
#if you want to erase all data so there is no trace on sda7:
dd if=/dev/zero of=/dev/sda7

```


To copy /dev/sda8 to /dev/sda6, use this (provided you are part of the disk group):
```

dd if=/dev/sda8 of=/dev/sda6
#if you want to erase all data so there is no trace on sda8:
dd if=/dev/zero of=/dev/sda8

```

PS: /dev/sda1 is probably an recovery partition that restores Win$$$$ Vista$$$(/dev/sda2) on your computer. Leave it alone.

---

### Post by Atomic Dog on 2008-07-31
Just a note of caution.  dd can be powerful but dangerous.  If you make a mistake you can hose things pretty bad.  I always look at dd as meaning data destroy because it will wipe out everything on the destination.  Just be careful and make sure you have it right before hitting the return key!

---

### Post by indytim on 2008-07-31
I think GParted Live has a partition copy feature.  Sorry, at work on the "other" ops so I can't verify.  If I'm correct, you may want to go that route (picture is worth 1000 keystrokes :)).

IndyTim

---

### Post by drs305 on 2008-07-31
> **indytim said:**
> I think GParted Live has a partition copy feature.  Sorry, at work on the "other" ops so I can't verify.  If I'm correct, you may want to go that route (picture is worth 1000 keystrokes :)).

IndyTim

Gparted does have a 'copy partition' function. You would have to run it from the gpartedCD or from liveCD as you can't work with mounted partitions and of course your root and home partitions would be mounted if you tried it from within ubuntu.

---

### Post by logos34 on 2008-07-31
If you image the partition with dd or gparted, remember to change the UUID or else you'll have problems mounting them:

sudo tune2fs -U random /dev/sda5

then edit /etc/fstab and /boot/grub/menu.lst ('kernel' and 'kopt' line)

You don't need 2 swaps.

---

### Post by pgte3 on 2008-07-31
Thanks, the dd program seems powerful. I will study it before attempting to use it.

Is the dd program a good way to back up an Ubuntu partition or partitions that hold data? What is the common or preferred way to back up various partitions on a hard drive to say a USB hard drive?

---

### Post by logos34 on 2008-07-31
> **pgte3 said:**
> 
Is the dd program a good way to back up an Ubuntu partition or partitions that hold data? What is the common or preferred way to back up various partitions on a hard drive to say a USB hard drive?

no, you don't want to use dd for backups of data. 

Try Simple Backup (gui).  Or make a **.tgz** archive.  Or **cp -a**. 

Here's how I backup /home:
$ cd /
$ sudo tar czvpf /media/hda5/homebackup.tgz /home/user

Rsync is another tool (grsync for gui version)

---

### Post by pgte3 on 2008-07-31
I should have looked before I asked:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

This link discusses backing up an entire partition, which is what I am interested in doing. This way I would have my entire Ubuntu system, provided I keep my data in the same partition.

Logos34 does this link layout a reasonable approach for backing up and restoring an entire Ubuntu install?

---

### Post by logos34 on 2008-07-31
you can certainly do it that way if you want...there's ten different ways to anything in linux...But I think a better way is to use tar for data partitions, and make an image of /, so that you can restore it EXACTLY the way it was before.

I use Partimage to clone / (which is fast because it copies only used disk space), and compressed tar for data

---

### Post by pgte3 on 2008-07-31
Thanks, there does seem to be a number of ways to do back ups. I will look at Partimage.

---

### Post by bodhi.zazen on 2008-07-31
If you start moving partitions in this way you are going to need to update /etc/fstab and /boot/grub/menu.lst

See this thread for general issues :

[How to run bleeding edge - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=316237") 

If you just want a back up, +1 partimage (or similar).

[uhelp]community/BackupYourSystem[/uhelp]

---

### Post by pgte3 on 2008-08-01
I checked out this link: community/BackupYourSystem and found it to be helpful, thanks.

---

