---
title: "Permissions for partition on second hard disk"
date: 2016-02-26
forum: New to Ubuntu
---

### Post by sawfish2 on 2016-02-26
Hi all

I have just acquired a desktop system and installed Ubuntu 14.04 LTS. The system has two disk. One is a SSD disk where Ubuntu is installed. Then i added a second hard disk for storage of data and documents. I used  gparted to crate two partitions and used  
mkdir to create an empty library (mkdir /media/Arkivz). Then fstab to mount the drive and chown (sudo chown -R sawfish:sawfish /media/Arkivz) to change permissions. I can access the partition Arkivx and the other partition mount, but the permissions are set to root. I have serched and read many pages both here and at Ask Ubuntu at Stackexchange, but I dont seem to get to the bottom of it. How do i change permissions for the Datax partition?

From terminal using sudo blkid:
/dev/sda1: LABEL="Arkivx" UUID="646376ac-5c76-4992-928d-b99909adf083" TYPE="ext4" 
/dev/sda2: LABEL="Datax" UUID="94f6fba1-34ea-459d-9cbd-e123726db956" TYPE="ext4" 
/dev/sdb1: UUID="07fdcda2-27f6-4d52-a1d8-718f9f292ca6" TYPE="ext4" 
/dev/sdb5: UUID="9c09011e-8028-4316-8455-8de8cbbd38ab" TYPE="swap"

---

### Post by sandyd on 2016-02-26
Hi, can you post the output of
```

mount -l
ls -l /media
touch /media/Arkivz/testwrite
ls -l  /media/Arkivz

```

All commands should be run as your usual user unless otherwise noted.

---

### Post by sawfish2 on 2016-02-26
This is from terminal. Hope i did i right. Thanks for your time.
```

sawfish@desktop:~$ mount -l
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda1 on /media/Arkivz type ext4 (rw) [Arkivx]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=sawfish)
/dev/sda2 on /media/sawfish/Datax type ext4 (rw,nosuid,nodev,uhelper=udisks2) [Datax]

sawfish@desktop:~$ ls -l /media
total 8
drwxr-xr-x  5 sawfish sawfish 4096 Feb 25 21:43 Arkivz
drwxr-x---+ 3 root root 4096 Feb 26 15:36 sawfish

sawfish@desktop:~$ touch /media/Arkivz/testwrite
sawfish@desktop:~$ 

sawfish@desktop:~$ ls -l  /media/Arkivz
total 24
drwxrwxr-x 9 sawfish sawfish  4096 Feb 26 11:26 Dokumenter
drwxrwxr-x 4 sawfish sawfish  4096 Feb 25 21:43 Downloads
drwx------ 2 sawfish sawfish 16384 Feb 25 19:11 lost+found
-rw-rw-r-- 1 sawfish sawfish     0 Feb 26 15:54 testwrite
```

---

### Post by sandyd on 2016-02-26
From the output, you can write to /media/Arkivz, and the files created on the drive with your normal user are owned by you, so that should be fine.

The DataX partition is mounted by udisks2, probably because you mounted it from the file manager.

In keeping with the way you are mounting /media/Arkivz, give this a try
```

sudo mkdir /media/Datax
sudo umount /dev/sda2
sudo mount /dev/sda2 /media/Datax
chown -R sawfish:sawfish /media/Datax

```

If you want to mount it automatically at boot, see [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) and use UUIDs to create the line in fstab

Hope this helps!

---

### Post by sawfish2 on 2016-02-26
Thank you very much - it works perfect.

I can easily mount it with UUID and fstab (worked last time :rolleyes:)

So the bottom line is - When I mounted the first partition (Arkivx) I mistakingly thought I also had mounted the second partition, because it was on the same drive. Linux doesn't care about that and threat the partitions individually.

Funny i couldn't find a similar answer when I searched, because it must be basic stuff. Maybe I should write a small guide how to ad a hard drive with two (or more) partitions for beginners like my self.

---

