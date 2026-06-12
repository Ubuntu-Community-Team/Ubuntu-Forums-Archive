---
title: "BackupPC Xfer Fails"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by rkulp on 2008-05-14
:confused: I have installed BackupPC and successfully connected to a Windows XP computer, although with considerable difficulty. However, when trying to transfer files from the XP box, rsyncd almost immediately exits and gives the following in the BackupPC log:

008-05-14 09:21:20 full backup started for directory 
2008-05-14 09:21:20 Got fatal error during xfer (unexpected response: '@RSYNCD: EXIT')
2008-05-14 09:21:25 Backup aborted (unexpected response: '@RSYNCD: EXIT')

On the Windows side this appears to be immediately after the backup file list is requested.

I have searched for this error throughout the Ubuntu forums, Rsync documentation and the LinuxQuestions forum to no avail. I have tried every change in the conf files that I can think of. Any pointers as to how to find the problem would be greatly appreciated.

---

### Post by shifty_powers on 2008-05-14
[http://www.clonezilla.org/](http://www.clonezilla.org/)

a livecd backup distro, that will do a fill backup, (creata an image of your hd), and can do it over samba.

probably easier ;)

---

### Post by dlcobb on 2008-05-17
> **rkulp said:**
> :confused: I have installed BackupPC and successfully connected to a Windows XP computer, although with considerable difficulty. However, when trying to transfer files from the XP box, rsyncd almost immediately exits and gives the following in the BackupPC log:

008-05-14 09:21:20 full backup started for directory 
2008-05-14 09:21:20 Got fatal error during xfer (unexpected response: '@RSYNCD: EXIT')
2008-05-14 09:21:25 Backup aborted (unexpected response: '@RSYNCD: EXIT')

On the Windows side this appears to be immediately after the backup file list is requested.

I have searched for this error throughout the Ubuntu forums, Rsync documentation and the LinuxQuestions forum to no avail. I have tried every change in the conf files that I can think of. Any pointers as to how to find the problem would be greatly appreciated.
Are there any messages in the Rsyncd log or the Backuppc log?

---

### Post by watsbe on 2008-05-17
> **rkulp said:**
> :confused: I have installed BackupPC and successfully connected to a Windows XP computer, although with considerable difficulty. However, when trying to transfer files from the XP box, rsyncd almost immediately exits and gives the following in the BackupPC log:

008-05-14 09:21:20 full backup started for directory 
2008-05-14 09:21:20 Got fatal error during xfer (unexpected response: '@RSYNCD: EXIT')
2008-05-14 09:21:25 Backup aborted (unexpected response: '@RSYNCD: EXIT')

On the Windows side this appears to be immediately after the backup file list is requested.

I have searched for this error throughout the Ubuntu forums, Rsync documentation and the LinuxQuestions forum to no avail. I have tried every change in the conf files that I can think of. Any pointers as to how to find the problem would be greatly appreciated.
I think you should focus on the XP side.  The XP box will have a rsync.log or rsyncd.log in the directory where you installed rsyncd.  You may not be able to open it because it is in use.  Copy it and open the copy.  Note that it may contain passwords so don't post it on the internet without checking.  You may also like to check that the service is running in XP using control-panel, administrative tools, services.  The cgywin or rsync "readme" file also has some sample code to test rsyncd.  Unfortunately I'm not at that box at the moment so I can't tell you the exact names or paths.

---

### Post by Girya on 2008-05-19
Hey I've been playing around with backuppc and experiencing the same kind of frustrations. what really heped me was running the backup commands from a terminal on the server as user backuppc and adding a -**v argument **to the command. hope this helps. just guessing it's a connection problem or file permission problem. also the backuppc mailing list is a good start.

Can you run a rsync backup on the xp box with out backuppc?

---

