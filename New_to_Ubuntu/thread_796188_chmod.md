---
title: "chmod"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by NaF on 2008-05-16
Hi again!
So, trying to get the most awesome game in history, Baldurs Gate, to run on my ubuntu machine. After some fiddling with Wine, I got it installed and .. kinda.. working. I've been trying to find out how to use the chmod thing, thought I did figure it out, but when I apply it to the game directory (so I can save games and change whatever the game needs), I still have no write privileges, hm. 

here what I enter into the terminal: 

sudo chmod 777 '/home/naf/.wine/drive_c/Program Files/Black Isle/BGII - SoA'

what's wrong :oops:?

---

### Post by Mr A Mouse on 2008-05-16
Try this:

```

sudo chmod -R 777 '/home/naf/.wine/drive_c/Program Files/Black Isle/BGII - SoA'

```

This not only opens that file to writing, but recursively opens all files below it for writing.

---

### Post by damis648 on 2008-05-16
Also just try right clicking in Nautilus and select properties and change the permissions from there.

---

### Post by unutbu on 2008-05-16
Please note I have no experience with wine, so I don't know if what I'm going to tell you is the best way to set Baldur's Gate up. 

```
sudo chmod -R 700 '/home/naf/.wine/drive_c/Program Files/Black Isle/BGII - SoA'
```

The -R flag tells chmod to act recursively -- not only will the top level directory have permission 700, so will all the files underneath it. Since this directory looks to be in your home directory, I changed the permission from 777 to 700. This will give the owner of the files complete read, write, execute permissions, but nothing to the rest of the world. 

There is also the possibility that you don't own 
BGII - SoA. (It might be owned by root, for example). You can find that out by typing

```
ls -ld '/home/naf/.wine/drive_c/Program Files/Black Isle/BGII - SoA'
```

To change the ownership of all the files in that directory:

```
sudo chown -R naf:naf '/home/naf/.wine/drive_c/Program Files/Black Isle/BGII - SoA'
```

---

### Post by NaF on 2008-05-16
> **Mr A Mouse said:**
> Try this:

```

sudo chmod -R 777 '/home/naf/.wine/drive_c/Program Files/Black Isle/BGII - SoA'

```

This not only opens that file to writing, but recursively opens all files below it for writing.

ahh the -R did that :), When I type the command in, the permissions are still the same, when looking at them through the windows explorer thingy. 

> **damis648 said:**
> Also just try right clicking in Nautilus and select properties and change the permissions from there.

I DID try that, but the changes are not remembered, I don't know what I'm doing wrong:(

> **unutbu said:**
> Please note I have no experience with wine, so I don't know if what I'm going to tell you is the best way to set Baldur's Gate up. 

```
sudo chmod -R 700 '/home/naf/.wine/drive_c/Program Files/Black Isle/BGII - SoA'
```

The -R flag tells chmod to act recursively -- not only will the top level directory have permission 700, so will all the files underneath it. Since this directory looks to be in your home directory, I changed the permission from 777 to 700. This will give the owner of the files complete read, write, execute permissions, but nothing to the rest of the world. 

There is also the possibility that you don't own 
BGII - SoA. (It might be owned by root, for example). You can find that out by typing

```
ls -ld '/home/naf/.wine/drive_c/Program Files/Black Isle/BGII - SoA'
```

To change the ownership of all the files in that directory:

```
sudo chown -R naf:naf '/home/naf/.wine/drive_c/Program Files/Black Isle/BGII - SoA'
```

Same for the  ```
sudo chmod -R 700 '/home/naf/.wine/drive_c/Program Files/Black Isle/BGII - SoA'
``` 
the permissions still look the same, and I was the owner of the folder to begin with?

---

### Post by NaF on 2008-05-16
I'm looking here: 
[IMG]http://www.fo.person.dk/Screenshot.png[/IMG]

---

### Post by unutbu on 2008-05-16
Please post

```
mount
sudo fdisk -l
ls -ld '/home/naf/.wine/drive_c/Program Files/Black Isle/BGII - SoA'
ls -ld '/home/naf/.wine/drive_c/Program Files/Black Isle/'
ls -ld '/home/naf/.wine/drive_c/Program Files/'
ls -ld '/home/naf/.wine/drive_c/'
ls -ld '/home/naf/.wine/'
ls -ld '/home/naf/'
```

---

### Post by NaF on 2008-05-16
Ok :) 

```

naf@naf-desktop:~$ mount
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/naf/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=naf)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=naf)
naf@naf-desktop:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7a7c7a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48640   390700768+   7  HPFS/NTFS
naf@naf-desktop:~$ ls -ld '/home/naf/.wine/drive_c/Program Files/Black Isle/BGII - SoA'
drwx------ 20 naf naf 4096 2008-05-16 13:27 /home/naf/.wine/drive_c/Program Files/Black Isle/BGII - SoA
naf@naf-desktop:~$ ls -ld '/home/naf/.wine/drive_c/Program Files/Black Isle/'
drwxr-xr-x 3 naf naf 4096 2008-05-16 12:24 /home/naf/.wine/drive_c/Program Files/Black Isle/
naf@naf-desktop:~$ ls -ld '/home/naf/.wine/drive_c/Program Files/'
drwxr-xr-x 6 naf naf 4096 2008-05-16 12:24 /home/naf/.wine/drive_c/Program Files/
naf@naf-desktop:~$ ls -ld '/home/naf/.wine/drive_c/'
drwxr-xr-x 4 naf naf 4096 2008-05-16 11:21 /home/naf/.wine/drive_c/
naf@naf-desktop:~$ ls -ld '/home/naf/.wine/'
drwxr-xr-x 4 naf naf 4096 2008-05-16 14:28 /home/naf/.wine/
nafnaf-desktop:~$ ls -ld '/home/naf/'


```

---

### Post by unutbu on 2008-05-16
Everything looks ok. Are you still having trouble writing to 'BGII - SoA'? If so, where are you getting the error message? Is it something BG spits out? Or if it's from the terminal, what command do you type to elicit the error?

---

### Post by NaF on 2008-05-16
> **unutbu said:**
> Everything looks ok. Are you still having trouble writing to 'BGII - SoA'? If so, where are you getting the error message? Is it something BG spits out? Or if it's from the terminal, what command do you type to elicit the error?

Yes I still get an error from baldurs gate. But the way I'm validating it, is by going into the folder from the windows explorer and looking at the permission (ref screenshot above), that haven't showed that I have write permissions yet.

---

### Post by unutbu on 2008-05-16
Try RomeReactor's suggestion:
[http://ubuntuforums.org/showthread.php?t=345905](http://ubuntuforums.org/showthread.php?t=345905)

You might also find more knowledgeable help here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2827](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2827)

---

