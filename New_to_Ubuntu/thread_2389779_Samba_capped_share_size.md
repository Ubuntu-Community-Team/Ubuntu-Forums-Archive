---
title: "Samba capped share size"
date: 2018-04-21
forum: New to Ubuntu
---

### Post by eule8070 on 2018-04-21
Hello Forum,

i have a problem conserning the size of samba shares. Apparently they are always capped at extact 28,4 GB
[ATTACH=CONFIG]279385[/ATTACH]

My smb.conf looks like this:
```

[global]
workgroup = HOMEGROUP
server string = %h server (Samba, Ubuntu)
security = user
encrypt passwords = true
invalid users = root


[shared]
path =/home/cloud
writeable = yes
public = no
printable = no
valid users = user
### Recycle ###
vfs object = recycle
recycle:repository = Papierkorb
recycle:touch = Yes
recycle:keeptree = Yes
recycle:versions = Yes


[music]
path = /var/lib/minidlna/music
writeable = yes
public = no
printable = no
valid users = user


[videos]
path = /var/lib/minidlna/videos
writable = yes
public = no
printable = no
valid users = user

```

And i have the following partitions:
Command: df -h[
```
Dateisystem    Größe Benutzt Verf. Verw% Eingehängt auf
udev            1,9G       0  1,9G    0% /dev
tmpfs           384M    6,0M  378M    2% /run
/dev/sda2        29G    9,6G   18G   36% /
tmpfs           1,9G       0  1,9G    0% /dev/shm
tmpfs           5,0M       0  5,0M    0% /run/lock
tmpfs           1,9G       0  1,9G    0% /sys/fs/cgroup
/dev/loop2       87M     87M     0  100% /snap/core/4407
/dev/loop1       82M     82M     0  100% /snap/core/4206
/dev/loop0      185M    185M     0  100% /snap/nextcloud/5627
tmpfs           384M       0  384M    0% /run/user/0
```

Command: fidisk -l
```
Gerät      Boot   Start      Ende  Sektoren Größe Id Typ
/dev/sda1          2048   1953791   1951744   953M 82 Linux Swap / Solaris
/dev/sda2  *    1953792 629145599 627191808 299,1G 83 Linux

```

EDIT: I am using Ubuntu 16.04 LTS - Server

After a long time of seraching i dont know what to do. I hope anyone can help me there, i am new at linux and would like to use my entire 300GB of storage.
Thank you in advance.

Greetings eule8070

---

### Post by Holger_Gehrke on 2018-04-21
If the output of df is to be believed, you have somehow managed to create a filesystem that is smaller than the partition it sits on. Did you restore an image of a partition from a different (smaller) hard disk on this one ? 'df' gives the size of the root-partition as 29G with 18G free, while fdisk gives a size of 299G. So the good news is: your smb.conf is not the problem ...

You might want to read the manual of resize2fs.

Holger

---

### Post by eule8070 on 2018-04-21
Thank you for your fast response. I am using a virtual server with an .vhdx disk. I did make the hard disk bigger with the hyperv-converter. But how can i change the size of the root partition?

---

### Post by eule8070 on 2018-04-21
Thanks for the help,i did the partitioning again and now its working perfectly.

---

