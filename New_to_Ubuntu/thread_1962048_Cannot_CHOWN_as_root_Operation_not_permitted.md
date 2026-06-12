---
title: "Cannot CHOWN as root: Operation not permitted"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by CaptainZn on 2012-04-20
Please help.

I am trying to set access for various local FTP users to folders on the Ubuntu FTP server. 

I cannot seem to get the folder permissions correct. I am logged on as root, and I am getting: 

root@ig-ftp01:/mnt/iscsi/srv/files/ftp# chown 8ta:ftp-users /mnt/iscsi/srv/files/ftp/8ta
chown: changing ownership of `/mnt/iscsi/srv/files/ftp/8ta': Operation not permitted

The current folder permissions are:

drwxr-xr-x  6 root root 16384 2012-04-05 17:24 8ta

The filesystem is mounted as:

/dev/sda1 on /mnt/iscsi type vfat (rw)


Thanks in advance.

---

### Post by iponeverything on 2012-04-20
vfat does not support the inode characteristics you are attempting to modify via the chown command.

---

### Post by jerome1232 on 2012-04-20
Furthermore the permissions are determined at mount time. If it is in fstab you would need to modify the options you are passing the filesystem.

There are a few examples here, hopefully you can garner what you need from this [https://help.ubuntu.com/community/Fstab#fat16_and_fat32](https://help.ubuntu.com/community/Fstab#fat16_and_fat32)

edit: Now that I think about it, why on earth are you using fat? It would be much, much, much better to any other native linux filesystem. They will have more features, have more tools to work with, and fully support Unix style permissions.

---

### Post by NikTh on 2012-04-20
> **iponeverything said:**
> vfat does not support the inode characteristics you are attempting to modify via the chown command.

+1

---

