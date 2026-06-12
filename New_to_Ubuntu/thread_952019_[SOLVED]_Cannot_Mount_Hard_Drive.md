---
title: "[SOLVED] Cannot Mount Hard Drive"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by SILLAT on 2008-10-18
Hello .. i hav a Pc running Ubuntu Hardy 8.04 with 2 hard drive, my IDE cable Died on me a few minutes ago so i replaced it a while back but after replacing the IDE cable an logged in i notice Ubuntu see 's my second hard drive but it wont mount it . .
When i double click on the Drive i get "you are not privilege to mount this  volume " so i thought it was a root thing so i login as root an did the same an it said "Cannot Mount Volume" Mount Point /Media/Disk does not Exist.
How can i get Ubuntu to mount back my second drive as usual??
my previous settings was set to automatically mount my HDD at  boot an run fsck .

---

### Post by Ryadt on 2008-10-18
Try ```
sudo mkdir /Media/Disk
```

---

### Post by SILLAT on 2008-10-18
I have a lota Multimeadia Files on my HDD
if i run  sudo mkdir /Media/Disk will it interfere with my files?

---

### Post by Ryadt on 2008-10-18
> **SILLAT said:**
> I have a lota Multimeadia Files on my HDD
if i run  sudo mkdir /Media/Disk will it interfere with my files?
How will it interfere? 
It's only creating a directory.

---

### Post by SILLAT on 2008-10-18
i jus ran sudo mkdir /Media/Disk an this what i get: 
mkdir: cannot create directory `/Media/Disk': No such file or directory

---

### Post by jerome1232 on 2008-10-18
You probably just need to create an fstab entry for it.

first figure out which device it is by listing out all drives/partitions, then make a dir where you want it mounted, edit your fstab and then mount it.
```
sudo fdisk -l                    # lists all disks and partitions and their /dev path
sudo blkid                       # lists all partitions and their uuid, figure out which uuid relates to your drive
sudo mkdir /media/mountpoint     # You can change this to whatever, traditionaly /mnt and /media are use for mounting. /media shows up on you desktop
gksu gedit /etc/fstab
# for this I'll pretend your partition is /dev/sdc1, it's uuid is goobly-gook and it's formated ext3 so add a line like this, change it according to needs
     this is the example fstab entry
# /dev/sdc1
UUID=goobly-gook /media/mountpoint ext3 defaults 0 2
      end example fstab entry
# save then try and mount it
sudo mount -a
```

---

### Post by Ryadt on 2008-10-18
Try ```
sudo mount -a
```

---

### Post by SILLAT on 2008-10-18
Hey jerome1232 thnx for the Help !! 
your Post did the Trick !!
Ryadt thnx for the Quick Reply to my thread 
My 2nd HDD is up and Running 

Thnx again Guys ...

---

