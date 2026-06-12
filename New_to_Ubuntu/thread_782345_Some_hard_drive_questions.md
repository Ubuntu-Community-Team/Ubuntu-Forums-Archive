---
title: "Some hard drive questions"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by nikoPSK on 2008-05-04
Hello to all of Ubuntuforums. I have a bit of a conundrum right now... you see, my question is; can someone help me with automounting my hard drive? I would like it to appear in places and have files execute.

Here is the output of sudo fdisk -l:
```
niko@home:~$ sudo fdisk -l
[sudo] password for niko: 

Disk /dev/sda: 20.4 GB, 20496236544 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15f4a6d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2382    19133383+  83  Linux
/dev/sda2            2383        2491      875542+   5  Extended
/dev/sda5            2383        2491      875511   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa5b5a5b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2434    19551073+  83  Linux
niko@home:~$ 

```

---

### Post by Rocket2DMn on 2008-05-04
Can you also please post
```
cat /etc/fstab
ls -l /dev/disk/by-uuid
mount
```

---

### Post by nikoPSK on 2008-05-04
Wehee!
```
niko@home:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3edad271-638a-4625-8434-e8a56eea6bb7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=be61f2a1-df3b-4ab5-b80f-769e8661029a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
niko@home:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-05-04 18:40 3edad271-638a-4625-8434-e8a56eea6bb7 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-05-04 18:40 5afc7598-076c-442b-b1f9-8f693ce0f9df -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-05-04 18:40 be61f2a1-df3b-4ab5-b80f-769e8661029a -> ../../sda5
niko@home:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/niko/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=niko)
niko@home:~$ 
```

---

### Post by Rocket2DMn on 2008-05-04
OK, let's edit fstab to add the entry
```
gksudo gedit /etc/fstab
```
Now add the line
```
UUID=5afc7598-076c-442b-b1f9-8f693ce0f9df /media/<your_mount_point> ext3 defaults 0 0
```
Save and close, then run
```
sudo mkdir /media/<your_mount_point>
sudo mount -a
```

Change <your_mount_point> to whatever you want to call it.  You may need to chown the mount point, too
```
sudo chown -R <yourusername>:<yourusername> /media/<your_mount_point>
```

---

### Post by nikoPSK on 2008-05-04
So before you added to the end if your post, I couldn't put files in. Now, I made a simple script to se if you could execute things inside it and it doesn't go. :)

---

### Post by Rocket2DMn on 2008-05-04
In fstab, change "defauts" to "defaults,exec", save and close, then run
```
sudo umount /media/<your_mount_point>
sudo mount -a
```
You should now be able to execute on the drive.

---

### Post by nikoPSK on 2008-05-04
> **Rocket2DMn said:**
> <snippy>Done, but when I try to launch say, gridwars in there I get:
```
niko@home:/media/maxtor/gridwars_lin$ ./gridwars
./gridwars: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
niko@home:/media/maxtor/gridwars_lin$ 

```

---

### Post by Rocket2DMn on 2008-05-04
Do
```
sudo apt-get install build-essential
```
Looks like it's trying to find some dependencies, namely the C++ standard libraries.

---

### Post by Rocket2DMn on 2008-05-04
If you compiled that program from source on a different machine or different install, you should remake it on this setup so it can connect with the correct and up to date dependencies.

---

### Post by nikoPSK on 2008-05-04
Nevermind, I was missing some C++ libraries. :p Thanks to you all.

---

