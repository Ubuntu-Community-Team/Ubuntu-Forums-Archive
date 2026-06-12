---
title: "Allow executing file as program unchecks and a few general questions."
date: 2013-03-09
forum: New to Ubuntu
---

### Post by Eyeball114 on 2013-03-09
Ubuntu server 12.10
Ubuntu Desktop GUI (not xubuntu, I mis-clicked :/)



I am trying to launch my minecraft servers but the check mark for executing keeps un-checking. I have all 4 individual servers in their own folder in a 1TB HDD NTSF. 
I copied a folder to the desktop where it allowed me to keep the check mark checked. I than clicked my start.sh. The terminal flashes open than closes instantly. 


How can I get the check mark to stay checked when the info is on the storage drive?
Do I need to do configure anything on my HDD? 


Any help is appreciated.

---

### Post by papibe on 2013-03-09
Hi Eyeball114.

NTFS doesn't support Linux permissions. The way you deal with them is in the mount options.

Either the option 'default_permissions' or dmask=022 should work.

How are you mounting the partition?

Regards.

---

### Post by Eyeball114 on 2013-03-09
I am 100% new to linux. Its fascinating to me and I'd love to learn this and go to school for it. 

I havent done anything, to my knowledge, as far as mounting. I installed ubuntu than plugged in my 1TB HD and if I right click on that it does say unmount, so I am assuming it has mounted itself in some sort of default fassion?
I had ubuntu on this SSD previously and had reformatted it on my pc. Than installed ubuntu from a usb through uefi. Is their perhaps a guide of "first things to do when adding a second HDD for dummies" haha.

---

### Post by papibe on 2013-03-09
Let's see what are the mounting options that are being used by default. When you have access to the content of your disk, open a terminal and run:
```
mount -l
```
Please post back your results.
Regards.

---

### Post by Eyeball114 on 2013-03-09
```
zach@vbox:~$ mount -l
/dev/mapper/vbox-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
cgroup on /sys/fs/cgroup type tmpfs (rw,relatime,mode=755)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu type cgroup (rw,relatime,cpu)
cgroup on /sys/fs/cgroup/cpuacct type cgroup (rw,relatime,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,relatime,perf_event)
/dev/sdb1 on /boot type ext2 (rw)
gvfsd-fuse on /run/user/zach/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=zach)
/dev/sda2 on /media/zach/BDA5-8156 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


```

---

### Post by papibe on 2013-03-09
I believe this is the one:
```
/dev/sda2 on /media/zach/BDA5-8156 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
```
The option dmask looks OK. You should have read, write and execute permission on all files on the disk.

Could you post the result of this commands?
```
ls -l  /media/zach/BDA5-8156
```
Regards.

---

### Post by Eyeball114 on 2013-03-09
```
zach@vbox:~$ ls -l  /media/zach/BDA5-8156
total 64
drwx------ 11 zach zach 16384 Mar  9 13:27 MindCrack
drwx------ 11 zach zach 16384 Mar  8 20:29 Tekkit-Server
drwx------  7 zach zach 16384 Mar  8 20:29 Unlimited
drwx------  9 zach zach 16384 Mar  8 20:29 Voltz
zach@vbox:~$ 


```


Would formatting the HDD to fat32 or exfat be a solution? Its only about 6gb in total of information it would be easy enough to put onto a usb real quick.

---

### Post by papibe on 2013-03-09
> **Eyeball114 said:**
> ```
zach@vbox:~$ ls -l  /media/zach/BDA5-8156
total 64
drwx------ 11 zach zach 16384 Mar  9 13:27 MindCrack
drwx------ 11 zach zach 16384 Mar  8 20:29 Tekkit-Server
drwx------  7 zach zach 16384 Mar  8 20:29 Unlimited
drwx------  9 zach zach 16384 Mar  8 20:29 Voltz
```
There you go, every file has execute permission (x). You should be able to execute any file on the disk.

> **Eyeball114 said:**
> Would formatting the HDD to fat32 or exfat be a solution? Its only about 6gb in total of information it would be easy enough to put onto a usb real quick.
Unfortunately no. But if you are willing to reformat, try a truly Linux filesystem: ext4.

Let us know how it goes.
Regards.

---

### Post by Eyeball114 on 2013-03-09
Thanks for all the help. Ill let you know how it goes. 


Also I just realized this. I have already had these servers running off the HDD using ubuntu server in the past. The only thing new here is the installation of ubuntu server onto the ssd, not the HDD. If the the format works, great but I wonder why it worked than but not now :/ We shall see.

---

### Post by Eyeball114 on 2013-03-09
Format to ext4. Do I need to set anything up after formatting? I can't write to the HDD though. Says I am not the owner.

---

### Post by papibe on 2013-03-09
Try this:
```
sudo chown -R zach:zach /media/zach/BDA5-8156
```
Regards.

---

### Post by Eyeball114 on 2013-03-09
No file exists. I have already reformatted the drive. Its ext4 now. The partition type says HPFS/NTSF and the contents says Ext4. Should I change the partition type to something else?

---

### Post by Eyeball114 on 2013-03-11
So I have formatted the HDD to ext4, updated java, set permissions to launch as a program for the .sh and the .jar. Double click the .sh and the terminal flashes open than closed still. Anyone have an idea of why this isnt staying open?

---

### Post by papibe on 2013-03-11
I would start running it on the terminal until you know it is running properly.

Right now, you don't know if it is failing, or a task is directed to the background without you knowing it.

Regards.

---

