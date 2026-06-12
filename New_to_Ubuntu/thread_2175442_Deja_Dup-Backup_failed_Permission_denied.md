---
title: "Deja Dup-Backup failed: Permission denied"
date: 2013-09-19
forum: New to Ubuntu
---

### Post by neelson2 on 2013-09-19
I use 13.04 and can't get Deja Dup to backup my home folder to an external drive. I tried ntfs and ext2,3,4 as fileformats with several permission settings, but it is always denied ("Cannot create folder, permission denied").
The deja dup process seems to run under my user name rights.
Any suggestions?

---

### Post by mastablasta on 2013-09-19
what kind of rights are set on external hard drive?

if it's NTFS it shouldn't give problems. unless it is mounted as read only or something.

another option is mint backup tool ([http://community.linuxmint.com/software/view/mintbackup](http://community.linuxmint.com/software/view/mintbackup)). it has two buttons one for backing up software selection and the other one for home folder (data). or that you clone the whole disk using redo backup or clonezilla.

or you can just compress the home folder to external disk :-)

---

### Post by neelson2 on 2013-09-25
Thanks for the suggestions.

Deja-Dup suddenly worked, when i  formatted to NTFS, created the "backup" folder manually and started it  3x times from the commandline with "gksu deja-dup --backup". Now it  backups normally without the commandline.

---

