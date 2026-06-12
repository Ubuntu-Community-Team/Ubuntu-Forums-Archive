---
title: "Help setting permissions on mount"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by AlwaysBreaking on 2008-11-09
I'm added a second hard drive following the instructions in [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) but I don't have permission to add files. 

I want to share the folder and read/write to it from my XP system, but right now I can't even write to it from ubuntu.  root is the owner and no one else has permission to do anything.

The drive mounts in /media/music01 on boot and is formatted fat32. I've tried chmod and chown, but get errors.

---

### Post by bumanie on 2008-11-10
Why not format it to ntfs and use ntfs-config to automount it a boot and it should then have permissions to read/write to from ubuntu and windows should like it being ntfs too.

---

### Post by gate on 2008-11-10
What you need to do is manipulate the file /etc/fstab it is what sets up the permissions for static drives. You need to add the drive in there if it isn't already, etc.

---

### Post by AlwaysBreaking on 2008-11-10
Thank you. I think it was probably the fstab file. I did reformat to NTFS and edited the fstab file, now it mounts and I have permission to add files. I still can't share it because root is the owner. Is there a way to share on boot? or do I have to use nautilus to create the share?

---

