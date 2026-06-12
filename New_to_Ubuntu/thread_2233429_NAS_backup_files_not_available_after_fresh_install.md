---
title: "NAS backup files not available after fresh install Kubuntu 14.04"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by KEES01NED on 2014-07-08
Hello,

I have done the setup of the link below to backup files of my home  directory of my HP desktop with Kubuntu to a NAS hard drive. The NAS  hard drive is also used for backup of my windows Laptop manually. It  worked like a charme, every day an incremental backup was made on the  NAS.

[http://ubuntuforums.org/showthread.php?t=1471854](http://ubuntuforums.org/showthread.php?t=1471854)

For some reason I did install Kubuntu 14.04, it was a fresh install  covering the entire disk, actually overwriting the old version of  Kubuntu (not sure anymore i think 12.04). Before installing the new version I made an extra backup to  another hard disk (you never know what can go wrong).

Unfortunately I am not able to mount the drive correctly, at least I  think so. I am not a new-newby, but not everything is clear to me. I  tried the following command

sudo mount -t cifs //192.XXX.X.XX/Volume_1 /media/backups -o credentials=/etc/samba/user,sec=ntlmssp

that seems to be okay (no error message), but when I have a look at the  contents (via Dolphin, or the terminal) it shows me the windows files,:mad:. I am not interested in the windows files (work related) when I am working with Kubuntu (privat).

For the backup of Kubuntu files I use /media/backups as mount point and  /media/backups/current as directory where the files are stored. The  current directory isn't available anywhere.

How can I mount the NAS corectly showing the kubuntu files.

I did search on the internet but didn find a solution yet.

Regards Kees

---

