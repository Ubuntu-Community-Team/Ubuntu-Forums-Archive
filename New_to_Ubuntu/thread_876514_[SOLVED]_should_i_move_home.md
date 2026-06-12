---
title: "[SOLVED] should i move /home?"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by GrnFrag on 2008-07-31
I've got Hardy installed and running well (I think), and I'm loving it.   I want to move more of my toys/stuff from Windows, so i'm adding a second disk.
so my question is "is this feasible?  or should i just nuke and pave?" i want to move /home from an extended partition on HDA1 to a primary on HDA2. i figured out how to copy the files over, no brainer.   
What i'm having probs with is how do i tell Ubuntu that /home is now over there??

Thanks.   And Thanks again to all of you for creating this wonderfull alternative to WinHosed.   I'm impressed (and a bit overwhelmed) with the amount of information available!!
:popcorn:

---

### Post by collinp on 2008-07-31
As a last resort, there is an option when you install ubuntu to change the default partition some of the directories are on, so you should do that, but as i said, as a last resort.

---

### Post by GrnFrag on 2008-07-31
ty for your quick answer.    i'm just going to copy the /home folder to it's new location then reinstall.   because i'm going to be changing parition sizes and physical locations, i'm sure it's the best option.    

but i got to read these boards all day, trying to figure it out   LOL

---

### Post by sstvinc2 on 2008-07-31
I'm pretty sure gparted can handle this kind of stuff.  If you're going to nuke the system anyway, maybe try booting the live CD and reconfiguring using gparted.  Worth a try.

I mean, as long as /etc/fstab knows where /home is (which gparted will adjust appropriately), it shouldn't really matter if it's moved to a different disk/partition or not.  I could be wrong, though.

---

### Post by ibuclaw on 2008-07-31
You'd have to format the second hard-drive with gparted.

Then copy the entire contents of your /home folder over to it (don't include the top folder "home") and make sure that all permissions are set right.

Then make a line in your fstab folder to change the current /home partition to the new one.

use:
```
sudo blkid /dev/sdb1
```
to get the UUID number of your drive and put in the line:
```
UUID=example-1234-5678-90ab /home ext3    relatime 0    2
```
inside your /etc/fstab file.

And reboot to commit the set changes.

It is not as difficult as it sounds, but it is easier to explain if you have the disks and are ready to go :)

---

### Post by arpanaut on 2008-07-31
Here's a good guide for doing about the same thing you want... without having to reinstall.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Lotsa other good info on that site too!

---

### Post by GrnFrag on 2008-07-31
Thank you all very much.  In search of the easy way to do this, i've come across several options for copying but not much about bulk .     what about this?

 mount --move olddir newdir


according to man pages, this would do it all for you, even copying the files if i read correctly.

---

### Post by GrnFrag on 2008-08-01
ok i booted off LiveCD, gparted did copy /home to sdb1. 
according to
 ```
every1@MoonRock:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
**/dev/sdb1 on /home type ext3 (rw,relatime)**
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/every1/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=every1)
every1@MoonRock:~$ 
```
looks right, eh?   but.....fstab
> # /dev/sda3
UUID=44a8949a-e314-40e4-9636-01136b446696 /home           ext3    relatime        0       2
And gparted (loaded from my install, not live cd, correctly shows SDB1 as /home.   so i just update fstab?   then i should be safe to remove the parition?   i'm going to resize / hehehhehe   eventually this will replace my winders box   :)   take that bill:shock:

i just noticed that the uuid is correct for SDB1, it's just called sda3.......i backed up and am changing the name....

---

