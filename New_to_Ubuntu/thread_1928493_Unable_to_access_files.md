---
title: "Unable to access files"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by les5335 on 2012-02-20
I'm a complete newbie with Ubuntu. I had a laptop running Ubuntu 11.10. I used a Paragon bootdisk to resize the partitions from 1 x 120Gb to 2 x 60Gb so I could install another operating system on the second partition. However after the resize my laptop wouldn't boot. No errors, just a black screen and restarting in a loop. I urgently need to get at some files in one particular folder! I attached the hard drive to another Ubuntu PC using an external USB-sata cable, then ran gparted/gpart. It shows the Ubuntu file system as /dev/sdb 1, with ext4 filesystem. Mount point is blank If I try to open or mount I got "error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb 1, missing codepage or helper program, or other error".
I looked in your forums and ran commands begining e2fsck and mke2fs but this seemd to do nothing. Now when open the Home folder and click on "63GB File system" nothing happens at all!. Is there any way to access my important files and copy them off? Thanks in advance.
 
Les

---

### Post by ajgreeny on 2012-02-20
Oh dear!

The **mke2fs** command you used is a "make new filesystem" or "format" command, telling the system to make a new ext partition on the space or partiton that you asked it to work on, so it is possible that you may have formatted over the existing OS on that disk.

Use a live CD or USB system, and run ```
sudo fdisk -l
```(lower case L at end) in terminal to see what partitions are on the disk at the moment, then use nautilus file manager on the live disk to navigate to the partition that you think is your old OS, and see if any files that you expect to see are there.  The partitions will probably be in /media/sdx#, or something similar.  Look in all the partitions if there are now more than one, just in case you have mixed up where things really are.

---

### Post by les5335 on 2012-02-20
Hi ajgreeney,
 
Many thanks for your reply. I ran sudo fdisk 'l (I have the hard drive on the external cable connected to another USb PC). It says /dev/sdb 1 is there containing a Linux file system. Gparted shows 27.88Gb used abd 30.92 Gb free, so the data is still there... unfortunately file manager can't see anything there. Groping blindly, I typed sudo mount /dev/sdb 1 abd got an error "mount point 1 does not exist". It seems to me that whatever the Ubuntu equivalent of the Windows file allocation table is damaged..?
Cheers, Les

---

### Post by ajgreeny on 2012-02-20
OK, just as a final check before I have to pass on to others, with the disk still attached (and hopefully still detected as sdb), but with the partition sdb1 unmounted, can you run ```
sudo e2fsck /dev/sdb1
``` and report any error messages that appear.

If that still does not work you may need to resort to using testdisk, which can repair corrupt partition tables.  However, that is about as far as I can go with testdisk so will need to let others take over.

---

