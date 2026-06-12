---
title: "Reinstalling Ubuntu"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by bower4311 on 2012-08-05
Hello,

I'm very new to Ubuntu, but have a decent understanding of computers.  My cousin just installed Ubuntu on my computer. He used a partition so I believe my OS is on a small GB partition and there is a larger one for all of my files. Right now I have a folder with 110 GB of files located in /home/adam. I do not want to lose these files if I re-install. I'm pretty sure that they are on a separate partition.

1.) How do I know this?
2.) Is there an easy way to re-install Ubuntu, I screwed it up trying to install a virtual machine?
3.) What is the best way to go about this?

I'm running Ubuntu 12.04LTS on a new core i5 computer I built.

Thank you in advance.

---

### Post by egeezer on 2012-08-05
If you have a LiveCD of any Ubuntu, or better yet of PartedMagic, you can run it live in your CD or DVD drive and mount any partition on your installed version.  That will tell you what files are where.  ETA: A quicker way would be to run Gparted (look in System or system tools) and you can see what partitions are on your HDD.  That will tell you if you cvan reinstall and retain your existing /home partition.

---

### Post by dFlyer on 2012-08-05
Just start diskutilities from the dash and click on the drive you want to examin. It will list your partitions and there names.

---

### Post by ajgreeny on 2012-08-05
Or use the command ```
mount
``` in terminal.
That will give output something like:-
```
[COLOR=Red]/dev/sda1 on / type ext4 (rw,errors=remount-ro)[/COLOR]
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
[COLOR=Red]/dev/sda2 on /home type ext4 (rw)[/COLOR]
```with the two lines in red showing here as the root and home partitions.

---

### Post by bower4311 on 2012-08-05
This is the text I get when I use 'mount'



/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
vmware-vmblock on /run/vmblock-fuse type fuse.vmware-vmblock (rw,nosuid,nodev,default_permissions,allow_other)
gvfs-fuse-daemon on /home/adam/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=adam)

Here is what I get when I run Disk Utility

They should be attached, not sure how exactly it looks once I attach them.

---

### Post by NikTh on 2012-08-05
Hi , 
it seems you don't have a separate /home partition. /home partition is IN /root partition . 
If you try to reinstall Ubuntu you will lose ALL your files. 
You must first backup (copy) all your important files to another disk (maybe to an external) or maybe to this space I can see 484GB free. 
Then you will install Ubuntu from scratch and at the end you will transfer again your files inside your new /home partition. 

So first you must add a new partition (from disk utility) on this free space . Make the partition little bigger . If your files are 110GB , make the partition 120GB. Then copy all your important files to this new partition and then re-install Ubuntu (from CD). 

If you don't want to face this situation on future re-installations , create a separate /home partition , while installing Ubuntu . You must be little careful when you do the partitioning . 
Read here the section "While Installing Ubuntu" . [http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/)

Thanks

---

### Post by mansonfan78 on 2012-08-05
You could also follow the instructions here:  [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)  to create a separate home partition and move all your files to it BEFORE you reinstall.  Then, when you reinstall just mount that as /home (and uncheck "format").  Just make sure you use the same username and password when it asks you during install.

---

### Post by bower4311 on 2012-08-28
I moved my files to an external then reinstalled ubuntu. Does it look like I did it right?

---

### Post by mansonfan78 on 2012-08-28
> **bower4311 said:**
> I moved my files to an external then reinstalled ubuntu. Does it look like I did it right?


Looks right to me.  Does everything work?

---

