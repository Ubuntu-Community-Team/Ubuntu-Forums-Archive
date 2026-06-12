---
title: "invalid mout option"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by dvsevin on 2013-02-08
very lost on ancient distro. i got a Fiesty Fawn distro given to me, knowing nothing i ran... i cant mout my usb flash drive i have tried everythng i can understand. about a million posts read videos watch and still nowhere.
help! 
cody@cody-laptop:~$ mkdir /mnt/sda1
mkdir: cannot create directory `/mnt/sda1': File exists
cody@cody-laptop:~$ mount/dev/sda1/mnt/sda1
bash: mount/dev/sda1/mnt/sda1: No such file or directory
cody@cody-laptop:~$ /etc/fstab
bash: /etc/fstab: Permission denied
cody@cody-laptop:~$ sudo-/etc/fstab
bash: sudo-/etc/fstab: No such file or directory
cody@cody-laptop:~$ mount/dev/sda1/mnt/sda1
bash: mount/dev/sda1/mnt/sda1: No such file or directory
cody@cody-laptop:~$ sudo mkdir /mnt/sda1
Password:
mkdir: cannot create directory `/mnt/sda1': File exists
cody@cody-laptop:~$ mount/dev/sda1/mnt/sda1
bash: mount/dev/sda1/mnt/sda1: No such file or directory
cody@cody-laptop:~$                     
cody@cody-laptop:~$ :confused:
cody@cody-laptop:~$ HELP HELP

---

### Post by deadflowr on 2013-02-08
Try this:

first :
```
sudo mkdir /mnt/sillyname
```

second:
```
sudo chown me:me /mnt/sillyname
```

third:
```
sudo mount /dev/sdaX /mnt/sillyname
```

see if that helps.

Change the X in the mount to whatever number the drive is.
Change the name to whatever floats your boat.
And change the permissions and ownership to whatever pleases you.

---

### Post by mapes12 on 2013-02-08
If the USB stick is of large capacity it may be formatted to exFAT by default. You will need extra packages to support this. Google: > Ubuntu exfat for a ton of guides.

Mark

---

### Post by dvsevin on 2013-02-08
it is formated in vfat

---

### Post by mapes12 on 2013-02-08
The vfat driver is used in linux to read and write FAT32 and FAT16 partitions. What capacity is the USB stick?

---

### Post by dvsevin on 2013-02-14
it a usb reader, i have 3 micro sd cards im trying to use 4,8,16gb and non work. the 4gig is a live disk for fiesty

---

### Post by schragge on 2013-02-14
From your output it looks like the space key on your keyboard doesn't work reliably ;). Try what **deadflowr** suggests above. And don't forget spaces between commands and their parameters.

---

