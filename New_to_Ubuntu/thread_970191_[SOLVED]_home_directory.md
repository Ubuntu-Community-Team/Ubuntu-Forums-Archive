---
title: "[SOLVED] home directory"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by adsf on 2008-11-04
Hey Guys, 

I just updated my computer to 8.10.  Instead of updating I chose to reinstall.  My home folder is cept on a different participation.

i have gone into the setting and changed the home directory of my user to the second partition and everything seems to fine except I have to logn with a different user.  mount the other partition then relogin in with my user and then it works.

Suggestions?

---

### Post by em4r1z on 2008-11-04
Type "cat /etc/fstab" in a terminal and post the result.

---

### Post by adsf on 2008-11-04
here it is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=55a10946-2a51-40f5-82d6-0a043f7fa49d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=53941099-8d1a-47a0-a8b9-6e1d39c4430a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by em4r1z on 2008-11-04
Sorry for the delay, mate.

fstab shows the partitions mounted at start. As you can see, only Root, swap and CD-ROM are mounted but there are at least two more partitions (sda2 and sda3). You'll need to identify and add your Home partition to fstab. Type "sudo fdisk -l" in a terminal and post your results. This will show all the partitions running in all drives.

In the mean time, type "man fstab" in a terminal to familiarize with that file.

---

### Post by adsf on 2008-11-05
em4r1z thanks for the reply.  This was exactly the problem.  i used the following post to fix it 

[http://ubuntuforums.org/showthread.php?t=925021](http://ubuntuforums.org/showthread.php?t=925021)

---

### Post by harsh1kumar on 2008-11-05
If your problem is solved, please mark it solved.:)

---

