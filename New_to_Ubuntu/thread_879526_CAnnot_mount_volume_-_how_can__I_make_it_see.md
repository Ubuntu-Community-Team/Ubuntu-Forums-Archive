---
title: "CAnnot mount volume - how can  I make it see"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Midgetprawn on 2008-08-04
It's an old issue I know and I have worked round it with

 [sudo mkdir /media/disk]
 [sudo mount /dev/scd0 /media/disk]

but when I reboot I have to do this again to mount my DVD / cdrom

Is there a way to make the computer accept changes permanently?

I have root privileges on a standalone on Hardy

---

### Post by Elfy on 2008-08-04
Add the partition to fstab

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Looks worse than it is :)

> #dev/sda5
UUID=000cf730-bffc-4ab6-bd8d-3305b4218fcf /media/data ext3 defaults 0 2this is a line I added to mount my ext3 data drive 

get the UUID from 
```
sudo blkid
```

If it's ntfs install the ntfs config tool and it can be done from system tools - ntfs config.

---

### Post by Midgetprawn on 2008-08-04
OK 
If I type mount iget
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kevin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kevin)
/dev/sda2 on /media/Crown Disc type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/scd0 on /media/disk type udf (ro)

scd0 is my DVD/CDrom drive which cannot mount automatically

 gksudo gedit /etc/fstab  values are

# /dev/sda5
UUID=39c5f886-057d-4e3c-a784-0769553cb439 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=3399d1d8-0579-46bf-b66a-8227db5f722c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660,user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

what can I do now?

---

### Post by Elfy on 2008-08-04
I'm sorry I misread your first post - your dvd should be mounting at boot - they are in the fstab or do you want it to mount in /media/disk? Not too sure now what you are trying to achieve.

If so I would try changing the fstab line to suit, but I don't know if it will like it...

> /dev/scd0 /media/[COLOR="Red"]cdrom0[/COLOR] udf,iso9660,user,noauto,exec,utf8 0 0

change cdrom0 to folder you have made.

---

### Post by Midgetprawn on 2008-08-04
Thanks Forestpixie
The drives are in Fstab but when I try to mount I get the message that I am not a privileged user. I found a way round this using the mkdir command hence the ambiguity. The computer does recognise the drive at boot up as I can insert live cd/DVD but it won't let me mount discs once it is running in desktop

I hope that summarises my problem

---

### Post by Elfy on 2008-08-04
That's a different problem then I would say - what permissions do they have, use a terminal change to /media and run 

```
ls -al
```

My cd has these permissions

> drwxr-xr-x   2 root    999 4096 2008-06-03 09:49 cdrom0

---

### Post by Midgetprawn on 2008-08-04
Hmmm Here is an interesting line

rwxrwxrwx  1 root              999     6 2008-04-02 20:32 cdrom -> cdrom0
drwxr-xr-x  2 root              999  4096 2008-04-02 20:32 cdrom0
drwxr-xr-x  2 root              999  4096 2008-04-02 20:32 cdrom1

---

### Post by Midgetprawn on 2008-08-04
Momentary pause to gather thoughts.....
I am not privileged to mount my DVD / CDROM media (that is the message)
I can mount and unmount it with the codes

sudo mount /dev/scd0 /media/disk

sudo  umount /dev/scd0 /media/disk

The Fstab file shows that both drives are recognised

I have permission according to the user/group option

Must I always mount media as root?

Is this the root of the problem......Ha HA (bad pun)

---

