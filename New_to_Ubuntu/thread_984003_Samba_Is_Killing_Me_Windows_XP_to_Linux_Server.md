---
title: "Samba Is Killing Me: Windows XP to Linux Server"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by tdrusk on 2008-11-16
I have Samba running. I can see the files in XP and can read and execute them. I can't write to the drive though... When I try to I get the error attached.

I have tried so many combinations of chmod. 
I did
```
chmod 777 /media/sda1
```
and it looks to have worked, but it doesn't. I have added the user to the folder(it wouldn't work this well without it).

Any clue what I'm doing wrong?

---

### Post by mike2357 on 2008-11-16
Do you have Linux and Windows running on different machines, or is it one machine that can be booted into either operating system?

Also, please post the lines from /etc/fstab that contain references to /media/sda1.

---

### Post by tdrusk on 2008-11-16
> **mike2357 said:**
> Do you have Linux and Windows running on different machines, or is it one machine that can be booted into either operating system?

Also, please post the lines from /etc/fstab that contain references to /media/sda1.

They are two different machines.

This is the fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
**/dev/sda1       /media/sda1     ext3    rw,user,auto 0 0**


```

Should I throw in an "all" under /dev/sda1 options?
Is it because it's ext3?

EDIT: I found a problem. I can rwx /media/sda1 but I can't rwx in any of the directories of /media/sda1.
EDIT2: I figured it out. I ran
```
chown -R username /media/sda1 
```

---

### Post by mike2357 on 2008-11-16
I'm sorry to be so slow on the uptake, but I want to make sure I understand what you want to do, as the solutions are very different.  If I understand it, you want to run Windows XP and from it, read/write files on your Linux box.  Right?  Or do I have it backwards?  I guess I'm confused because Samba is used for making your Linux files available on Windows, but /media/sda1 is generally used for making Linux able to see Windows files on the same, dual-boot machine.

---

### Post by tdrusk on 2008-11-16
> **mike2357 said:**
> I'm sorry to be so slow on the uptake, but I want to make sure I understand what you want to do, as the solutions are very different.  If I understand it, you want to run Windows XP and from it, read/write files on your Linux box.  Right?  Or do I have it backwards?  I guess I'm confused because Samba is used for making your Linux files available on Windows, but /media/sda1 is generally used for making Linux able to see Windows files on the same, dual-boot machine.

I have a Linux server I want to access with my XP installation.

I figured it out though. I had to chown all the children of /dev/sda1. Works now.

---

