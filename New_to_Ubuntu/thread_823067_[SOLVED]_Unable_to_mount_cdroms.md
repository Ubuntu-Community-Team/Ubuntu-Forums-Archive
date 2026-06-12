---
title: "[SOLVED] Unable to mount cdroms"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Trzone on 2008-06-08
I am using Hardy Heron (8.04).  Whenever i put a cd into my cd-rom drive, it says that it is unable to mount because only a superuser can use mount.  If anyone can offer any insight into this, it would be much appreciated.

---

### Post by unutbu on 2008-06-08
There is a way to make cdroms mountable by any user.
Please post 

```
cat /etc/fstab
```

---

### Post by Trzone on 2008-06-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=2a8960fc-dc28-4513-8904-c7122b8b48ba /               xfs     relatime        0       1
# /dev/sda5
UUID=ab822fc1-2d8a-4c62-b76d-bf41b92f722c /boot           ext3    relatime        0       2
# /dev/sda7
UUID=f82490e1-c29f-4356-9034-b567a5e9cc40 /home           xfs     relatime        0       2
# /dev/sda1
UUID=4580f061-ac0b-4c36-b41b-c550578c1646 none            swap    sw              0       0
#/dev/sda3 ((windows))
UUID=239243FC41C4313B	/media/Xp	ntfs	defaults	0	0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
tmpfs		/tmp		tmpfs			defaults	0	0









That would be my /etc/fstab

---

### Post by 4ebees on 2008-06-08
> **Trzone said:**
> I am using Hardy Heron (8.04).  Whenever i put a cd into my cd-rom drive, it says that it is unable to mount because only a superuser can use mount.  If anyone can offer any insight into this, it would be much appreciated.

Very strange!

Go to the settings window 

if KDE, check 'system settings'

If GNOME, urm..similar, I think :)

Then select

Users and Groups 

and make sure you, as a user, are included in the CDROM group. If not, select 'Administrator  mode' and select CDROM from the possible groups/options and add it to yours.

This should fix the problem.

Otherwise, I'd follow the option being offered by unutbu.

HTH

Regards.

---

### Post by unutbu on 2008-06-08
Hm. Your fstab looks fine.
When you put a CD in the drive, are you typing the command 

```
mount /media/cdrom0
```

or is this an automatic pop-up window that is giving you the error? (And what is the exact wording of the error?)

---

### Post by Trzone on 2008-06-08
it is an automatic pop up window
it states :Unable to mount the volume
mount: must be superuser to use mount

---

### Post by Trzone on 2008-06-08
This is now fixed, it was Bastille!

---

### Post by unutbu on 2008-06-08
I'm glad you found the solution!

---

### Post by 4ebees on 2008-06-08
> **unutbu said:**
> I'm glad you found the solution!

I agree...well done.

Weird problem! :)

---

