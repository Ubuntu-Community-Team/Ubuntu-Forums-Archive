---
title: "[SOLVED] gparted mounting fstab etc etc"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by pooper on 2008-11-21
Hi just recently acquired a new windows pc, to start off i reformatted the 40gb hd to 1gb swap and 5gb ext3 as / for installation of xubuntu. I left the 3gb fat32 recovery partition alone. that left me with around 30gb of hd unused which at the time i didn bother formatting...
now xubuntu is up and running great i installed gparted to format that unused 30gb to fat32 so its always accessible by other os apple windows..
i did this while running xubuntu on that same hd and gparted let it happen etc, and its all done, but i read you should do it when the hd isnt being used for example run a gparted cd. but it worked anyway..
now im just wondering how to mount that partition so i can use it! i've been able to mount it but not had permission to do anything with it, I've looked at settings, including fstab but cant piece it all together. 
any help on getting it mounted with permission to write to it would be appreciated. also i would like this partition automatically mounted at start up to. 
thanks, and sorry for my long winded explanation.

---

### Post by sisco311 on 2008-11-21
open a terminal and post the output of:
```
sudo blkid
```and```
cat /etc/fstab
```

---

### Post by pooper on 2008-11-21
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: LABEL="PRESARIO_RP" UUID="5F25-7B73" TYPE="vfat" 
/dev/sda2: TYPE="swap" UUID="81088fea-86ea-4fc5-af4f-fc358579580f" 
/dev/sda3: UUID="fa8f1671-b13e-4afb-96ab-7c46c62853e1" TYPE="ext3" 
/dev/sda4: LABEL="shared" UUID="4927-40BE" TYPE="vfat" 



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fa8f1671-b13e-4afb-96ab-7c46c62853e1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=81088fea-86ea-4fc5-af4f-fc358579580f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#partition 4
/dev/sda4	/mnt/shared	vfat	drwxrwx--- 7 bodhi users	0	0 



at the end of fstab you can see my attempt of adding the partition

---

### Post by sisco311 on 2008-11-21
add this to the fstab> UUID=4927-40BE /mnt/shared vfat defaults,umask=002,gid=46 0 0
and make sure that the mount point exist:
```
sudo mkdir /mnt/shared
```

mount the partition:
```
sudo mount -a
```
(the partition will be mounted automatically upon next boot)

---

### Post by pooper on 2008-11-21
ok thanks thats done the job...

I got the other settings for the line in fstab in the fstab guide on here!? dont understand, but im happy it works. 

Thanks alot!

---

### Post by sisco311 on 2008-11-21
You're welcome.

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

