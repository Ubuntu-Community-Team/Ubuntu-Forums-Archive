---
title: "Floppy Drive No longer Listed"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by ObiWanBenDover on 2008-09-18
Floppy drive is no longer listed in Computer - File Browser.

Used to automount but is now MIA.

**_fdisk:_**
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00080c8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4725    37953531   83  Linux
/dev/sda2            4726        4865     1124550    5  Extended
/dev/sda5            4726        4865     1124518+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1fcacef6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

**_fstab:_**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b0d9f981-a62f-4340-8217-04405b5034b1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=78cde2c5-82d3-4b54-8d08-c69f79f00e68 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Any help is appreciated

---

### Post by LowSky on 2008-09-18
Do you need to use a floppy drive? I haven't used a floppy since 2003 I think...?

 to mount a floppy in terminal type
mount /dev/fdo /media/floppy


check that your /etc/fstab file contains the following line:
/dev/fd0 /media/floppy auto rw,user,noauto 0 0

---

### Post by ObiWanBenDover on 2008-09-18
I'm not a big user of the floppy either, but I got one and it ought to work...

If you look at my original post, fstab has floppy0 listed instead of floppy.

I tried using mount with floppy and floppy0:
obiwanbendover:~$ mount /dev/fdo/media/floppy
mount: can't find /dev/fdo/media/floppy in /etc/fstab or /etc/mtab

obiwanbendover:~$ mount /dev/fdo/media/floppy0
mount: can't find /dev/fdo/media/floppy0 in /etc/fstab or /etc/mtab

---

### Post by Kellemora on 2008-09-18
HI Obi Wan

I never could get my floppy to work at all until I changed my line to read exactly like this.

/dev/fd0 /media/floppy0 auto,umsdos,vfat,ext2 rw,user,noauto,exec,utf8 0 0

Now it works just fine except I can only use it in H1440 mode.

For some reason Ubuntu does not recognize:
fdformat /dev/fd0H1440 it only recognizes fdformat /dev/fd0 
H1440 seems to be the default?????  With no other options that I've learned about yet.

Good Luck

TTUL
Gary

---

### Post by ObiWanBenDover on 2008-09-18
Thanks Gary. I made the change you suggested but still no luck.  The floppy is not recognized.  If I start Ubuntu with any old disk in the floppy drive I get the red drive light and a 'non-system' disk error message so it seems the drive is OK physically.

---

### Post by Kellemora on 2008-09-20
Hi Obi

I'll check a couple of other things when I get home tonight to see if I can come up with something for you.

Sometimes it helps to know exactly how other users set-up files appear in Ubuntu, to make comparisons.
Don't know why, but they are quite a bit different in Debian.  What works perfectly in Ubuntu don't work at all in Debian, at least not for me.

I do know this, the floppy MUST BE a 1.44 floppy  720 and 2.0 floppies are not recognized by Ubuntu for some reason.  That's a problem I'm still working on myself since MOST of the stuff I have is on 2.0 floppies.

I bought an entire CASE of 3M pre-formatted 1.44 MB floppies, I have only two drives that could read them or use them.  Did some checking and found out they are NOT 1.44 MB, they are 2.0 MB formatted to 1.44 Mb which is not recognized except by Doze and MAC and then only a few later drives recognize them.
All other drives cannot see track 0 as they don't move that far I guess.  It must be the low level format that messes them up?

I'll post my set-up files this evening when I get home!

TTUL
Gary

---

### Post by Kellemora on 2008-09-20
Hi Obi

I was rereading your posts and picked up on something.

It appears from the text on the screen that you are typing
an o (lower case letter o) instead of a 0 (a numeral zero).

Here is the lines from your post:
I tried using mount with floppy and floppy0:
obiwanbendover:~$ mount /dev/fdo/media/floppy
mount: can't find /dev/fdo/media/floppy in /etc/fstab or /etc/mtab

obiwanbendover:~$ mount /dev/fdo/media/floppy0
mount: can't find /dev/fdo/media/floppy0 in /etc/fstab or /etc/mtab 

Try doing the mount using mount/dev/fd0/media/floppy and see what happens!

TTUL
Gary

---

