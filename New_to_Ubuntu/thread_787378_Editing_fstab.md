---
title: "Editing fstab"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Gregory_NZL on 2008-05-08
Could someone please help me mount a partition as a non root user. I have tried inserting 'user' before and after the option 'realtime' but to no avail.

Here is the line from my fstab.

```
# /dev/sda7
UUID=3a9c0210-ecbc-4c68-b18f-455a98bb38d9 /media/data           ext3    relatime        0       2
```

I have tried checking the relevant [TuxFile](http://www.tuxfiles.org/linuxhelp/fstab.html) but it doesn't cover all the options. What exactly does the option realtime do?

---

### Post by glennric on 2008-05-08
You will have to make sure that you have write permission for /media/data, I am not sure if that is all you need though.

---

### Post by Gregory_NZL on 2008-05-08
I'm a newbie, how would I go about ensuring write permissions? thx

---

### Post by glennric on 2008-05-08
```
sudo chmod +w file-or-directory-name
```

---

### Post by lemming465 on 2008-05-08
The *relatime* option is described in *man mount*; classic unix filesystems have 3 timestamps for files, devices, and directories: last read (access) time, last write time, and last inode change time.  The inode change time is not the same as the file creation time, or at least not necessarily.  On classic systems the read time ("atime") is updated every time the file is read.  On busy systems updating the timestamps can be a significant percentage of the disk I/O.  So there are some mount options to tune the behavior.  "atime" is the classic behavior; "noatime" is the variant that never updates, and "relatime" is in between.

If you are allowing ordinary users to mount the filesystem, you probably want options like *rw,user,noauto,nosuid,nodev*.

---

### Post by Gregory_NZL on 2008-05-08
> **lemming465 said:**
> If you are allowing ordinary users to mount the filesystem, you probably want options like *rw,user,noauto,nosuid,nodev*.

If I add those options where should I place them in the file? Will I also need to chmod the directory like glennric mentioned?

I tried the following and the drive mounts ok but i still cant add or modify files without root permission.

```
# /dev/sda7
UUID=3a9c0210-ecbc-4c68-b18f-455a98bb38d9 /media/data           ext3    rw,user,relatime        0       2

```

---

### Post by lemming465 on 2008-05-08
The options go in the 4th field, after the filesystem type.  (The first three are device partition, mount point directory, and file system type.)  An ext3 filesystem is going to have standard unix owner and permissions behaviors; if you need to do stuff to it you will have to use a combination of "sudo chown", "sudo chgrp" and "sudo chmod" to give yourself the permissions you want. 

Actually, reading "man mount" in more detail, the "user" option already implies nodev,nosuid,noexec.  So the existing options of "rw,user,relatime" are OK unless you need to run programs off it, in which case add ",exec".

---

### Post by bodhi.zazen on 2008-05-08
See also : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Gregory_NZL on 2008-05-09
> **lemming465 said:**
> Actually, reading "man mount" in more detail, the "user" option already implies nodev,nosuid,noexec.  So the existing options of "rw,user,relatime" are OK unless you need to run programs off it, in which case add ",exec".

From what I can tell I have entered the options in the correct field. But still don't have permission to use it. What am I doing wrong?

---

### Post by bodhi.zazen on 2008-05-09
Can you post the line you are using from /etc/fstab ?

---

### Post by lemming465 on 2008-05-09
> don't have permission to use it

Can you give some specific details about what commands you type, and what error messages you get back?

---

### Post by Gregory_NZL on 2008-05-09
Thanks for all your help guys. The **sda7** partition mounts alright and has a handy icon on my desktop, but I cannot add files as a normal user. The error message is 

> There was an error copying the file to /media/data. Permission Denied.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cc0604a2-ae9d-4a5b-aaad-4849cf66341c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=3a9c0210-ecbc-4c68-b18f-455a98bb38d9 /media/data           ext3    rw,user,relatime        0       2
# /dev/sda6
UUID=39c77689-bf75-49ca-a8dc-f99173c189b8 /home           ext3    relatime        0       2
# /dev/sda5
UUID=e3fc8a29-8e49-4579-b081-7910ffcd5a1c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by Xiong Chiamiov on 2008-05-10
Try changing this line
```

UUID=3a9c0210-ecbc-4c68-b18f-455a98bb38d9 /media/data           ext3    rw,user,relatime        0       2

```
to this
```

UUID=3a9c0210-ecbc-4c68-b18f-455a98bb38d9 /media/data           ext3    rw,user,relatime,**umask=007**        0       2

```

---

### Post by Gregory_NZL on 2008-05-10
Well, umask sounds like a great idea until I checked "man mount" and discovered ext3 does not support the umask option.

---

### Post by Xiong Chiamiov on 2008-05-10
Oh, that's right, I ran into that when I reformatted some storage disks to ext3 from fat.  I believe you then just have to change the permissions on the disk.
```

sudo chmod 770 /media/data

```
or, if you prefer, through the GUI
```

gksudo nautilus

```
right-click on the folder, permissions.

---

### Post by Gregory_NZL on 2008-05-10
I found the following command on the Ubuntu documentation [wiki]("https://help.ubuntu.com/community/InstallingANewHardDrive")

```
sudo chown -R USERNAME:GROUP /media/data

```

It has allowed me to access the partition as a user, but I don't understand why I need to change ownership. Everything else I read suggests you can mount a partition by editing the fstab and using the option 'user'?

---

### Post by Xiong Chiamiov on 2008-05-10
I think that mounting as with option user allows the user to mount it, but the permissions on the folder are still set to whatever they were before.  I'm not sure if that made sense to you, but it did in my head...

---

### Post by Gregory_NZL on 2008-05-10
Yea it makes sense to me as well.. thanks for the help on this.

Interestingly if I leave the default option of 'realtime' I can still mount and access the partition as a normal user. It seems the chown command is the important one for me. ```
# /dev/sda7
UUID=3a9c0210-ecbc-4c68-b18f-455a98bb38d9 /media/data           ext3    relatime        0       2

```

---

