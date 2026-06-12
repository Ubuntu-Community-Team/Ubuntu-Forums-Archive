---
title: "[SOLVED] partitioned /home but....  not sure"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by scotcella on 2008-08-22
How do i know if all the documents and stuff will be sent straight to /home?

the fdisk -l output tells me

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a8eda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080       30401   195366465    5  Extended
/dev/sda5            6080       27963   175783198+  83  Linux
/dev/sda6           27964       30401    19583203+  82  Linux swap / Solaris
```

But it doesn't say anything like /home... I did a manual fresh install of the whole thing so there was nothing for me to backup or move to the new /home drive...

Anyway......  /home...  where is it? Did i do anything wrong?

I followed the instructions of [this]("http://forumubuntusoftware.info/viewtopic.php?f=7&t=242") (which was the most visual thing i found and easy to follow..... and seemed to be the only one that worked..  tried following psychocats but an error always came up even though everything was double checked over and over..

---

### Post by kpkeerthi on 2008-08-22
Can you post the output of ```
mount
``` command as well?

---

### Post by scotcella on 2008-08-22
output of

> mount

> /dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda5 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/china/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=china)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
china@china-desktop:~$ 


---

### Post by mcduck on 2008-08-22
Based on that, your setup is working justa s it should:

"/dev/sda5 on /home type ext3 (rw,relatime)"

All user home directories are inside /home, so everything you put in your own home dir will go to that partition.

---

### Post by kpkeerthi on 2008-08-22
> 
**[COLOR="Red"]/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)[/COLOR]**
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
[COLOR="Red"]**/dev/sda5 on /home type ext3 (rw,relatime)**[/COLOR]
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/china/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=china)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

Seems everything is OK. :)

Your documents and stuffs will be saved in /dev/sda5 which is mounted as /home.

---

### Post by ugm6hr on 2008-08-22
> **/dev/sda5 on /home type ext3 (rw,relatime)**

Looks like sda5 partition is mounted as /home. i.e. success.

Hence anything in /home will be written to the separate partition.

---

### Post by scotcella on 2008-08-22
Great thanks everyone,,  now i know this..  good thing i write everything down for future reference...

Took me ages to work out my partitioning.. i know i did a couple errors regarding the sizes..  but that can be fixed up later...

but i now get the whole concept of creating partitions manually...

thanks heaps again all!

---

