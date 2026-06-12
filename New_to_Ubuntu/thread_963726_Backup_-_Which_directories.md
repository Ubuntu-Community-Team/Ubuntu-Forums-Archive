---
title: "Backup - Which directories?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by technosinner on 2008-10-30
Hi again,

Simple question: I want to set up backups on my server.  Which directories should I dump?  I'm talking about a system backup and not anything to do with files or data; I just want to be able to restore my system if I do something stupid, shich is likely to happen ;)

I have the backup system all set up, I just need to know the directories... I've looked it up and it seems I don't get the same info everywhere.  I'm thinking /bin /sbin and /usr, but I don't want to forget anything, all the while not getting too big of backup files.

Thanks
ts

---

### Post by Idefix82 on 2008-10-30
I would certainly backup /etc which contains system wide configuration files, and /boot in case you mess up really badly.

---

### Post by Het Irv on 2008-10-30
If you have the room, I would suggest backing up everything but /home, /media, and /mnt.  That should cover all system files.
But I am not a backup genius by any means, so don't just look at my post.

---

### Post by cdtech on 2008-10-30
I run a regular backup of my server using two files:
**do-backup -**
/boot
/etc
/home
/root
/usr/local
/var
/downloads
/scripts
**dont-backup -**
*.mp3
*.mpg
*.avi
*.wav
*.mov
*.asf
*.rm
*.iso
*.flac
*.zip
*.exe
data.bin
/usr/local/games
/var/cache/apt/archives
/mnt
/backup
/dev
/var/lock
/var/run
/var/tmp
/tmp
/cdrom
And I also copy my installed packages using -
dpkg --get-selections > ${backuppart}/${current}/selections

But thats just my backup scheme, yours may differ.
Hope this helps........

---

### Post by Idefix82 on 2008-10-30
> **Het Irv said:**
> If you have the room, I would suggest backing up everything but /home, /media, and /mnt.  That should cover all system files.

Certainly no need to backup /proc and /sys.

---

### Post by technosinner on 2008-11-01
Thank you all, I should be able to get it working!

---

