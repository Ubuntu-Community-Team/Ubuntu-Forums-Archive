---
title: "Why is my USB suddenly showing as locked in ubuntu?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-09-30
First I have to ask, do I need to manually unmount the USB stick before pulling it out. In Windows this tis not necessary, maybe Ubuntu is different. Note however that my USB says in the instruction that you dont have to dismount the drive; perhaps they assume everyone is using Windows.

Another thing is that there is a file that neither windows or Ubuntu can delete. Might be related. Now Im noticing that suddenly whenever I plug in this USB it shows all the files as locked, yet in windows I have access to all of them (except for the one corrupted file of course).


Thanks

---

### Post by Tatty on 2008-09-30
You should always unmount a usb drive before removing in both ubuntu and windows.

Windows does come with an option which claims to make it safe to remove a drive without unmounting, however I would not rely on this.

---

### Post by Gannon8 on 2008-09-30
Most USB thumb drives have a switch that prevents writing to the device. Make sure it is set to unlocked.

If that does not work, post the output of these commands:
```
sudo fdisk -l
mount
```

---

### Post by Dan_Dranath999 on 2008-09-30
There's a risk to damage your files if you remove an USB stick without "safely unmounting" it in WINDOWS XP (or MacOS). I know, because my files have been corrupted this way more than 2 times in several years.

---

### Post by Lateforgym on 2008-09-30
Here is the print out. Note that I got it to not be locked, I think, I hit f-5 to refresh as Maybe I was getting to the USB too fast. I have a lot of stuff on it. However, I cant paste to it. 

x3@x3-laptop:~$ sudo fdisk -l
[sudo] password for x3: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7acf7acf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3589    28828611    7  HPFS/NTFS
/dev/sda2            3590        4864    10241437+   5  Extended
/dev/sda5            3590        4804     9759456   83  Linux
/dev/sda6            4805        4864      481918+  82  Linux swap / Solaris

Disk /dev/sdb: 2055 MB, 2055021056 bytes
16 heads, 63 sectors/track, 3981 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3982     2006825    e  W95 FAT16 (LBA)
x3@x3-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/x3/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=x3)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


See anything wrong?

---

### Post by Crafty Kisses on 2008-09-30
Do the following:
```
gksu nautilus
```
See if you can access it.

---

### Post by richg on 2008-09-30
I have had the same thing start happening to me after a Ubuntu update about two months ago. Ubuntu seems to be locking my files now and affects a couple different flash drives once in a while. I put the flash drive into my EEE PC or my Linspire laptop and delete the files. My files with Ubuntu also show locked now but in the other two PCs no problem. I have to manually unlock a file when I want to modify the file.

Rich

---

### Post by Lateforgym on 2008-09-30
x3@x3-laptop:~$ gksu nautilus
Initializing nautilus-share extension

** (nautilus:6133): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

seahorse nautilus module shutdown
x3@x3-laptop:~$ 
x3@x3-laptop:~$

---

### Post by Lateforgym on 2008-10-01
How do I manually unlock the files?

---

