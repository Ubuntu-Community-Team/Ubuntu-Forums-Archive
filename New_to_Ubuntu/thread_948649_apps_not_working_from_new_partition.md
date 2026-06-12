---
title: "apps not working from new partition"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by nevermind86 on 2008-10-15
I have a problem, I have put /home on a seperate partition and everything works fine from it. I have recently allocated more space from a hard drive and wanted to mount the partition as the /home partition is mounted. I have mounted the new partition, but applications and games do no work from it. when i copy the apps/games to /home they work, so i am assuming it is a permissions error? I have tried to use sudo nautilus to change it, but doesnt help, so it is a problem with my fstab i presume? **I want all the permissions of the /home partition on my new drive**. here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sda1
UUID=21af1d91-098e-4e1a-9ff5-e9a07dbbbee9  /               ext3         relatime,errors=remount-ro  0  1  
# /dev/sda3
UUID=82a6ab26-b4ae-4a53-a5ef-ab23ccc0ef86  /home           ext3         relatime                    0  2  
# /dev/sda2
UUID=6d30a15c-2a45-4bf5-9498-ce8460fd2073  none            swap         sw                          0  0  
/dev/hda                                   /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/hdb                                   /media/cdrom1   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sda1                                  /media/sda1     ext3         defaults                    0  0  
**/dev/sda6                                  /home/tom/sata377gig     ext3         defaults	    0  0**

the drive /home/tom/sata377gig is the one i want with full permissions to run files, at present i can access it fully, but not run any files/games from it. please help! i am sure it is simple...

---

### Post by jamesrl on 2008-10-15
change to 

```
/dev/sda6 /home/tom/sata377gig ext3 defaults,umask=227 0 0
```
and it will give 
user and group read/execute permissions
and other no permissions.
Basically umask is the inverse of chmod (as you are taking away priveleges rather than giving priveleges).

See ```
man chmod
man fstab

```

---

### Post by nevermind86 on 2008-10-15
Thanks for the swift reply! It works cheers :)

---

### Post by nevermind86 on 2008-10-17
Sorry! it doesnt seem to work anymore :S

When I rebooted, it doesnt seem to work, says I have invalid permissions to mount the parititon "sata 377gig" and the folder i created to mount it to is empty :( (/home/tom/sata377gig)

when I went back to the old fstab file, it mounts and the folder I mounted it to is now full of the files on the partition mounted to it. But files dont work off it :(

I assume it is some more permissions errors, I want the parition "sata 377gig" to mount at boot to the dir /home/tom/sata377gig with full read /write permissions for my user "tom", t**he same as the /home/tom folder is granted**. I have looked through the permissions wiki and still doesnt work. Please help! Previous advice only worked until I restarted! 

current Fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sda1
UUID=21af1d91-098e-4e1a-9ff5-e9a07dbbbee9  /               ext3         relatime,errors=remount-ro  0  1  
# /dev/sda3
UUID=82a6ab26-b4ae-4a53-a5ef-ab23ccc0ef86  /home           ext3         relatime                    0  2  
# /dev/sda2
UUID=6d30a15c-2a45-4bf5-9498-ce8460fd2073  none            swap         sw                          0  0  
/dev/hda                                   /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/hdb                                   /media/cdrom1   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sda1                                  /media/sda1     ext3         defaults                    0  0  
[B]/dev/sda6                                  /home/tom/sata377gig     ext3         defaults	    0  0
[/B]

---

