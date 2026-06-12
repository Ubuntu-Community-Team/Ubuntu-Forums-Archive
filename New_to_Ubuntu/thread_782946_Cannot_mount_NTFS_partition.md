---
title: "Cannot mount NTFS partition"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by ebeckhusen on 2008-05-05
I was messing with something, trying to get my Windows partition to auto mount.  There was a properties box that I opened and one of the pages had a box to enter a mount point.  I entered /media/disk, and apparently there is no such directory.  Now I cannot get my Windows partition to mount at all.

I get the message "mount_point cannot contain the characters newline, G_DIR_Separator"

What did I do, and how do I fix it?  Please use simple language as I'm still pretty new at this.

---

### Post by bumanie on 2008-05-05
Paste the output of > cat /etc/fstab. i'm not usre what you did before though. Mounting issues are usually solved by editing /etc/fstab.

---

### Post by ebeckhusen on 2008-05-05
Ok, here's what I get from "cat /etc/fstab"
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=681b134a-c23c-4c57-98f0-134001ddf7be /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=136d3682-d30f-49ef-a4c9-27c7b5337d86 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by ebeckhusen on 2008-05-05
Never mind, I fixed it.  For anyone else who might have this problem:

 > Re: usb drive won't mount after changing mount point
This post could be related to an Ubuntu bug filed at: [https://bugs.launchpad.net/ubuntu/+bug/107607](https://bugs.launchpad.net/ubuntu/+bug/107607)
----------------------------


Hi

To undo this, open ~/.gconf/system/storage/drives, remove the directory corresponding to the drive you saved an incorrect mount point for, then log out and log back in.

IMO this is a bug that it does not validate the user input as a valid mountpoint before saving the mountpoint. I just reported this.

Matthew

---

### Post by malathion on 2008-05-05
Thanks! Don't forget to mark your thread solved! :)

---

