---
title: "Cant Mount Maxtor NTFS Portable Drive"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by mikeody on 2008-06-21
Am trying to transfer data from XP PC to Ubuntu via a Maxtor Portable Drive [NTFS].
I get the message that the drive cannot be mounted and a suggestion that I 'add the following to the 'relevant row' of /etc/fstab'.

/dev/sdb1 /media/MAXTOR DRIVE ntfs-3g force 0 0

I understand the issue but unfortunately the message doesnt say exactly where in /etc/fstab that the additional line be added [or inserted].
If I add the line at the bottom of /etc/fstab I get a 'bad line in fstab' message.
Can someone help please ?
Keep things simple though - am strong on XP but am very new to Ubuntu.
Thanks.

---

### Post by hovzio on 2008-06-21
Have you tried "saftley removing" from windows. This is important for otherwise ubuntu cannot mount the drive because it hasnt been shut down properly. For an external drive you don't usually need to put any entries in fstab.

---

### Post by mikeody on 2008-06-22
Thanks for that but fr some reason its NOT showing up in the Windows taskbar so I cant 'safely' remove it.
Works fine in Windows though but there just doesnt seem to be any way to unmount the drive.

---

