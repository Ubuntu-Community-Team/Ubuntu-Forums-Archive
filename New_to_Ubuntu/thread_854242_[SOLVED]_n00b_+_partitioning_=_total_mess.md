---
title: "[SOLVED] n00b + partitioning = total mess"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Varsch on 2008-07-09
Hello! I am as new as it gets since I've installed ubuntu today! 

So I have a brand new laptop with Vista pre-installed and when installing ubuntu I didn't understand much about the partitioning stage so I just played with it until it worked.

Now the OS is successfully installed but it seems I only have 945 MB of free space even though I have a 160 GB hard drive which should be completely empty apart from the system files. So my guess is that I only have access to a small partition. How do I make it so I can use my hard drive to its full potential?

There is nothing on this computer so I have no problem with formating it all and re-installing, except I have no idea how to do that and I'm afraid I would make the same mistake again!

Can anyone help me? Thanks a lot!

---

### Post by Darkchef on 2008-07-09
> **Varsch said:**
> Hello! I am as new as it gets since I've installed ubuntu today! 

So I have a brand new laptop with Vista pre-installed and when installing ubuntu I didn't understand much about the partitioning stage so I just played with it until it worked.

Now the OS is successfully installed but it seems I only have 945 MB of free space even though I have a 160 GB hard drive which should be completely empty apart from the system files. So my guess is that I only have access to a small partition. How do I make it so I can use my hard drive to its full potential?

There is nothing on this computer so I have no problem with formating it all and re-installing, except I have no idea how to do that and I'm afraid I would make the same mistake again!

Can anyone help me? Thanks a lot!

It sounds to me like you've made a small partition off the windows vista installation as grub cant detect that vista exists. To fix this you need to go into the installer again and choose the option "guided - use full disk". This should solve your problem. :D

---

### Post by mikewhatever on 2008-07-09
If the HDD is empty, have chosen to delete Vista? Can you post the outputs of the following from Applications>Accessories>Terminal:
```
sudo fdisk -l
df -h
```

---

### Post by meindian523 on 2008-07-09
It depends on whether you want Vista or not.If you do,first you will have to resize Vista's partition using Vista's tools.IIRC,those were found by right clicking My Computer>>Manage>>Disk management.
1]BACKUP everything before you do anything to your partitions.
2]Assuming you want to keep Vista,defrag atleast 2 times before attempting a resize.
3]Deleting and formatting partitions results in COMPLETE loss of data.

If you don't want Vista,it's quite simple.Just select use Entire Disk while installing.

EDIT:Also,please provide the info mike asks above.

---

### Post by Varsch on 2008-07-09
> **mikewhatever said:**
> If the HDD is empty, have chosen to delete Vista? Can you post the outputs of the following from Applications>Accessories>Terminal:
```
sudo fdisk -l
df -h
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b53eb06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       18721      160618+  82  Linux swap / Solaris
/dev/sda6           19170       19436     2144646   83  Linux
/dev/sda7           19437       19457      168651   82  Linux swap / Solaris
/dev/sda8           18722       19142     3381651   83  Linux
/dev/sda9           19143       19169      216846   82  Linux swap / Solaris

Partition table entries are not in disk order



Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             3.2G  2.2G  926M  71% /
varrun               1013M  104K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   84K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   38M  976M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      3.2G  2.2G  926M  71% /home/varsch/.gvfs
/dev/sda6             2.1G  2.1G     0 100% /media/disk

---

### Post by meindian523 on 2008-07-09
Ok,so you have removed Vista.What are you using /dev/sda1 for?That is the first primary partition on your disk?
EDIT:If you don't know,please post the results of 
```
mount
```

---

### Post by Varsch on 2008-07-09
When I tried using the entire disk during the install it didn't work (something when wrong and I started over). Now it seems that Vista isn't there anymore (when I restarted without the boot disk it told me "no OS found).

I don't care about keeping Vista, I'm all in for the ubuntu experience! ^_^

---

### Post by Varsch on 2008-07-09
> **meindian523 said:**
> Ok,so you have removed Vista.What are you using /dev/sda1 for?That is the first primary partition on your disk?
Honestly I have no idea, I didn't understand the partitioning stage of the installation so I just toyed with it until it worked and now I'm trying to fix it =)

---

### Post by meindian523 on 2008-07-09
Ok,please post the results of the command I gave above.

---

### Post by Varsch on 2008-07-09
/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/varsch/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=varsch)
/dev/sda6 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

---

### Post by meindian523 on 2008-07-09
Your problem is that you have not used the biggest partition on your disk,the first,primary one.
Now,what I plan to do is,to copy your entire / partition(the one you put on the 3.2 G partition) to the 150 GB one(the first primary one).
Either that,or you could go for a complete reinstall,and let the installer handle the work.Keep in mind though,you will learn some interesting concepts through the first way,considering how new you are.

---

### Post by kansasnoob on 2008-07-09
If you think you may have messed up Vista a totally fresh install would probably, IMO, be the easiest way to go if you have the Vista install disc(s).

Can you boot Vista at all?

The following guide is what you really needed to accomplish your original goal:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Of course if you decide to start fresh you can choose what size to make Vista when you install it, then use Gparted (aka Partition Editor from the Live CD to delete any and all remaining Ubuntu partitions) so you'd then just choose "Guided - use the largest continuous free space" from the installer and let Ubuntu do it's thing.

But if you can boot Vista just try that APC guide to properly resize Vista and start from there.

---

### Post by meindian523 on 2008-07-09
kansasnoob:
OP doesn' want Vista.Plus it's a pre-installed system.I doubt pre-installed systems hand over CDs of the OS,specially of Windows Vista.

---

### Post by Varsch on 2008-07-09
I think I'll try doing a fresh install of ubuntu and use the entire disk, since I'd rather not lose anything to a messy partitioning. I can't boot Vista and I don't really want to, so that's that!

I'll come back to tell you how it went! Thanks for everything! =D

---

### Post by meindian523 on 2008-07-09
Ok,if everything goes well,please mark the thread solved.

---

