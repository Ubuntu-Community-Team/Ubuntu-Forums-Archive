---
title: "Grub error 15 won't fix"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by oldrocker99 on 2008-08-10
I tried to install Kubuntu. GRUB Error 15. 

Super GRUB Disk ran all night without finding what it was looking for.

I tried another hard drive. GRUB error 15. 

Same story with Super GRUB Disk.

I installed Ubuntu on that same drive. GRUB Error 15. 

I tried to reinstall GRUB from the CD. It said "Success!"

GRUB Error 15.

Now what?

:guitar:

---

### Post by wolfen69 on 2008-08-10
grub error 15 : "File not found This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 16 : Inconsistent filesystem structure This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB. "

did you check the cd for errors?

---

### Post by oldrocker99 on 2008-08-10
Hmmm...no, I didn't, but I had a perfect install from the same CD before. I'll try that, but I doubt it's the CD.

Back in a few.

:guitar:

(sigh)

---

### Post by oldrocker99 on 2008-08-10
The CD is fine...can anyone help? I saw no errors in the /boot/grub/menu.lst file.

:guitar:

---

### Post by logos34 on 2008-08-10
post output of:

sudo fdisk -l

If you have more than one drive connected what is the Bios **hard disk** boot order?

---

### Post by oldrocker99 on 2008-08-10
Here it is:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17fa3c38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24791   199133676    7  HPFS/NTFS
/dev/sda3           24792       24792        8032+   f  W95 Ext'd (LBA)

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1043a06e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36483   293049666    7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00097505

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       29759   239039136   83  Linux
/dev/sdc2           29760       30515     6072570    5  Extended
/dev/sdc5           29760       30515     6072538+  82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       29649   238155561   83  Linux
/dev/sdd2           29650       30401     6040440    5  Extended
/dev/sdd5           29650       30401     6040408+  82  Linux swap / Solaris

---

### Post by oldrocker99 on 2008-08-10
Oh, yeah. I had originally had set the BIOS to start with the disk I had installed Ubuntu on, and I got a "No bootable disks found. Insert bootable disk and press ENTER." Then I, having read it on a forum, set the boot order in the BIOS as a non-bootably disk first. That's when I started going into GRUB, and getting the Error 15.

:guitar:

---

### Post by logos34 on 2008-08-10
Which disk are you booting from? You need to disconnect one of the ubuntu disks to avoid further confusion (sdc or sdd)

---

### Post by oldrocker99 on 2008-08-10
I'm booting from scd. Sdd is a data disk only and has no boot partition, although it is Linux-formatted.

:guitar:

---

### Post by oldrocker99 on 2008-08-10
I'll also add that that disk's /boot/grub/menu.lst shows:

(snip)

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=161d5053-96c0-496c-a024-49b4bffe2d9b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=161d5053-96c0-496c-a024-49b4bffe2d9b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet


...and GRUB identifies the location of /boot/grub/stage-1 as (hd3,0).

HOWEVER:

There is no /boot/initrd.img-2.6.24-16-generic, only a /boot/initrd.img-2.6.24-16-generic.bak. There's a Gzipped /boot/initrd.img-2.6.24-16-generic file, but it won't decompress.

Arrgghh.

:guitar:

---

### Post by logos34 on 2008-08-10
initrd.img is normally gzipped archive...take off the '.bak' suffix and use that instead...

Change '(hd3,0)' to to (hd**0**,0)


gksudo gedit /path/to/boot/grub/menu.lst

or gksudo nautilus 

for admin privileges

Restore grub to mbr (link my signature) so that it points to sdc root

---

### Post by bumanie on 2008-08-10
Reinstalling grub to mbr, does not fix grub error 15 as far as I know. The problem, most often, is that grub can't find the correct kernel image to boot. Go [here]("http://users.bigpond.net.au/hermanzone/p15.htm"). About 2/3 down the page there are grub errors and fixes.

---

### Post by oldrocker99 on 2008-08-10
OK, I've done Yet Another Reinstall, gone to the GRUB pages, installed GRUB (again), edited the /boot/grub/menu.lst file. Crossing my fingers.

I really don't want to go back to XP. I've been using Ubuntu since April. I tried to install OSS and my system got completely hosed. I managed to copy my /home directory to another disk, and figured a reinstall would do the trick. That was last Tuesday.:(

Here goes. Thanks for the advice.

:guitar:

---

### Post by ace007 on 2008-08-10
[http://ubuntuforums.org/showthread.php?t=796640](http://ubuntuforums.org/showthread.php?t=796640)

Read my post, #4.

Cheers!

---

### Post by oldrocker99 on 2008-08-12
FIXED!

I downloaded the Ubuntu Studio ISO and installed it. With only one small GRUB error, it installed perfectly and I'm finally back up and running.

Thanks for all the suggestions!

:guitar::guitar::guitar:

---

