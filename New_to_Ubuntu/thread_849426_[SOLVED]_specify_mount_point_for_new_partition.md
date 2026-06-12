---
title: "[SOLVED] specify mount point for new partition"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by dmitrijledkov on 2008-07-04
I created new /dev/sda4 partition and formatted it into ext3.

How do you a make it automount as /home/user/tmp?

That directory doesn't exist yet though.

---

### Post by milosz.galazka on 2008-07-04
Just look at */etc/fstab* file and add it there...

---

### Post by jombeewoof on 2008-07-04
> **dmitrijledkov said:**
> I created new /dev/sda4 partition and formatted it into ext3.

How do you a make it automount as /home/user/tmp?

That directory doesn't exist yet though.

the directory needs to exist, you can't mount a block device to nothing.

create the directory, then set up your fstab.

---

### Post by drs305 on 2008-07-04
> **dmitrijledkov said:**
> I created new /dev/sda4 partition and formatted it into ext3.

How do you a make it automount as /home/user/tmp?

That directory doesn't exist yet though.

Normally fixed drives are mounted in /media. You can change the command to put it wherever you wish. To mount it in /media you would run:
```
sudo mkdir /*media/yourmountpointname*
```

You would then edit your fstab, after making a backup of course:
```
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
```

A typical entry would look like this:
```

UUID=**f69c6913-c385-4cda-af45-244fb7db102e** /media/yourmountpointname ext3 defaults,user 0 2 

```

To get the UUID for /dev/sda4 (or better, check them all by removing "| grep sda4":
```
sudo blkid | grep sda4
```

---

### Post by dmitrijledkov on 2008-07-04
That didn't work. I want that extra partition to automount into
```
/home/dmitrij/tmp
```
so that I will 7GB in there =D

Currently I see it in the Computer "directory" in Nautilus simply as partition. When i double click to mount it I get error that i don't have enough privileges.

This is my /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=87f82d96-97d1-4bb5-8b6c-5d740e8ce245 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=2860-11F4  /media/EFI      system  partition       vfat    defaults,utf8,umask=007,gid=46 0 1
# /dev/sda4
UUID=d18d1d66-0ebb-470d-9b6e-666befa84615 /home/dmitrij/tmp ext3    defaults,utf8,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by drs305 on 2008-07-04
You will need to add "user" after 'defaults' in the fstab entry if you want to mount it manually by  clicking on it.

Did you make a folder /home/dmitrij/tmp?

A normal ext3 fstab entry for what you want would be:
```

# /dev/sda4
UUID=d18d1d66-0ebb-470d-9b6e-666befa84615 /home/dmitrij/tmp ext3 defaults,user 0 2 

```

---

### Post by NikS on 2008-07-04
I am not sure, but just see if this helps you anyhow..

[http://ubuntuforums.org/showthread.php?t=820635](http://ubuntuforums.org/showthread.php?t=820635)

---

### Post by dmitrijledkov on 2008-07-04
> **drs305 said:**
> You will need to add "user" after 'defaults' in the fstab entry if you want to mount it manually by  clicking on it.

How do i make it automount? I don't want to mount it manually by clicking.

Maybe I formated it wrong. And I don't own it. :confused:

---

### Post by drs305 on 2008-07-04
> **dmitrijledkov said:**
> How do i make it automount? I don't want to mount it manually by clicking.

Maybe I formated it wrong. And I don't own it. :confused:

To make sure you own it:
```
sudo chown -R dmitri:dmitri /home/dmitrij/tmp
```

The last entry I gave with the suggested line for fstab should automount.

To test it:
```
sudo umount /dev/sda4
sudo mount /dev/sda4
```

---

### Post by dmitrijledkov on 2008-07-04
It worked =D

But there is Lost+found folder inside =D What is that for????

---

### Post by jombeewoof on 2008-07-04
> **dmitrijledkov said:**
> It worked =D

But there is Lost+found folder inside =D What is that for????
It's in all block devices, something you'll have to live with.

---

