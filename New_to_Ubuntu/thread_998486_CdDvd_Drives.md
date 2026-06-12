---
title: "Cd/Dvd Drives"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by bigal1932flying on 2008-11-30
(Not Relevant)I am receiving messages from gxine regarding my drives:
FAILED-could not access cdrom /dev/cdrom
Either create a symbolic link /dev/cdrom pointing to your cdrom device  or set your cdrom device in the prederences dialog.
FAILED- could not access dvdrom:/dev/dvd
Either create a symbolic link /dev/dvd pointing to your cdrom device or set your cdrom device in the preferences dialog.
In the check for DMA mode on DVD drive:
FAILED - could not read stats for /dev/dvd if you are using the ide-cd module ensure that you have the following entry in /etc/modules. conf:
options ide-cd dma=1
reload ide-cd module
otherwise run hdparm-d/ on your dvd device.
What does all this mean? Can anyone PLEASE help?
Output of "cat /etc/fstab":
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=017a9443-bc48-4ccc-9928-0857397f300d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=066888db-b3eb-419c-95fd-46388d4e84c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Ocxic on 2008-11-30
post the output of "cat /etc/fstab"

this just means gxine cannot get access to those drives. you'll either need to assign the proper drive paths in gxine preferences or create the links as required.

---

### Post by Ocxic on 2008-12-02
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

These are your cd-rom drives you'll need to figure out which is your CD and which is DVD drive then create links for gxine to use:

"sudo ln -s /dev/scd0 /dev/cdrom"
"sudo ln -s /dev/scd1 /dev/dvd"

The above commands would be assuming that scd0 is your cdrom and scd1 is your DVD drive if I'm wrong just switch the drive numbers around.

Forum Tip "Post a reply instead of editing your post, we'll usually get an e-mail notification automatically"

---

### Post by bigal1932flying on 2008-12-02
Have tried both commands and both times received reply "File exists".
By the way both of my drives are DVD drives.

---

### Post by bigal1932flying on 2009-01-14
Thought my Master DVD Drive might be playing so replaced it with a CD Drive.
Now the CD Drive will play Audio Disks but DVD's will not play in DVD Drive.
VLC returns the message:
Playback failure:
DVDRead could not open the disk "/dev/scd1".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/scd1'. Check the log for details.

---

### Post by mc4man on 2009-01-14
Run this and post (have a dvd in the drive

```
sudo lshw -C disk
```

---

### Post by Artemis3 on 2009-01-14
Try /dev/cdrom2, this is a Debian heritage ^_^'

---

### Post by bigal1932flying on 2009-01-15
Tried "sudo lshw -C disk" received this response:
 *-disk                  
       description: ATA Disk
       product: ST380215A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 5QZ5FMZ7
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0003b348
  *-cdrom:0
       description: CD-R/CD-RW writer
       product: CD-Writer+ 9500b
       vendor: HP
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.06
       serial: [HP      CD-Writer+ 9500b1.06KRBF071
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: SCSI CD-ROM
       product: DRW-1814BL
       vendor: ASUS
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.10
       capabilities: removable audio
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1

---

### Post by bigal1932flying on 2009-01-23
Have installed 8.04 on another hard drive. Dvd's just work no problem.
Why the hell doesn't this happen in 8.10?

---

### Post by mc4man on 2009-01-23
Out of curiosity run the sudo lshw -C disk again on your 8.04 install and compare to posted one

From previous post

> *-cdrom:0
description: CD-R/CD-RW writer
product: CD-Writer+ 9500b
vendor: HP
physical id: 1
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name: /dev/dvdrw
logical name: /dev/scd0
logical name: /dev/sr0
version: 1.06
serial: [HP CD-Writer+ 9500b1.06KRBF071
capabilities: removable audio cd-r cd-rw
configuration: ansiversion=5 status=nodisc

I don't believe that drive is a dvd drive, (if it isn't it shouldn't have had /dev/dvd links

The asus, who knows ...?

---

### Post by bigal1932flying on 2009-01-24
The HP Drive is the CD Drive I fitted after problems with the original DVD Drive. The ASUS Drive is definitely a DVD Drive.
 Sorry but when I tried the "sudo lshw -C disk" in Hardy I forgot to put a DVD in the Drive.
Howevever the output was:
*-disk                  
       description: ATA Disk 
       product: ST340014A 
       vendor: Seagate 
       physical id: 0 
       bus info: scsi@0:0.0.0 
       logical name: /dev/sda 
       version: 3.04 
       serial: 3JX0PFWA 
       size: 37GiB (40GB) 
       capabilities: partitioned partitioned:dos 
       configuration: ansiversion=5 signature=0009919b 
  *-cdrom:0 
       description: CD-R/CD-RW writer 
       product: CD-Writer+ 9500b 
       vendor: HP 
       physical id: 1 
       bus info: scsi@1:0.0.0 
       logical name: /dev/cdrom 
       logical name: /dev/scd0 
       logical name: /dev/sr0 
       version: 1.06 
       serial: [HP      CD-Writer+ 9500b1.06KRBF071 
       capabilities: removable audio cd-r cd-rw 
       configuration: ansiversion=5 status=open 
  *-cdrom:1 
       description: DVD-RAM writer 
       product: DRW-1814BL 
       vendor: ASUS 
       physical id: 0.1.0 
       bus info: scsi@1:0.1.0 
       logical name: /dev/cdrom1 
       logical name: /dev/dvd1 
       logical name: /dev/scd1 
       logical name: /dev/sr1 
       version: 1.10 
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram 
       configuration: ansiversion=5 status=open 
The obvious differences are as mentioned namely that the HP Drive is not a DVD Drive.
Should I attempt some fix or fit another DVD Drive which I have been considering and can easily do.
Thanks.

---

### Post by bigal1932flying on 2009-02-02
Tried putting a DVD in the DVD Drive in xubuntu and received this message:
Failed to mount "DVD-ROM Disc"
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so.

Is this any help in solving this problem?

---

### Post by bigal1932flying on 2009-02-13
Took the plunge and fitted a new DVD Drive. When I put a DVD in it comes up with the message "Cannot mount volume. Invalid mount option when attempting to mount the volume"
Output from the command "sudo lshw -C disk" for the two DVD Drives is now:
 *-cdrom:0
       description: DVD-RAM writer
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=ready
  *-cdrom:1
       description: SCSI CD-ROM
       product: DRW-1814BL
       vendor: ASUS
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.10
       capabilities: removable audio
       configuration: ansiversion=5 status=nodisc
Any ideas what I should do next?

---

### Post by bigal1932flying on 2009-05-02
A recent upgrade to Jaunty seems to have fixed my DVD Drive problems.

---

