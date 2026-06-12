---
title: "another invalid mount option sdhc"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by aspergerian on 2008-08-23
My sdhc mounted properly in Asus "Xandros" but doesn't mount in 8.04.1 but can be manually mounted from terminal after which can be read evenas the sdhc then has write errors (or write-message errors).  I've read many threads with "invalid mount option" discussed. One discussion provided a line akin to what my Asus 901 with 8.04.1 states.

My 901# /etc/fstab: static file system information.
/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

= = = =

Here's a clue from another thread regarding a usb drive:
[http://ubuntuforums.org/showthread.php?t=846283&highlight=invalid+mount+option](http://ubuntuforums.org/showthread.php?t=846283&highlight=invalid+mount+option)

Command "cat /etc/fstab" generated
/dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
which received the following critique:

"It is wrong because your usb key is device /dev/sdb1, not your cdrom. (It is not the mount point that is making this fail, it is the filetype: the usb key is not iso9660, it is W95 FAT16.
   from:
[http://ubuntuforums.org/showthread.php?t=846283&highlight=invalid+mount+option&page=3](http://ubuntuforums.org/showthread.php?t=846283&highlight=invalid+mount+option&page=3)

====

That thread is marked "Solved" and was for a usb flash drive, but the line is very similar to what fstab presents for my sdhc (16gig, ext3).

Fstab in my 901 presents:
/dev/sdc1  /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
In the other thread, fstab had presented:
/dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

Given that my sdhc is labeled sdc1, ought I write something ese in place of /media/cdrom0   udf,iso9660
???

The usb in the quote thread was labeled as W95 FAT16. Is there a way to learn the similar but probably non-identical label for my sdhc which is sdc1.

Perhaps someone knows a more direct way? Or can answer the questions. Guidance appreciated!

---

### Post by aspergerian on 2008-08-23
I've found a solution to the "invalid mount option" that kept occurring in my Asus 901. 


sudo gedit /etc/fstab
remove the line (probably at the bottom) that is for the cd drive.
save and close
reboot 

My 901 had labeled my sdhc as cdrom0. I deleted the following line:
/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
Saved the file and rebooted.

My sdhc as sdc1 is booted and is now functional. 

The solution was provided by flexgrip, posting into a 901 Asus forum
[http://forum.eeeuser.com/viewtopic.php?id=34280](http://forum.eeeuser.com/viewtopic.php?id=34280)

My sdhc is left in the 901 "permanently", even when not mounting properly. My usb flash drive was also not mounted during that time period, but after the above-described solution was enacted, my sdhc mounted correctly during boot and my usb flash drive mounted properly.

---

