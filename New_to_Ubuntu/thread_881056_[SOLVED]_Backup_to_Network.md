---
title: "[SOLVED] Backup to Network"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by SBFree on 2008-08-05
Hi - Complete newb here, just into my install a few days. I would really like a backup I can restore that would let me have the packages I've installed and my wireless network working as part of the restore. These things take a newb forever. I've been used to disk images in the Windows world with a 10 minute restore to a new drive to get up and running to the point where the back up was made. Sorry for the long intro. I've installed SBACKUP which allows backups to go to a remote directory. This is what I would like to do but I can't seem to get the backups to go there even when I select this. They keep going to the default '/var/backup'. I selected the 'Use remote directory choice and entered "smb://htpc-wmce/backuplapalpha/" and sbackup indicates this is an acceptable directory ( it has a "test" option ). If I open "smb://htpc-wmce/backuplapalpha/" with the Places menu at the top I see the files that are there and can write files to that directory. I installed the SAMBA package but it doesn't appear realavent. It seems to allow me to share local files to others on my network. Displaying the 'about' info for SBACKUP relates that it is "Simple Backup Suite 0.10.4" if that helps.
Thanks in advance - Scott

---

### Post by ktrnka on 2008-08-05
Are you doing a remote backup to a Samba Server? Are you connecting with a username and password?

---

### Post by Qchan on 2008-08-05
> **SBFree said:**
> Hi - Complete newb here, just into my install a few days. I would really like a backup I can restore that would let me have the packages I've installed and my wireless network working as part of the restore. These things take a newb forever. I've been used to disk images in the Windows world with a 10 minute restore to a new drive to get up and running to the point where the back up was made. Sorry for the long intro. I've installed SBACKUP which allows backups to go to a remote directory. This is what I would like to do but I can't seem to get the backups to go there even when I select this. They keep going to the default '/var/backup'. I selected the 'Use remote directory choice and entered "smb://htpc-wmce/backuplapalpha/" and sbackup indicates this is an acceptable directory ( it has a "test" option ). If I open "smb://htpc-wmce/backuplapalpha/" with the Places menu at the top I see the files that are there and can write files to that directory. I installed the SAMBA package but it doesn't appear realavent. It seems to allow me to share local files to others on my network. Displaying the 'about' info for SBACKUP relates that it is "Simple Backup Suite 0.10.4" if that helps.
Thanks in advance - Scott

[b][color=darkred]
Here ya go!

[http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html](http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html)
[/b][/color]

---

### Post by ktrnka on 2008-08-05
Try this in the SBackup remote directory setup:

```
smb://username:password@htpc-wmce/backuplapalpha/
```

---

### Post by SBFree on 2008-08-05
> **ktrnka said:**
> Are you doing a remote backup to a Samba Server? Are you connecting with a username and password?

I am trying to backup to a shared folder on a Windows Media Center Machine. It doesn't need a password or ask for a user name. I can access the folder from Nautilus and seem to have permission to write & delete files across the network.

---

### Post by ktrnka on 2008-08-05
After you clicked "test" after smb://host/sharedfolder and it says it looks ok you need to make sure to click SAVE before you click backup. If that still doesn't work, add another folder inside the shared folder and give everyone FULL read and write access and specify it in the config like so

smb://host/sharedfolder/newBackupFolder

I finally got it to work for me doing those steps above. Let me know if you still need help.

---

### Post by ritterm on 2008-12-31
> **ktrnka said:**
> After you clicked "test" after smb://host/sharedfolder and it says it looks ok you need to make sure to click SAVE before you click backup. If that still doesn't work, add another folder inside the shared folder and give everyone FULL read and write access and specify it in the config like so

smb://host/sharedfolder/newBackupFolder

I'm also new to Linux and have been trying to backup to a network drive using sbackup.  This thread, particularly ktrnka's last post, solved my problem.  I'd gotten just far enough to know how to spell "samba" - the path format is exactly what I needed.  Thanks! :D

---

