---
title: "[SOLVED] FIle system check failed at boot time - exit status 4"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by m10 on 2008-09-20
When booting my laptop - ubuntu 8.04 - the routine check starts but when at 70% it stops with an error.
```
File system check failed
A log is being saved at /var/log/fsck/checkfs if that location is writable
Please repair the file system manually
A mantenance shell will now be started
[..]
```

i do not know what to do on that maintenance shell and booted with ctrl+d(wich it said to press to do that:P)

this is my /var/log/fsck/checkfs:
```
Log of fsck -C3 -R -A -a 
Sat Sep 20 14:09:40 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sda6: clean, 57/108544 files, 115002/433720 blocks
/dev/sda8 contains a file system with errors, check forced.
/dev/sda8: Duplicate or bad block in use!
/dev/sda8: Multiply-claimed block(s) in inode 2162697: 4348420 4348421 4348546 4348595
/dev/sda8: Multiply-claimed block(s) in inode 2162819: 4348421 4348595
/dev/sda8: Multiply-claimed block(s) in inode 2162939: 4362944 4362965
/dev/sda8: Multiply-claimed block(s) in inode 2163068: 4362965
/dev/sda8: Multiply-claimed block(s) in inode 2169271: 4362944
/dev/sda8: Multiply-claimed block(s) in inode 2169368: 4362945
/dev/sda8: Multiply-claimed block(s) in inode 2169830: 4348420
/dev/sda8: Multiply-claimed block(s) in inode 2169835: 4363003
/dev/sda8: Multiply-claimed block(s) in inode 2169843: 4362945
/dev/sda8: Multiply-claimed block(s) in inode 2169844: 4363004
/dev/sda8: Multiply-claimed block(s) in inode 2169851: 4348546
/dev/sda8: Multiply-claimed block(s) in inode 2169890: 4363003 4363004
/dev/sda8: (There are 12 inodes containing multiply-claimed blocks.)

/dev/sda8: File /mio/.mozilla/firefox/e62jeq9s.default/bookmarkbackups/bookmarks-2008-09-12.json (inode #2162697, mod time Fri Aug  8 02:34:47 2008) 
  has 4 multiply-claimed block(s), shared with 3 file(s):
/dev/sda8: 	/mio/.mozilla/firefox/e62jeq9s.default/bookmarkbackups/bookmarks-2008-09-16.json (inode #2162819, mod time Tue Sep 16 19:22:16 2008)
/dev/sda8: 	/mio/.purple/status.xml (inode #2169851, mod time Fri Sep 19 20:39:30 2008)
/dev/sda8: 	/mio/.gconfd/saved_state (inode #2169830, mod time Fri Sep 19 23:00:46 2008)
/dev/sda8: 

/dev/sda8: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
/dev/sda7: clean, 38/537504 files, 51794/1074339 blocks
fsck died with exit status 4

Sat Sep 20 14:18:08 2008
----------------
```

this is my /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2e7b2bed-c87c-48fb-83bc-0dda9b42410f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=c71ed6d0-da29-4f74-9674-e3d99c294afa /boot           ext3    relatime        0       2
# /dev/sda9
UUID=621d8983-2081-4d58-971f-a6a5461cd714 /home           ext3    relatime        0       2
# /dev/sda8
UUID=fc8e60e8-c66f-4cf0-8676-5ef87091b766 /tmp            ext3    relatime        0       2
# /dev/sda7
UUID=e8bcc8d1-ce85-4556-82dc-e3a6d647b3a4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#sdcardreader edited by hand
/dev/mmcblk0p1 /media/sdcard vfat defaults,noauto,user 0 0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

```

when i try to run fsck in a terminal i get:
```
:~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=2e7b2bed-c87c-48fb-83bc-0dda9b42410f'
```

help is appreciated. i thanck u in advance

note: i did neither edit my partitions nor reformatted them nor anything else in that direction

---

### Post by cmnorton on 2008-09-20
Boot with a rescue CD of some kind (Ubuntu Live, Knoppix, etc).

See if you can even mount this file system.

If you can, try to backup the data on the mounted volume somewhere.

Then, unmount the file system and recover the file system using fsck.

Depending on the output of fsck, you can make a decision as to whether you need to replace the drive or re-create the file system. 

Assuming this is a smart enabled drive, have you seen any smartd errors on boot? 

Usually the disk manufacturer will supply you with a floppy or CD based boot disk with drive diagnostic. You also might try that.

You might want to have a look at this link, too:

[http://ubuntuforums.org/showthread.php?t=674409](http://ubuntuforums.org/showthread.php?t=674409)

---

### Post by m10 on 2008-09-21
Thank You that worked! and the linked post was instructive too:)

---

