---
title: "Permissions questions"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by kuproverto on 2008-09-27
Since asking questions in [this]("http://ubuntuforums.org/showthread.php?t=929121") thread I've figured out that to copy or create files in the new drive I have to use gksudo nautilus to become the root user temporarily. Is there some way I can permanently have these privileges when accessing this drive?

Also, how do I temporarily obtain root privileges to alter the /etc/fstab file so the drive will be mounted automatically?

---

### Post by terry_gardener on 2008-09-27
alter the fstab file you need root permissions. to obtain this use: 

sudo gedit /etc/fstab

---

### Post by amauk on 2008-09-27
to gain permission to write to the drive
edit the entry for the drive in /etc/fstab

add the 'user' option
this will allow reading & writing with normal user permissions

---

### Post by medic2000 on 2008-09-27
> **terry_gardener said:**
> alter the fstab file you need root permissions. to obtain this use: 

sudo gedit /etc/fstab

No! Dont use `sudo` with graphical programs like gedit. Use `gksudo` instead.

And for terminal programs use `sudo`

---

### Post by amauk on 2008-09-27
> **medic2000 said:**
> No! Dont use `sudo` with graphical programs like gedit. Use `gksudo` instead.

And for terminal programs use `sudo`

:confused:

there's no difference
gksu / gksudo are just gui wrappers around su / sudo

---

### Post by kuproverto on 2008-09-27
Thanks for the replies. A further question with regards to this answer:

> to gain permission to write to the drive
edit the entry for the drive in /etc/fstab

add the 'user' option
this will allow reading & writing with normal user permissions

my fstab file now looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1881a546-64d0-4c1d-b4a4-c960789a9cc4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f6e79a03-08ec-48d0-bd70-a74520d53b4e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1	/backup		auto	defaults,user	0	0
```

but I still can't create files or folders on the drive or move/copy them to the drive. The options are grayed out. What have I done incorrectly?

---

### Post by terry_gardener on 2008-09-27
i have found couple of sites that might help this issue.

[http://pennsylvania.ubuntuforums.com/showthread.php?t=283131](http://pennsylvania.ubuntuforums.com/showthread.php?t=283131)

and 

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

hope this helps

---

### Post by Xiong Chiamiov on 2008-09-27
> **amauk said:**
> :confused:

there's no difference
gksu / gksudo are just gui wrappers around su / sudo

They are wrappers that don't screw up your permissions.  For instance, after running dolphin through sudo, your bookmarks file (which gets saved automatically) is owned by root, which leads to a rather annoying error message every time you open it, until you fix the perms.

> **kuproverto said:**
> I still can't create files or folders on the drive or move/copy them to the drive. The options are grayed out. What have I done incorrectly?

Although you can add umasks and such to your fstab, it is much easier to directly alter the permissions on the drive.  If you have Nautilus opened as root, the you should be able to change them with the properties of the folder (not a gnome user, sorry), or you can change it with the terminal:
```

sudo chmod 775 /backup -R

```
or somesuch.

Notes on the above:
775 are permissions, with each digit being for root, users in the group, and others, respectively.  You can find out more [here]("http://www.ss64.com/bash/chmod.html").

-R is a recursive flag for chmod, which will apply those same permissions to all folders and files in /backup.

You may want to change the owner of the drive first, with chown:
```

chown yourusername:users /backup -R

```

---

