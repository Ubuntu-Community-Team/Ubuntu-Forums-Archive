---
title: "HIIBERNATION error message"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-22
Hello, 

When I hibernate my sys, i get this message:
drm_sysfs_suspend
swsusp: Cannot find swap device, try swap -a 
after that a login window (not the one we see during reboot) will come out. 
What is the problem and how to solve this problem

---

### Post by prshah on 2008-05-22
> **wariskampar said:**
> Hello, 

When I hibernate my sys, i get this message:
drm_sysfs_suspend
swsusp: Cannot find swap device, try swap -a 
after that a login window (not the one we see during reboot) will come out. 
What is the problem and how to solve this problem

Looks like you either don't have a swap partition/file, or that it is simply not activated.

Open a terminal, Applications-Accessories-Terminal, and post the output of ```
sudo fdisk -l
```

---

### Post by wariskampar on 2008-05-22
i have SWAP file for sure but maybe it is not activated. How to do it?
Btw, this is my fdisk -l
aznan@aznan-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1883    15125166    7  HPFS/NTFS
/dev/sda2            1884        9729    63022995    f  W95 Ext'd (LBA)
/dev/sda5            1884        3165    10297633+  83  Linux
/dev/sda6            3166        7774    37021761   83  Linux
/dev/sda7            7775        9561    14354046   83  Linux
/dev/sda8            9562        9729     1349428+  82  Linux swap / Solaris
aznan@aznan-laptop:~$ 

Hope can guide me through the process

---

### Post by wariskampar on 2008-05-22
i think you may want to look at my fstab as well:

aznan@aznan-laptop:~$ whatis fstab
fstab (5)            - static information about the filesystems
aznan@aznan-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=a3972a39-4b18-43b1-9848-f5788689ccbf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=177befd4-be3f-4cb6-bc23-0357a348b971 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#/dev/nameofdisc1
/dev/sda5 /media/sda5 ext3 defaults 0 2
#/dev/nameofdisc2
/dev/sda6 /media/sda6 ext3 defaults 0 2 
aznan@aznan-laptop:~$

---

### Post by prshah on 2008-05-22
> **wariskampar said:**
> ```

/dev/sda8            9562        9729     1349428+  82  Linux swap / Solaris
aznan@aznan-laptop:~$ 
```


Yes you have swap... give the command ```
sudo swapon -a
``` to activate it .. post back error messages if any!

Once activated, it will _remain_ activated, even across reboots.

---

### Post by wariskampar on 2008-05-22
ok, actually i swapon using gparted(right click menu at the partition). anyway when i hibernate, all open windows gone after start up. so i suspect swap partition still malfunction. when i check in gparted, can see traingle icon beside the swap partition. so i change the uuid in etc/fstab to uuid i get with this code sudo vol_id -u /dev/sdb5. now im going to test again to see whether its work or not. i also do as you said. here is what i get in terminal

aznan@aznan-laptop:~$ sudo swapon -a
swapon: /dev/sda8: software suspend data detected. Reinitializing the swap.
Setting up swapspace version 1, size = 1381810 kB
LABEL=ID_FS_USAGE=oth, UUID=52a73e62-30e3-492b-8b03-43ffa7e5aa7f
aznan@aznan-laptop:~$

---

### Post by wariskampar on 2008-05-22
now my swap partition is fully functioning (a attach gparted screenshot because still need your confirmation though). However, when i reboot, all my previous open windows(Firefox) do not get restored. Hmm, is this normal or only happen to Firefox because it get "Restore Previous Tab".

---

### Post by tamias on 2008-06-10
If hibernating your laptop works but, upon resuming, the computer reboots and does not resume from the hibernation point, the following information should be of use (taken from the Ubuntu forums):

Make sure the swap drive UUID is correct in  /etc/initramfs-tools/conf.d/resume. Sometimes it is not updated. You can obtain the UUID of the swap drive using the following command: vol_id /dev/hda3 (or your swap drive id)

Then run sudo update-initramfs -u

This will update the initrd.img file in the /boot directory. This will generate a new image that is aware of the swap drive location for resume purposes.

The drm_sysfs_suspend error is not actually an error. It's just a harmless bug in Ubuntu, which the devs are fixing right now: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234239](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234239)

---

