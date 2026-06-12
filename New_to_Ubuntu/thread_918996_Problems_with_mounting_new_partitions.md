---
title: "Problems with mounting new partitions"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by hesjnet on 2008-09-13
I'm trying to mount my new partition that i made with gparted but when I mount the drive it is read-only for my user. It belongs to root... how can i change this?

What I am trying to do is to have a partition where I'll put my files, maybe also home folder, separate from the Xubuntu OS.

I used these commands in terminal:

mkdir /mnt/backup/
sudo mount /dev/sda2 /mnt/backup

If it is possible to have my new partition show up mounted just as a usb-thumbstick or an external drive, it would be great :)

Thanks guys!

---

### Post by hubie on 2008-09-13
Did you add the partition to your /etc/fstab file?  The paritions (and disks) listed in that file get mounted automatically.

If you do have an entry in fstab for it, could you post what it is?

---

### Post by hesjnet on 2008-09-13
This is whats in my fstab file:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cfe01e42-2a6b-48ed-a36b-dc4240353e61 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1b06909d-0fe4-40c1-8da9-b6460fc37c92 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I haven't done anything in this file. What should I do?

---

### Post by hesjnet on 2008-09-14
bump?

---

### Post by bumanie on 2008-09-14
Post the output of > sudo fdisk -luPoint out which partition you wish to add to /etc/fstab - from the earlier post, it looks as though it will be sda2 - but please confirm.

---

### Post by Bucky Ball on 2008-09-14
```
mkdir /mnt/backup/
sudo mount /dev/sda2 /mnt/backup


```You looking to have this automounted at boot? If so, copy and paste this:

**sudo blkid**

... in a terminal and post here. :)

---

### Post by hesjnet on 2008-09-14
Thanks for all your help guys. You're great!

sudo blkid gives me:

/dev/sda1: UUID="cfe01e42-2a6b-48ed-a36b-dc4240353e61" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="1b06909d-0fe4-40c1-8da9-b6460fc37c92" 
/dev/sda2: UUID="3132eaf0-f368-43c7-bbc2-5c6e22f96040" SEC_TYPE="ext2" TYPE="ext3" 

Yes. I want to mount the sda2 partition on startup. When I try to open gparted I get an errormessage:

"Could not mount 140G unit
org.freedesktop.hal.storage.mount-fixed auth_admin_keep_always <-- (action, result)."  

I guess this is the problem.

And I'm running Xubuntu.

---

### Post by hesjnet on 2008-09-14
pal@pal-laptop:~$ sudo fdisk -lu 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00079ab3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   100438379    50219158+  83  Linux
/dev/sda2       100438380   374796449   137179035   83  Linux
/dev/sda4       374796450   390716864     7960207+   5  Extended
/dev/sda5       374796513   390716864     7960176   82  Linux swap / Solaris

---

### Post by Bucky Ball on 2008-09-14
You need to be in the correct directory to do this. Copy and paste this:

**cd /media**
[I]
Then[/I] create your mount points for your partitions. Then go for not quite what you had before ...

```
mkdir /mnt/backup/
sudo mount /dev/sda2 /mnt/backup
```but try changing this to:

```
sudo mkdir /mnt/backup/
sudo mount /dev/sda2 /mnt/backup
```That mounts it for the moment, but when you reboot, you will need to do it again ... so,

Just fill me in; what you have here is not mounted through the drop down menu 'Places'? Is there something not mounting? You have in effect two partitions here; the other two are swap and Ubuntu. Which one is not mounting?

---

### Post by hesjnet on 2008-09-14
It doesnt show in my "Places" no, but this is not necessary for me.

After doing the commands:
```

sudo mkdir /mnt/backup/
sudo mount /dev/sda2 /mnt/backup
```

It gets mounted but the root is set as the owner, so I cannot write to the folder, only read..

the two others are working perfectly. I only want to have access to my newly mounted partition. And it would be great if I didn't have to mount it after every reboot.

Thanks again.

---

### Post by Bucky Ball on 2008-09-14
[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

There is much more info out there. Do a search for:

**automount ubuntu hardy**

:)

---

### Post by hesjnet on 2008-09-14
thanks for the resource link. It was quite thorough, so I'll have to check that tomorrow. 

But for now, could somebody please help me with the write permissions?

When I manually mount the partition, I do this with sudo. This gives root the ownership and rw rights to the mount. How can I, in terminal give myself (my user) read AND write privileges?

---

### Post by Bucky Ball on 2008-09-14
Open a terminal and copy/paste:

**sudo nautilus**

This should open nautilus as root. Right click on the correct partition and set the permissions there. This will not work with FAT drives as they need to have permissions set at boot. :)

---

### Post by hesjnet on 2008-09-15
It worked! Thanks!

---

