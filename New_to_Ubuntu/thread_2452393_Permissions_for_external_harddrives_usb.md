---
title: "Permissions for external harddrives usb"
date: 2020-10-21
forum: New to Ubuntu
---

### Post by alphardvb on 2020-10-21
Goodafternoon, 

I have a question: see the image. What do I do wrong?? [ATTACH=CONFIG]287198[/ATTACH]

i just cant understand why those permissions are different from eachother. The only difference there is is that the drive Series is a network drive from my windows machine (also an external harddrive). Kids and MM are 2 drives whom are connected to the raspi directly. 

i hope you guys can help me. And after that I might have another issue, the GPT table is corrupt. :)

with kind regards (and I hope tou understand what Ive typed in my “Louis van Gaal English”),

alphard

---

### Post by Impavidus on 2020-10-21
It depends on how you mount them and what filesystems they use. I'm not so familiar with network drives from Windows. Can you tell us?

It's easier if you simply copy the text from your terminal to the forum.

---

### Post by TheFu on 2020-10-21
First things first, please post using text, not images.  I can't copy/paste parts of images to ask more questions, get clarification.  Any terminal program you are using supports copying the text.  Please and thank you.

Ok, next learn and understand Unix permissions.  777 permissions are for people who don't care about security or who are extremely lazy.  File and directory permissions are the core for all Unix security, so 777 is effectively no permissions controls at all. all processes on the device can read and write, and delete and move any of those files. That is seldom a good idea and almost always a really bad idea.

Unix permissions are tied to the file system.  In Windows, there are basically 3 file systems These do not support Unix permissions. They are FAT32, exFAT, and NTFS.  None of them support normal Unix owner, group, and permissions commands. Those Unix commands are chown, chgrp, chmod.  The only way to force permissions for FAT32, exFAT, and NTFS is using a hack with the mount options. This is a poor substitute for real Unix permission controls.  On Linux, mounting storage with any of those file systems will be slow without some extra options anyways, so it isn't too unreasonable to add the owner, group, and default permissions for files and directories to be used.  Using any GUI to mount non-Linux file systems will be slower than using either a real **mount** command or setting things up in the /etc/fstab.  Mounting Unix file systems though a GUI does not cause performance or permmisson problems. but using the fstab is more secure. 

Sometimes we don't have any choice but to use non-Linux file systems due to hardware limitations. I have a video recording device which only supports NTFS or FAT32, nothing else. It is a pain to use under Linux, but I pull all the files off it ASAP.

With that said, all storage can be formatted to use a Linux file systems.  For flash devices, f2fs is the fastest, best, choice for Linux-only use.  f2fs keeps the write counts down and performs really great, even beating ext4 for typical workloads.  
For non-flash storage, ext4 is usually the best, all-around, choice. For really large HDDs, ext4 is all I use.  
Plus, all native Linux file systems support the full Unix permissions model.

So, the first choice is to decide the file system to be used. That would determine the mount options needed.

As for permissions, Ubuntu has a tutorial: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)  There are many different modes and we can show you how to allow different users to have whatever access is needed for each, without using 777 permissions. We can setup the directories to make it so you and others don't need to deal with permissions in any subdirectories again too. It is a 1-time thing.

For ext4, mounting is pretty easy.  A line like this in the /etc/fstab:
```
UUID=2471d686-fde5-4680-5544-46c99c8a5550      /media/D1     ext4    noauto,users,noatime,errors=remount-ro     0     1
```
The fstab manpage has more details about what each field means.  1 or more spaces separates the fields.  The "noauto,users,noatime,errors=remount-ro" is a single "option". No spaces are allowed anywhere in that option.  To edit the fstab, use **sudoedit /etc/fstab**  That's the safest way to edit 99.9999% of system config files.
The UUID for your file system will be different.

If the USB drive ad partitions use non-Linux file system, we need to know which it is. This command, run when it is mounted, will show that:
```
df -Th
```

This applies to locally connected disks or those connected using the NFS protocol.
For samba/cifs connections to Windows storage, the rules are different.

---

### Post by TheFu on 2020-10-21
Network file systems and permissions are controlled by the server of the storage.  What server and how is it being mounted?

---

