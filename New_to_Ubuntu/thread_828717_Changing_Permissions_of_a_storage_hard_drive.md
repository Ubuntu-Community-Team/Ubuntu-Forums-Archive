---
title: "Changing Permissions of a storage hard drive"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by DarthOpto on 2008-06-14
I have two hard drives in my machine.
/dev/sda1 - this is my main hard drive and what Ubuntu Hardy Heron is installed on

/dev/sdb1 - this is an ext3 formatted hard drive which has nothing on it except an empty Lost and Found folder. I would like my standard user to be able to read/write to this drive however I cannot for the life of me figure out why the chown command does not appear to be working.

I have done the following:

darthopto@darthopto-desktop:~$ chown -hR darthopto:darthopto /dev/sdb1
darthopto@darthopto-desktop:~$ chown -hR darthopto:darthopto /dev/sdb2
darthopto@darthopto-desktop:~$ chown -hR darthopto:darthopto /dev/sdb5
darthopto@darthopto-desktop:~$ ls -la /media
total 20
drwxr-xr-x  5 root      root       4096 2008-06-13 23:44 .
drwxr-xr-x 21 root      root       4096 2008-06-07 09:49 ..
lrwxrwxrwx  1 root      root          6 2008-06-07 08:57 cdrom -> cdrom0
drwxr-xr-x  2 root      root       4096 2008-06-07 08:57 cdrom0
-rw-r--r--  1 root      root        140 2008-06-13 23:44 .hal-mtab
-rw-------  1 root      root          0 2008-06-11 21:14 .hal-mtab-lock
drwxr-xr-x  3 root      root       4096 2008-05-28 00:20 storage
drwxrwxrwx  5 darthopto 4294967295  200 2008-05-17 11:06 UDF Volume

and still the root user is the owner of the drive. Please someone help me get it so I can read/write to this drive.

Thank you.

---

### Post by iaculallad on 2008-06-14
Try placing sudo first on your first command, if it still fails try using chmod:

```
sudo chmod 666 /mount/point
```

---

### Post by sam_delta on 2008-06-14
> Volume, Mount and File System Permissions are different than FilePermissions. 
check out this link
[https://help.ubuntu.com/community/VolumePermissions](https://help.ubuntu.com/community/VolumePermissions)

the 'chown' to the mount point will probably work, but as soon as you create a new directory, that directory wont have permission until you type the command again, i believe thats the diference between volume and file permissions

any questions we will be around

sam

---

### Post by DarthOpto on 2008-06-14
I am not seeing my sdb volume in my fstab, to even change the volume permissions. 
How do I get that added?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7438e2d1-0e1a-4080-ae58-a2599ec89731 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fc1ba4b8-a363-4630-9987-3f5808c38d2c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by sam_delta on 2008-06-14
make sure you unmount the volume before continue

first, make a backup of your fstab by typing ```
sudo cp /etc/fstab /etc/fstab.backup
```
then, make the folder in which it will mount under media by typing
```
sudo mkdir /media/storage
```
open fstab by typing ```
sudo gedit /etc/fstab
```
fstab will open then, add this line to the fstab```
/dev/sdb1    /media/storage    ext3   defaults,umask=000    0    0
```

then update/mount it with ```
sudo mount -a
```


sam

---

### Post by DarthOpto on 2008-06-14
Thank you, but I followed the directions posted by Sam and I still have no permission to put files into my storage volume. 

HELP

---

### Post by sam_delta on 2008-06-14
does it mounts on /media/storage?

sam

---

### Post by DarthOpto on 2008-06-14
> **sam_delta said:**
> does it mounts on /media/storage?

sam

Yes it does mount on /media/storage

---

### Post by sam_delta on 2008-06-14
try editing your fstab so the line we added looks like this
```
/dev/sdb1    /media/storage    ext3   umask=000    0    0
```
NOTE: we removed the "defaults," word just before umask

update/mount with
```
sudo mount -a
```

sam

---

### Post by DarthOpto on 2008-06-14
> **sam_delta said:**
> try editing your fstab so the line we added looks like this
```
/dev/sdb1    /media/storage    ext3   umask=000    0    0
```
NOTE: we removed the "defaults," word just before umask

update/mount with
```
sudo mount -a
```

sam

Ok, I made that change and still I am unable to make any changes to the storage volume.

Here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7438e2d1-0e1a-4080-ae58-a2599ec89731 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fc1ba4b8-a363-4630-9987-3f5808c38d2c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sdb1    /media/storage    ext3   umask=000    0    0

Here is the result of ls -la /media after making the change.

drwxr-xr-x  5 root      root       4096 2008-06-14 11:11 .
drwxr-xr-x 21 root      root       4096 2008-06-07 09:49 ..
lrwxrwxrwx  1 root      root          6 2008-06-07 08:57 cdrom -> cdrom0
drwxr-xr-x  2 root      root       4096 2008-06-07 08:57 cdrom0
-rw-r--r--  1 root      root         78 2008-06-14 11:11 .hal-mtab
-rw-------  1 root      root          0 2008-06-11 21:14 .hal-mtab-lock
drwxr-xr-x 21 root      root       4096 2008-06-07 09:49 storage
drwxrwxrwx  5 darthopto 4294967295  200 2008-05-17 11:06 UDF Volume

---

### Post by cariboo on 2008-06-14
You can't change the ownership of automatically mounted volumes but you can change the permissions to make them world readable, in other words anybody can write to them. To find your automounted drives check /etc/mtab. To change the permissions to world readable in a terminal type:

```
sudo chmod -R 777 /media/storage
```

The way you've got /media/storage set now you've got it so everyone can execute the files but not change them.

Jim

---

### Post by DarthOpto on 2008-06-14
OK I did that and my darthopto user still does not have any rights to the storage volume.

drwxrwxrwx  6 root      root       4096 2008-06-14 13:19 .
drwxrwxrwx 21 root      root       4096 2008-06-07 09:49 ..
lrwxrwxrwx  1 root      root          6 2008-06-07 08:57 cdrom -> cdrom0
drwxrwxrwx  2 root      root       4096 2008-06-07 08:57 cdrom0
-rwxrwxrwx  1 root      root        141 2008-06-14 13:19 .hal-mtab
-rwxrwxrwx  1 root      root          0 2008-06-11 21:14 .hal-mtab-lock
drwxrwxrwx 21 root      root       4096 2008-06-07 09:49 storage
drwxr-xr-x  3 root      root       4096 2008-05-28 00:20 storage_
drwxrwxrwx  5 darthopto 4294967295  200 2008-05-17 11:06 UDF Volume


What can I do to get this up and running so my darthopto user has permissions to read/write on this volume?

---

### Post by Duck2006 on 2008-06-14
Some info on mounting that may help.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by DarthOpto on 2008-06-14
The problem is that the hard drive is already mounted, and I have no permissions. No amount of chmod and chown has seemed to work yet.

---

### Post by Duck2006 on 2008-06-14
From the last link i gave you, permissions.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Duck2006 on 2008-06-14
[http://ubuntuforums.org/archive/index.php/t-530520.html](http://ubuntuforums.org/archive/index.php/t-530520.html)

---

### Post by sam_delta on 2008-06-14
drwxrwxrwx 21 root root 4096 2008-06-07 09:49 storage

that line means that root owns it, but everyone is able to read/write

also, does changind the owner helps? it appears that root owns it
```
sudo chown darthopto -R /media/storage
```
while mounted, go into /media/storage using the gui and right click the folder storage,  then click properties, ,, under the permissions tab, check whos the owner and which priviledges does every user have 



sam

---

