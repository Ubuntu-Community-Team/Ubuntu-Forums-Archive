---
title: "DVD write errors...getting desperate, help would be most welcome!!"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by django0909 on 2008-09-12
Hi guys,

I'm on a Mac right now, so I'm afraid I can't offer specifics, but every single time I try to write anything to DVD, I get i/o errors. The same drive writes to CD with no problems, but refuses to write anything to DVD.

I also can't start nautilus as root while the blank DVD is in the drive.

Any help at all would be so welcome.

Thanks!

--django

---

### Post by gvartser on 2008-09-12
DVD - + format problems maby?

/g

---

### Post by django0909 on 2008-09-12
Do you mean try different DVD's?

---

### Post by halitech on 2008-09-12
could be a dying drive but try a different format of dvd first and see what happens

---

### Post by django0909 on 2008-09-12
The drive is brand new. I'm starting to wonder if it's the way I installed it, but then it wouldn't write anything at all, would it?

---

### Post by halitech on 2008-09-12
ok, it shouldn't be the drive if its new. What make and model of drive is it and what kind of dvds are you trying to use?

---

### Post by django0909 on 2008-09-12
The drive is a Philips, (not sure on the model number, I'm at work right now, can get it tonight), and the disks are Tesco own brand, which is probably what's causing the problem.

---

### Post by halitech on 2008-09-12
most drives should handle both but some are only + or - and if the dvds are cheap you can run into problems as well

---

### Post by django0909 on 2008-09-12
What do you mean by only + or -?

---

### Post by jerome1232 on 2008-09-12
If you look at the dvd's they'll be dvd-r or they'll be dvd+r, it's less common now but some burners can only burn to dvd-r some only dvd+r. Most can do both.

---

### Post by halitech on 2008-09-12
if you look at a dvd it will say DVD-R or DVD+R. There are 2 different formats and if your drive only supports 1 and you try to use the other, it won't work

Check here for more info
[http://en.wikipedia.org/wiki/DVD](http://en.wikipedia.org/wiki/DVD)

---

### Post by django0909 on 2008-09-12
Ah right. Is +r rewritable, and -r write-only? These disks are write-only...

---

### Post by jerome1232 on 2008-09-12
No they are both record only rewritables are either dvd-rw or dvd+rw

---

### Post by django0909 on 2008-09-12
I'll have a read later. I'm at work right now so have to keep flicking back and forth. Thanks for the help, will try different disks and report back!

---

### Post by django0909 on 2008-09-12
I've changed the CD's and I'm still getting the same errors.

> /dev/scd1=/home/dan/Desktop/movie.iso
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/dan/Desktop/movie.iso of=/dev/scd1 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/scd1: "Current Write Speed" is 2.5x1352KBps.
BraseroGrowisofs stdout:           0/2202679296 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/2202679296 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2270)

Could the mount point of the drive be the problem?

---

### Post by django0909 on 2008-09-12
Sorry for the repeat post. Here is my fstab, and I don't see /dev/scd1...

Does it need to be in there?

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=222b71ee-9d1b-490d-b960-c2b1432d51a1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=42b9a48d-cd3c-4c4f-ad23-17019d1f569f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by halitech on 2008-09-12
do you have 1 cd/dvd or 2?

give K3B a try, I find it works everytime for me

---

### Post by django0909 on 2008-09-12
I have one DVDROM and one DVDRW. k3b gives the same error :(

---

### Post by halitech on 2008-09-12
if you put a dvd in the burner, does it show as mounted?

---

### Post by django0909 on 2008-09-12
Where do I check that? And what do I do if it isn't?

---

### Post by halitech on 2008-09-12
open a terminal and do
```
sudo fdisk -l
```then post the info back here

---

### Post by django0909 on 2008-09-12
I will do just that in the morning. Thanks for the help so far!

---

### Post by django0909 on 2008-09-13
Right, here we go again. The output of 

> sudo fdisk -l

gives this,

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00080c28

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9553    76734441   83  Linux
/dev/sda3            9554        9729     1413720    5  Extended
/dev/sda5            9554        9729     1413688+  82  Linux swap / Solaris


I'm pretty sure my DVDRW has to be in there somewhere. How do I sort that out?

--django

---

### Post by django0909 on 2008-09-13
Edit: I'm now going to try burning DVD's in Damn Small Linux, (as it's the only other live CD I have kicking about), to see if I get anywhere :S

No joy at all :(

k3B gives the following errors, same sort of thing as Brasero

> System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-17-generic
Devices
-----------------------
PHILIPS DVDR885P P1.7 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R]

Burned media
-----------------------
DVD+R

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 8.2x1352KBps.
:-[ WRITE@LBA=0h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1075527 -dvd-compat -speed=8 -use-the-force-luke=bufsize:32m 



Help!!!

---

### Post by cygnis1 on 2008-09-14
I also am having problems with my dvdr.  I have tried Brasero and K3b, and neither of them sees the blank dvd disk.  I can burn to cd without a problem. I looked in cd-rom information and under can write to dvdr it says no.  How can I reconfigure this so it will write to the dvd?  I have written to dvds before.
Thanks,
Cygnis1

---

### Post by halitech on 2008-09-14
> **django0909 said:**
> Right, here we go again. The output of 



gives this,



I'm pretty sure my DVDRW has to be in there somewhere. How do I sort that out?

--django

All i see is your primary hard drive that is 80 gig in size. Did you have a blank dvd in the drive or a written one?

---

### Post by mc4man on 2008-09-14
better to run this to sort out your dvd drives, their device nodes and dev links (if you have media in each drive before running even better

```
sudo lshw -C disk
```


> I have one DVDROM and one DVDRW. k3b gives the same error

your fstab only has an entry for one drive

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=222b71ee-9d1b-490d-b960-c2b1432d51a1 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=42b9a48d-cd3c-4c4f-ad23-17019d1f569f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0 

If you have 2 drives add another entry  and reboot
> /dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

---

