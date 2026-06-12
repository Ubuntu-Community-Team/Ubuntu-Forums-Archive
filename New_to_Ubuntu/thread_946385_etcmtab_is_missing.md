---
title: "/etc/mtab is missing"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by bangmalley on 2008-10-13
When I plug in a USB drive, an error message came out 
```
mount : /etc/mtab is missing
```

When I check the /etc folder, I found that the mtab file has been changed to mtab.fuselock.

To test the file, I copy the file to /home, changed the permission to 777, and rename it to mtab. After open it using gedit, I found that the file is empty.

I fsck the disk, the disk is clean.

I heard that rescue-mode provided by the alternate CD can solve it.(Downloading it...)
Is there any other way?

Edit: Using live-cd now, cannot create /etc/mtab
Edit: I have no idea /etc/mtab can be renamed suddenly to /etc/mtab.fuselock and mess up everything.
Edit: I try to update to Intrepid, updating...
Edit: Tried Intrepid, worse, update error, corrupted filesystem :(

---

### Post by philinux on 2008-10-13
This is the content of mine.

Maybe it could be useful if you edited it with your partitions.

```
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
/dev/sda3 /home ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/philcb/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=philcb 0 0
```

---

### Post by bangmalley on 2008-10-13
But I cannot create /etc/mtab. I deleted the mtab.fuselock, same thing.
When I boot, I saw /etc/mtab~2395, I think that's the root of my problem, but i can't seem to find /etc/mtab~2395

The error message when I try to create /etc/mtab using gedit:
```
Unexpected error: File not found
```

Edit: i just saw boot error
```

cannot create lock file: /etc/mtab~2369

```

---

### Post by philinux on 2008-10-13
You may have a backup then.

Use 

```
gksudo nautilus
```
That will let you open system files and save them so be careful

You would need the following to edit individual files.

```
gksudo gedit /etc/mtab
```

---

### Post by ajgreeny on 2008-10-13
> But I cannot create /etc/mtab. I deleted the mtab.fuselock, same thing.If you are just getting a message saying permission refused or something similar, try using gedit as root with gksudo gedit and then add the text given by philinux but with the partition dev name to suit your system.  Now save it as /etc/mtab.  It should work.

---

### Post by ajgreeny on 2008-10-13
> But I cannot create /etc/mtab. I deleted the mtab.fuselock, same thing.If you are just getting a message saying permission refused or something similar, try using gedit as root with ```
gksudo gedit
``` and then add the text given by philinux but with the partition dev name to suit your system.  Now save it as /etc/mtab.  It should work.

---

### Post by bangmalley on 2008-10-14
but it did not work. running as root doesn't help.
```
Unexpected error: File not found
```

---

### Post by Elfy on 2008-10-14
Can you post both the command you are trying to use and the error - we can see if you're putting the command in properly.

---

### Post by bangmalley on 2008-10-14
from terminal
```
sudo gedit /etc/mtab
```
i even tried sudo sudo

sigh, I can't even create the /etc/mtab using live-cd.

---

### Post by bangmalley on 2008-10-14
OK, i got back the /etc/mtab after updating to Interpid and fsck the disk.
Thanx everyone.

---

