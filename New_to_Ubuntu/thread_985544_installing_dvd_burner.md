---
title: "installing dvd burner"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by radiogirl on 2008-11-17
can anyone tell me if I will be able to install the ez dub DVD RW on ubuntu? If so how? The software that came with it won't install.

---

### Post by bumanie on 2008-11-17
That is an external burner connected by isn't it? In theory, it should be a plug-and-play device. What happens when you plug it in? Any software/firmware that came with the burner will be for windows - that won't work with ubuntu.

---

### Post by halitech on 2008-11-17
if its a usb connection, open a terminal and type```
sudo lsusb
```then plug the cable in and do the same command. post back the results

---

### Post by PierreDeKat on 2008-11-17
The bad news is that whatever software you have probably isn't made for Linux. The good news is that you can always use Brasero or several other applications to burn CDs, DVDs, and so on.

---

### Post by radiogirl on 2008-11-17
I tried opening a terminal. This is what I got 
Bus 002 Device 006: ID 1c6b:a120  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0461:4d15 Primax Electronics, Ltd 
Bus 001 Device 002: ID 413c:2003 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
The only difference from the first command was
Bus 002 Device 006: ID 1c6b:a120  
I am still :confused:!!!!
I am assuming that I cannot use the software that came with my burner.

---

### Post by halitech on 2008-11-18
ok, thats a good sign that it is being seen when you plug it in.

Open a terminal again and with the burner plugged in, type
```
sudo fdisk -l
```
thats a lower case L, not the number 1. then type in
```
sudo mount
```

post back the results of both commands.

---

### Post by radiogirl on 2008-11-18
ok here are the results of the first command
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4801    38564001   83  Linux
/dev/sda2            4802        4925      996030   82  Linux swap / Solaris
/dev/sda3            4926        9726    38564032+  83  Linux
And here are the results of the second command

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/jane/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jane)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=jane)

---

### Post by Keen101 on 2008-11-18
Yeah once the drive is mounted (if not already), then Brasero should work fine. Brasero should already be installed on your ubuntu system. There is also the other cd/dvd software too. You can always install something else like Gnomebaker too. That's the power of open source software.

---

### Post by halitech on 2008-11-18
> **radiogirl said:**
> ok here are the results of the first command
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4801    38564001   83  Linux
/dev/sda2            4802        4925      996030   82  Linux swap / Solaris
/dev/sda3            4926        9726    38564032+  83  Linux
And here are the results of the second command

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/jane/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jane)
[COLOR="Red"]/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=jane)[/COLOR]

this is good, the system sees the dvd so you should be able to use it. Brasero is one option for burning, another is K3B (which I prefer)

---

