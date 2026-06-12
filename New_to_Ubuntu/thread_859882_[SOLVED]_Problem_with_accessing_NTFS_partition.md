---
title: "[SOLVED] Problem with accessing NTFS partition"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Drenhead on 2008-07-15
I have an NTFS partition on a second hard drive that allows me to see it, but it won't allow me to move files to it.  Here is the fdisk:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1912    15358108+  83  Linux
/dev/sdb2            1913       14424   100502640    7  HPFS/NTFS
/dev/sdb3           14425       14946     4192965   82  Linux swap/Solaris

Here is my fstab entry for this:

/dev/sdb2 /media/share	ntfs ro,auto,user	0	0

I am trying to move files to /media/share/ but it gives me the following error:

The Destination is read-only.

When I look at the permissions on the directory, it looks like this:

drwxrwxrwx 1 root root 4096 2008-07-13 21:24 share

So, it looks to me like everything is open, but it won't let me move anything to it.

What am I doing wrong?

---

### Post by logos34 on 2008-07-15
you need to reconfigure fstab so it mounts rw (read-write access)

this should fix it:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Inxsible on 2008-07-15
> **Drenhead said:**
> I have an NTFS partition on a second hard drive that allows me to see it, but it won't allow me to move files to it.  Here is the fdisk:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1912    15358108+  83  Linux
/dev/sdb2            1913       14424   100502640    7  HPFS/NTFS
/dev/sdb3           14425       14946     4192965   82  Linux swap/Solaris

Here is my fstab entry for this:

/dev/sdb2 /media/share	ntfs ro,auto,user	0	0

I am trying to move files to /media/share/ but it gives me the following error:

The Destination is read-only.

When I look at the permissions on the directory, it looks like this:

drwxrwxrwx 1 root root 4096 2008-07-13 21:24 share

So, it looks to me like everything is open, but it won't let me move anything to it.

What am I doing wrong?You mounted it as root..so its owned by root. So you - the USER- cannot write to it.

you can assume ownership by using the following command```
sudo chown -R *your-username*:*your-username* /path/to/mount/point
```

---

### Post by weirdfox on 2008-07-15
The basic ntfs driver does not support file writing, you must use ntfs-3g.

```
sudo apt-get install ntfs-3g
```

then for your fstab:

/dev/sdb2 /media/share ntfs ro,auto,user 0 0
```
/dev/sdb2   /media/share      ntfs-3g   rw,users,gid=user,dmask=002,fmask=133,nls=utf8 	0 	0
```

Have fun !

---

### Post by Drenhead on 2008-07-15
Thanks for your help.  I used the ntfs-config tool and it appears to be working now.

---

### Post by logos34 on 2008-07-15
>thread tools>mark as 'solved'

enjoy

---

