---
title: "Why does backup name keep incrementing:  backup, backup1, backup2, etc?"
date: 2018-01-12
forum: New to Ubuntu
---

### Post by sterator on 2018-01-12
I distinctly remember naming my backup a certain name. for some reason its name is incrementing upward, and I don't know why. It causes a problem with rsync because my command will use "backupname" but the actual backup location has been changed to "backupname1" and then to "backupname2"

I don't understand what's causing this to happen. Can someone share some wisdom about this?

My workaround for rsync is to view properties on the backup volume to see what the current name is, then change my rsync command accordingly.

Thank you!

---

### Post by litlesam on 2018-01-12
Instead of writing over the first file "backupname" it will add a 1 to the file name, then 2 and so on. The latest file is the one with the highest number.

You can rename "backupname" to "backupname1" which would leave your "backupname" free again before running your backup and the others would then be backups of "backupname".

---

### Post by Dennis N on 2018-01-13
Not possible to tell without more information on your procedure, but it could be you are using a USB device named 'backup' for backup, and mounting it automatically by plugging it in. Plugging it in automatically will create a new mount point of /media/<user>/backup. Unmounting it removes that mount point, and when you plug it in again the OS recreates that mount folder.

But if your usb device isn't being unmounted properly, the mount folder isn't removed. Plug it in next time and the folder the OS would normally create already exists, so in that case system policy is to make a new mount folder with '1' added to the device name, giving you /media/<user>/backup1. If backup1 also exists, it tries backup2 for the name, and so on.

---

