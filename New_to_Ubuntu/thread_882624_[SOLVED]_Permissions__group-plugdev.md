---
title: "[SOLVED] Permissions : group-plugdev"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by sharad.sharma on 2008-08-07
I have switched recently to Linux with Ubuntu 8.04(dual boot with WindowsXP)
To mount the FAT32 partitions when I boot into Ubuntu,I added appended the following to /etc/fstab :
```

/dev/sda1 /media/C vfat defaults,umask=002,gid=46
/dev/sda5 /media/D vfat defaults,umask=002,gid=46
/dev/sda6 /media/E vfat defaults,umask=002,gid=46
/dev/sda7 /media/F vfat defaults,umask=002,gid=46
```

When I right click the icon of the mounted drive on the desktop,I see that Permissions of "C" can't be determined.
When I check the permissions of directories media/X (eg /media/C) , the owner is root and group is plugdev with the permission to create and delete files while it is *Access Files* for Others.


Thanks
Are above permissions OK/safe?
What is plugdev ?

---

### Post by sharad.sharma on 2008-08-07
Please help

---

### Post by sisco311 on 2008-08-07
Yes it's safe. 

The first user created on the system is in the plugdev group.

check it:
```
id *username*
```

You can add/remove new users to/from the group:
```
sudo adduser *username* plugdev
sudo deluser *username* plugdev
```


In this way you can decide which user can write to the partition or
delete files from it.

---

### Post by sharad.sharma on 2008-08-07
OK..Thank you :)

---

### Post by sisco311 on 2008-08-08
If your thread is solved, please mark your thread solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

