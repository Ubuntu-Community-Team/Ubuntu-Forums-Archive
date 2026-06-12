---
title: "noatime - no effect"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by bobzxr on 2012-08-15
Added the noatime in fstab in the right place. However, it does not have any effect since whenever i create or access a file, time stamps are made.

---

### Post by wheeze on 2012-08-15
Silly question but, have you rebooted since adding that to fstab?

---

### Post by bobzxr on 2012-08-15
> **wheeze said:**
> Silly question but, have you rebooted since adding that to fstab?

Yes, several times.

---

### Post by wheeze on 2012-08-15
Can you post the contents of your fstab file?

---

### Post by bobzxr on 2012-08-16
> **wheeze said:**
> Can you post the contents of your fstab file?

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a55125ea-560b-4122-ba31-c2e86ddbffe2 /               ext4    noatime,discard,errors=remount-ro 0       1
```

---

### Post by NikTh on 2012-08-16
Hi , 
can you post the output of 
```
sudo blkid
```don't you have a swap partition ? 

Did you try **realtime** instead **noatime** ? 
Thanks

---

### Post by bobzxr on 2012-08-16
> **NikTh said:**
> Hi , 
can you post the output of 
```
sudo blkid
```don't you have a swap partition ? 

Did you try **realtime** instead **noatime** ? 
Thanks

```
/dev/sda1: UUID="f90743e7-37f9-4dea-a1fd-d6c9084da5b2" TYPE="ext4"
```

I do not have a swap partition.

Just to clarify things: by adding noatime to fstab, I should not see the date and time any file was accessed and modified under nautilus if I right click on the file and then on properties. 

Right?

Also in terminal if I write ```
ls -l
``` I can see which file I downloaded when.

I use Ubuntu on both my notebook and desktop, they have very different hardware, and I have the same on both.

update: I did not try relatime, because it does not force a system to not use time stamps.

---

### Post by NikTh on 2012-08-16
Hi , 
take a look  
[http://askubuntu.com/questions/2099/is-it-worth-to-tune-ext4-with-noatime](http://askubuntu.com/questions/2099/is-it-worth-to-tune-ext4-with-noatime)
[http://ubuntuforums.org/showthread.php?t=1927754](http://ubuntuforums.org/showthread.php?t=1927754)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)
hopefully above links will clarify things better.
Thanks

---

### Post by bobzxr on 2012-08-17
> **NikTh said:**
> Hi , 
take a look  
[http://askubuntu.com/questions/2099/is-it-worth-to-tune-ext4-with-noatime](http://askubuntu.com/questions/2099/is-it-worth-to-tune-ext4-with-noatime)
[http://ubuntuforums.org/showthread.php?t=1927754](http://ubuntuforums.org/showthread.php?t=1927754)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)
hopefully above links will clarify things better.
Thanks

I overlooked that it is only works for read operations. My bad, but thanks for your time!

---

