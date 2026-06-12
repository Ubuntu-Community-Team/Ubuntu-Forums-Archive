---
title: "Issue with writing to the disk"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by civic_si on 2008-05-21
The other day I booted my 7.10 box and it started acting weird. I have not run any updates on in a while as it has not been used. I am having an issue with it writing files to the disk. I tried to run updates and it worked for some and then said it cant write to the file system. I rebooted into recovery mode and unmounted the drive and ran fsck -vfc on it and it came up with no errors. I also went into fstab and took out the NTFS drives that I had loading.

Anybody have any ideas on what could be the issue? I have not ran across this before.

---

### Post by civic_si on 2008-05-21
This machine is setup to dual boot and XP works fine.

I booted back into Ubuntu and it hung after the desktop loaded so I hit ctrl alt bkspce and it says 

scsi 0:0:1:0 rejecting I/O to dead device
EXT3-fs error (device sdb2): ext3_find_entry: reading directory #
6001774 offset 0

sdb2 is the hdd that linux is installed on sda3 is my swap partition.

---

### Post by civic_si on 2008-05-21
I need some advice, I cant stand Windows and I want to play ETQW need my Linux back. :(

---

### Post by civic_si on 2008-05-22
anybody?

---

