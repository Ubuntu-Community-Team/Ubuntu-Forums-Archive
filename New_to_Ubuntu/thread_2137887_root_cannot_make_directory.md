---
title: "root cannot make directory"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by Morons on 2013-04-22
```
root@artemis:/var/www/clients/client27/web60# sudo mkdir vmfiles
mkdir: cannot create directory `vmfiles': Permission denied
```
```

root@artemis:/var/www/clients/client27/web60# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid
``````


root@artemis:/var/www/clients/client27/web60# ls -halF
total 72K
drwxr-xr-x 18 root root 4.0K Mar 25 00:30 ./
drwxr-xr-x  4 root root 4.0K Apr 22 13:01 ../
-rwxr-xr-x  1 root root    0 Apr 22 11:10 .bash_history*
drwx------  2 root root 4.0K Apr 22 11:10 .ssh/
drwxrwxrwx  2 root root 4.0K Mar 25 00:30 backup/
drwxrwxrwx  2 root root 4.0K Mar 18 14:43 bin/
drwxrwxrwx  2 root root 4.0K Mar 18 14:29 cgi-bin/
drwxrwxrwx  2 root root 4.0K Apr 22 13:05 dev/
drwxrwxrwx  6 root root 4.0K Mar 18 14:43 etc/
drwxrwxrwx  4 root root 4.0K Mar 18 14:43 home/
drwxrwxrwx  3 root root 4.0K Mar 18 14:43 lib/
lrwxrwxrwx  1 root root    4 Mar 18 14:43 lib64 -> /lib/
drwxrwxrwx  2 root root 4.0K Apr 22 11:46 log/
drwxrwxrwx  2 root root 4.0K Mar 18 14:29 private/
drwxrwxrwx  2 root root 4.0K Mar 18 14:29 ssl/
drwxrwxrwx  2 root root 4.0K Mar 18 14:29 tmp/
drwxrwxrwx  6 root root 4.0K Mar 18 14:43 usr/
drwxrwxrwx  3 root root 4.0K Mar 18 14:43 var/
drwxrwxrwx 18 root root 4.0K Apr 22 12:33 web/
drwxrwxrwx  2 root root 4.0K Mar 18 14:29 webdav/
```

As you see I already took ownership and chmod to 777 in order to force it !

In the previous directory I can safely make the directory no problem

Any Ideas?

---

### Post by prodigy_ on 2013-04-22
Sanity check: ```
cat /proc/mounts
lsattr -d /var/www/clients/client27/web60
```

---

### Post by Morons on 2013-04-22
```
root@artemis:/var/www/clients/client27/web63# cat /proc/mounts
rootfs / rootfs rw 0 0
/dev/root / ext3 rw,noatime,errors=remount-ro,barrier=0,data=writeback,jqfmt=vfsv0,usrjquota=aquota.user,grpjquota=aquota.group 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
/dev /dev devtmpfs rw,relatime,size=473808k,nr_inodes=118452,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
/dev/root /var/www/clients/client27/web63/log ext3 rw,noatime,errors=remount-ro,barrier=0,data=writeback,jqfmt=vfsv0,usrjquota=aquota.user,grpjquota=aquota.group 0 0
root@artemis:/var/www/clients/client27/web63# lsattr -d /var/www/clients/client27/web63
----i-------------- /var/www/clients/client27/web63

```
All seem RW but what is the i ?

---

### Post by schragge on 2013-04-22
[s]Judging by the output, looks like you are on RHEL5.[/s][highlight]Edit[/highlight] Sorry, haven't noticed the output of lsb_release.
From [chattr(1)](http://manpages.ubuntu.com/manpages/lucid/en/man1/chattr.1.html):
> A file with the `i' attribute cannot be modified: it cannot be  deleted or  renamed,  no  link  can  be created to this file and no data can be
written to the file.  Only the superuser or a  process  possessing  the CAP_LINUX_IMMUTABLE capability can set or clear this attribute.

---

### Post by capscrew on 2013-04-22
The i stands for immutable.  See```
man chattr
```

This was probably done when you changed the permissions th 777 on directories that should not have that open permissions.

---

