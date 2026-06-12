---
title: "Down load to usb hard drive?"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by Buenadriver on 2014-02-25
Tried to download 13.10 to usb hard drive but ni option to send it there. I can open usb drive and see things there, just can't  download to it. Does the drive need to be mounted or unmounted? Thanks.

---

### Post by sandyd on 2014-02-25
Are you looking to use the USB Hard drive to install ubuntu, or to install ubuntu on the usb hard drive?

---

### Post by Buenadriver on 2014-02-25
Want to use the usb drive to try and maybe install 13.10 to PC

---

### Post by 3rdalbum on 2014-02-25
You need to follow the instructions on the Ubuntu website for creating a bootable USB.

---

### Post by Buenadriver on 2014-02-25
I have.

---

### Post by cariboo on 2014-02-25
You can't just download the iso to a usb hard drive and expect it to boot, you have to make some modifications to grub in order to do so. Have a look at [this howto,]("http://ubuntuforums.org/showthread.php?t=1549847") by a former staff member.

---

### Post by Buenadriver on 2014-02-25
Don't want to boot from usb drive. Just want to download to it.

---

### Post by sudodus on 2014-02-26
Do you want to use the USB hard drive to store a file (in this case a downloaded iso file)?

- In this case, it must be mounted (answering the question in your opening post).

- Furthermore, it must have (or some directory in it must have) write permissions.

Please post the output of the following commands ***within code tags*** in order to help us understand the details of the external drive.

0.
***Connect the external drive***

1.
```
sudo parted -l
```

2.
```
sudo ls -l /media
```

3.
Try to ***mount the external drive***, and after that

4.
```
df
```

5.
```
cat /etc/mtab
```

---

### Post by 3rdalbum on 2014-02-26
I'm afraid its not clear what you are trying to do. Are you using Ubuntu already? Do you want to install Ubuntu to your USB hard disk, or just use the USB hard disk to start the installation process? Or are you just trying to copy documents and other files to your disk?

Please use as few technical terms as possible.

---

### Post by Buenadriver on 2014-02-26
```
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  248GB  248GB   primary   ext4            boot
 2      248GB   250GB  2010MB  extended
 5      248GB   250GB  2010MB  logical   linux-swap(v1)


Model: Seagate FreeAgent Go (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ 

```

---

### Post by Buenadriver on 2014-02-26
```
ubuntu@ubuntu:~$ sudo ls -l /media
total 160
lrwxrwxrwx 1 root   root        6 Feb 26 05:49 cdrom -> /cdrom
drwx------ 1 ubuntu ubuntu 163840 Feb 26 03:26 FreeAgent Drive
ubuntu@ubuntu:~$ 








```

---

### Post by Buenadriver on 2014-02-26
```
ubuntu@ubuntu:~$ cat /etc/mtab
/cow / overlayfs rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0
/dev/sdb1 /media/FreeAgent\040Drive fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
ubuntu@ubuntu:~$ 

```

---

### Post by sudodus on 2014-02-26
Your external drive **/dev/sdb1** alias **'/media/FreeAgent Drive'** seems to be mounted read/write so it should be possible to write a file to it.

It can be seen from the ***ls -l*** command and from ***cat /etc/mtab***

---

### Post by Nayab Basha Sayed on 2014-02-26
To mount external hard drive, try this in your terminal
sudo mkdir /media/usbhd
enter password when it asks you. and enter the following command
sudo mount -t ntfs-3g /dev/sdb1 /media/usbhd

---

### Post by Buenadriver on 2014-02-26
Ok Thank you.

---

