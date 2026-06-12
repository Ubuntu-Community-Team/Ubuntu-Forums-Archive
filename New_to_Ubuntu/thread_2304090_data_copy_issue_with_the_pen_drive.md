---
title: "data copy issue with the pen drive"
date: 2015-11-24
forum: New to Ubuntu
---

### Post by Praful_Itankar on 2015-11-24
HI everyone I am unable to copy data from hard disk of my desktop to pen drive but reverse is possible i am using ubuntu 13.10 i was tried with the different pen drive but it is not permiited to me to copy the data from hard disk to pen drive.no error message had been occur. please help me to troubleshoot this problem.

---

### Post by blade4 on 2015-11-24
It may be because the USB is being mounted as a read only drive. You will need to remount as read write. The link below will help : 

[http://askubuntu.com/questions/175739/how-do-i-remount-a-filesystem-as-read-write](http://askubuntu.com/questions/175739/how-do-i-remount-a-filesystem-as-read-write)

---

### Post by cmcanulty on 2015-11-24
did you try going to properties by right click of the drive and making sure the permissions are correct? If set to root then open file manager as root (in terminal gksu nautilus) and change the permissions to yourself as read  and write.

---

### Post by mcduck on 2015-11-24
What file system is the USB drive formatted in? If it's NTFS, and the drive was unplugged from a Windows machine without correctly removing it first, the filesystem would be marked as unclean, in which case Linux will automatically only mount it as read-only to prevent corruption or loss of data. In that case you should plug the drive back to a Windows machine and then remove it correctly, which will mark the filesystem as clean again.

---

### Post by LukeMorrison on 2015-11-24
The above solutions will most likely work, but you are running a non-supported version of *ubuntu.  The currently supported versions are 12.04, 14.04, 15.04 (two more months), 15.10.  I would highly suggest backing up your data and installing one of the above supported versions.

---

