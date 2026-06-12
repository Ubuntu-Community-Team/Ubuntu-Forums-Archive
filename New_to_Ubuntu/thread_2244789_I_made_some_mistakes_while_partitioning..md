---
title: "I made some mistakes while partitioning."
date: 2014-09-18
forum: New to Ubuntu
---

### Post by manuel18 on 2014-09-18
Evening, when I was partitioning my HDD I made some mistakes  appearently, I thought I could solve them later, but it's becoming quite  difficult, I have 4 partitions and something called 'useless space',  the partitions are /boot of 27.94gb, /home that is 195.31gb, swap that  is 8gb and another one called '/' of about 172gb.. Oh and the 'useless  space' that now appears as unassigned of 61gb.


  Now the problem is, I want to make /home and '/' one partition, and  also combine the unasigned space there.. Is there a way to do so without  reinstalling? 


  Sorry for my bad english and thanks in advance.

EDIT: solved with ajgreeny's solution.

---

### Post by sotiris2 on 2014-09-18
Well there is a way but it will require some work on your part. If you pursue this option I strongly recommend you backup your non-replaceable data to an external disk. You will also require a live cd/usb media since you can't resize partitions that are in use. If you still have the cd/usb you installed ubuntu with it will do. Before we suggest a solution we need a more precise 'description' of the situation so if you could please post the output of terminal commands. ```
sudo parted -l
``` and ```
mount
```

EDIT: Also how much space is free in / partition?

---

### Post by manuel18 on 2014-09-18
I hope you understand, because it's in spanish.. So here it goes
First command line "sudo parted -l"
> Modelo: ATA ST1000DM003-1CH1 (scsi)
Disco /dev/sda: 1000GB
Tamaño de sector (lógico/físico): 512B/4096B
Tabla de particiones. msdos

Numero  Inicio  Fin     Tamaño  Tipo     Sistema de archivos  Banderas
 1      1049kB  106MB   105MB   primary  ntfs                 arranque
 2      106MB   84,0GB  83,9GB  primary  ntfs
 3      84,0GB  1000GB  916GB   primary  ntfs


Modelo: ATA SAMSUNG HD502HI (scsi)
Disco /dev/sdb: 500GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin     Tamaño  Tipo     Sistema de archivos  Banderas
 2      106MB   30,1GB  30,0GB  primary  ext4
 1      30,1GB  38,7GB  8594MB  primary  linux-swap(v1)
 3      105GB   315GB   210GB   primary  ext4
 4      315GB   500GB   186GB   primary  ext4



Second command line "mount"
> /dev/sdb4 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sdb3 on /home type ext4 (rw)
/dev/sdb2 on /boot type ext4 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=manuel)



There's about 165gb free on "/", and 61gb free on the not assigned space, I want to combine "/" and the not assigned space with "/home".. There's absolutely no problem on reinstalling ubuntu, haven't downloaded or stored anything in here yet, the main HDD has windows btw.. So, that's my case and thanks in advance.

---

### Post by ajgreeny on 2014-09-18
You do not appear to have an LVM partitioned installation, but do you have an encrypted disk or partitions?  I don't think you have from the parted output but can you confirm, please.

If you have neither you do not need a separate /boot partition, which would free up that partition and allow you another primary partition; only 4 primary partitions being possible on a msdos partition table formatted disk.

A screenshot of a gparted windowfrom the live DVD/USB showing /dev/sdb would be useful as it will show how partitions are arranged on disk, but I think as you have not actually used the system yet that a complete reinstallation would make most sense, choosing the "Something Else" option at partitioning stage, deleting all current partitions, then making a new one for / (root) of about 20GB, swap of 2 - 4GB, or, if you need to hibernate the system, swap of the same size as your total ram, and all the rest as /home.

If that is all gobledeegook to you, come back again and ask for more details, but as you mnaged to previously make those separate partitions I assume you know how to do that already.

---

### Post by manuel18 on 2014-09-18
> **ajgreeny said:**
> You do not appear to have an LVM partitioned installation, but do you have an encrypted disk or partitions?  I don't think you have from the parted output but can you confirm, please.

If you have neither you do not need a separate /boot partition, which would free up that partition and allow you another primary partition; only 4 primary partitions being possible on a msdos partition table formatted disk.

A screenshot of a gparted windowfrom the live DVD/USB showing /dev/sdb would be useful as it will show how partitions are arranged on disk, but I think as you have not actually used the system yet that a complete reinstallation would make most sense, choosing the "Something Else" option at partitioning stage, deleting all current partitions, then making a new one for / (root) of about 20GB, swap of 2 - 4GB, or, if you need to hibernate the system, swap of the same size as your total ram, and all the rest as /home.

If that is all gobledeegook to you, come back again and ask for more details, but as you mnaged to previously make those separate partitions I assume you know how to do that already.

Yeah, I think I'm gonna try that out.. But when I was partitioning on the Ubuntu installation I tried to delete previous partitions and I couldn't, I'll try again in a bit.. If I can't fix it, I'll post back here, thanks for the answer, have a good day!

---

