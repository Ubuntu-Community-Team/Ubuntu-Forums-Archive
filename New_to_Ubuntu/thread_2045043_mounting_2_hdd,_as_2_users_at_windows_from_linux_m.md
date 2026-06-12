---
title: "mounting 2 hdd, as 2 users at windows from linux machine"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by bremenpl on 2012-08-20
Hello!
Im having a problem mounting 2 drives that are connected to my raspberry pi on my windows pc.
On Rpi i have samba installed.
I have 2 users.

to mount the drives, i use sgtartup script (/etc/init.d/mountdisk):
```
#! /bin/sh
# /etc/init.d/blah

sudo mount -o uid=pi,gid=pi /dev/sda1 /home/pi
sudo mount -o uid=sonia,gid=sonia /dev/sdb1 /home/sonia

exit 0
```

I use that coz even though I edit the /etc/fstab file, it doesnt mount anything on startup for me:
```
proc            /proc           proc    defaults          0       0
/dev/mmcblk0p1  /boot           vfat    defaults          0       0
/dev/mmcblk0p2  /               ext4    defaults,noatime  0       0
/dev/sda1       /home/pi        ext3    rw,defaults       0       0
/dev/sdb1       /home/sonia     ext3    rw,defaults       0       0

# a swapfile is not a swap partition, so no using swapon|off from here on, use  dphys-swapfile swap[on|off]  for that
```

I have the drives mounted, i can see them when login by ssh.
in home folder there are folder pi and sonia, they containh hdd1 and hdd2.

On windows I mount 1st drive by adress:
```
\\192.168.0.XXX\pi
```
and its being mounted corectly, I login with user pi.

Now, when i try to mount second drive by going:
```
\\192.168.0.XXX\sonia
```
An window opens for me to login. I tried login in with users pi and sonia, in both situations i got an error message:
> Current web folder is currently mapped using other username and password.
To connect using other username and password all mappings to this web region has to be unmounted
Something like that im translating it, forgive me my english.

So basicaly i dont understand it, coz i am trying to mount 2 separate drives.

I solved this problem by creating 2 subfolders in folder pi. loging with user pi. But in that case, on maped drives i see the storage space of my Rpi sd card, not my drives.
Also, disks not always mount in the same order, sometimes hdd1 is (S:) and hdd2 is (R:) (I am mounting them as S and R). And sometimes way around.


I would realy aprichiate if someone could explain me how to do this properly in a nub way.
Cheers.

---

