---
title: "How to Use Dropbox With Ubuntu 10.04 Simple Backup"
date: 2011-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by forliberty on 2011-05-10
I use Simple Backup on Ubuntu 10.04, with Dropbox as the backup destination. The backups go to the local Dropbox folder on my Ubuntu machine. But the backups do not get synced to the Dropbox "cloud" storage. When I go online to view my Dropbox account, it shows all the folders that are being created by Simple Backup for each backup, but the folders are all empty. 

I have discovered this is a permissions problem; Simple Backup runs as root by default, and the backup files are only accessible to the root user. Apparently Dropbox does not have root access, and thus does not see the backup files. 

The solution is as follows: 

Open a terminal session, and type:  sudo gedit /usr/sbin/sbackupd

On line 183 or 184 of the file, substitute "admin" instead of "root". The original line looks like this: 

os.setgid( grp.getgrnam("root").gr_gid )

After changing it, it will look like this: 

os.setgid( grp.getgrnam("admin").gr_gid )

After making the change, using Simple Backup with Dropbox works perfectly. An added bonus of this change is that you need not log in as root to restore or view your backups.

---

