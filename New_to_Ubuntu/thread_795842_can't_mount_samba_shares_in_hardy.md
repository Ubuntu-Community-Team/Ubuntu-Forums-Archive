---
title: "can't mount samba shares in hardy"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by lunaz on 2008-05-15
```

sudo mount -t smbfs -o username=myname,password=mypw //192.168.1.102/music /media/music

```

```

rebecca@soggy:/media$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=87ff5bcb-396a-468a-a324-bdbe129890f0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=e476c6e2-da4a-d7b2-c7be-d43b46b927ba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3 /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
//192.168.1.102/rebecca /media/rebecca cifs auto,iocharset=utf8,uid=rebecca,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0
//192.168.1.102/music /media/music cifs auto,iocharset=utf8,uid=rebecca,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0
rebecca@soggy:/media$

```

```

rebecca@soggy:/media$ sudo mount -a
mount error 111 = Connection refused
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
mount error 111 = Connection refused
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
rebecca@soggy:/media$

```

my other ubuntu box works still.

---

### Post by Xiong Chiamiov on 2008-05-17
For sharing between Unix-like machines, you should really use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo").  You can usually set it up easily through the GUI, starting with properties -> sharing, or something similar.

---

### Post by Aearenda on 2008-05-17
Try using '-t cifs' instead of '-t smbfs'. CIFS is a more up to date version of the protocol.

Does the credentials file still exist?
Also try removing the language settings.
This fstab line works for me, but with noauto:
```
//machine1/aea /home/aea/m1   cifs  user,noauto,credentials=/home/aea/.smbpasswd,uid=steve,gid=steve 0 0
```

---

