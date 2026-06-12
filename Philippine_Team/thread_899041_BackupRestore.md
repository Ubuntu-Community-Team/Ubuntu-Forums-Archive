---
title: "Backup/Restore"
date: 2008-08-23
forum: Philippine Team
---

### Post by initial_m on 2008-08-23
Any ideas on how to backup/restore my system, or any apps that i can used to do it? So that when prob/issues arises, I can just restore my current desktop..

---

### Post by pendletone on 2008-08-24
If you're comfortable with the terminal and don't want to install anything, you can use the [TAR trick]("https://help.ubuntu.com/community/BackupYourSystem/TAR").

However, I do recommend sbackup for simple automated backups:

```
sudo apt-get install sbackup
```

Follow this guide on how to configure it: [Backup and Restore Your Ubuntu System using Sbackup]("http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html")

---

### Post by xrmuser on 2008-09-28
May be this program will help you to backup your desktop.

You can also use hubackup:

Concise and easy to use backup application for the desktop user
HUBackup is short for Home User Backup System. As the name implies, this is a very simple, concise and easy to use backup application that uses the renowned and proven dar (Disk ARchive) to do the actual archiving. Emphasis has been on providing true and reliable progress indication throughout all operations, as well as the ability to cancel any operation at any given point. HUBackup mainly concerns with backing up your home folder data, allowing you to restore it in case of data loss.

You can install it by:
1. Login to your desktop

2. Click Applications, then point to Accessories. Click Terminal.

3. Type the command below.

[I]sudo apt-get install hubackup
[/I]
and then press enter.

NOTE: Make sure you are online (connected to the Internet) before running the command.

4. After it is successfully installed, to start the program.

Click System menu, then point to Administration and then select Home User Backup.

---

