---
title: "trouble with permission on my newly installed hd"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by mxultra on 2008-10-12
ok guys.. ive been using ubuntu hardy for a couple of weeks now.. and its a love affair.. however i've hit a snag. i used gparted to set up a ext3 filesystem, then i mounted the drive to  /media/mynewdrive .. so far so good, my problem arose when i tried to access the folder.. i got an error message stating thusly :Error while copying.
The folder "insert any name here" cannot be copied because you do not have permissions to create it in the destination.
What do i do now?...:)

---

### Post by hyper_ch on 2008-10-12
post the output of:

```

sudo fdisk -l

```

```

df -l

```

```

cat /etc/fstab

```

```

ls -al /media

```

---

### Post by hellion0 on 2008-10-12
Open a Terminal and try copying something to the drive via it:
```
cp any_file_will_do.here /media/mynewdrive
```
...As the example provides, any file will do. If that fails, prefix "cp" with sudo:
```
sudo cp any_file_will_do.here /media/mynewdrive
```
...and if using sudo helps, it's a permissions issue, in which case doing this:
```
cat /etc/fstab
```
...and posting the results can help us aid you.

Of course, if even the admin-driven access doesn't work, it could be a different issue.

---

### Post by mxultra on 2008-10-12
mxultra@mxultra-desktop:~$ sudo fdisk -l
[sudo] password for mxultra: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05e205e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9447    75882996   83  Linux
/dev/sda2            9448        9729     2265165    5  Extended
/dev/sda5            9448        9729     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120060444672 bytes
16 heads, 63 sectors/track, 232632 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x775095b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      232631   117245992+  83  Linux
mxultra@mxultra-desktop:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             75285156  54958476  16532532  77% /
varrun                  387640       224    387416   1% /var/run
varlock                 387640         0    387640   0% /var/lock
udev                    387640        52    387588   1% /dev
devshm                  387640        12    387628   1% /dev/shm
lrm                     387640     39780    347860  11% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon      75285156  54958476  16532532  77% /home/mxultra/.gvfs
/dev/sdb1            116321872    192252 110267324   1% /media/mynewdrive
mxultra@mxultra-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=08ebd961-1840-406b-ae16-d18ba2680213 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=962ff166-6ca2-43f1-ab22-8586d540fa36 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
mxultra@mxultra-desktop:~$ ls -al /media
total 16
drwxr-xr-x  4 root root 4096 2008-10-12 02:15 .
drwxr-xr-x 21 root root 4096 2008-09-30 01:01 ..
lrwxrwxrwx  1 root root    6 2002-08-05 18:27 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2002-08-05 18:27 cdrom0
-rw-r--r--  1 root root    0 2008-10-12 02:15 .hal-mtab
-rw-------  1 root root    0 2008-10-12 01:57 .hal-mtab-lock
drwxr-xr-x  3 root root 4096 2008-10-11 02:31 mynewdrive


ok.. there it is.. hope it helps..

---

### Post by mxultra on 2008-10-12
mxultra@mxultra-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=08ebd961-1840-406b-ae16-d18ba2680213 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=962ff166-6ca2-43f1-ab22-8586d540fa36 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by hellion0 on 2008-10-12
Unmount your new drive first:
```
sudo umount /media/mynewdrive
```
Then back up /etc/fstab:
```
sudo cp /etc/fstab /etc/fstab.bak
```
Now open /etc/fstab in a text editor:
```
sudo nano /etc/fstab
OR
gksu gedit /etc/fstab
```
Then append this line to the bottom:
```
/dev/sdb1 /media/mynewdrive ext3 defaults 0 0
```
Save and exit (if you go with nano, use CTRL+O, Enter, then CTRL+X to save and exit). Then remount your new drive.

---

### Post by mxultra on 2008-10-12
alright now were starting to get somewhere.. the file copied fine when i used sudo.. where do we go from here?

---

### Post by hellion0 on 2008-10-12
See my previous post. It's a permissions issue. If what I suggested works, you should have normal permissions. If not, post back.

---

### Post by vanadium on 2008-10-12
You need to know something of permissions. By default, the user can only write in his home directory. For other locations, permission must be granted by the root user.

You can use an instance of nautilus with root permissions to accomplish this. A nautilus window with root permissions can be launched using the command

gksudo nautilus

Using that nautilus window, you can do anything, including deleting the whole system, so be carefull and close it as soon as you are finished.

* If you want to grant the whole hd to one user, change the owner of the mount point.
* If there are multiple users, create directories on the new hd and grant these to the different users.
* In any case, you can create a symbolic link to the storage on the new hd in the user's home directories for convenient access.

---

### Post by hyper_ch on 2008-10-12
when posting output put it into [noparse]```

```[/noparse] brackets so that it's easier to read.

---

### Post by mxultra on 2008-10-12
alrighty.. did as you said and got this: Error making symbolic link: Permission denied

---

### Post by mxultra on 2008-10-12
beautiful! the nautilus approach worked! many thanks friend!
more knowledge... more power!

---

