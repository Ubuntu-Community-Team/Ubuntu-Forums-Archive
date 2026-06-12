---
title: "Unable to mount when connecting any flash drive, exit status 16"
date: 2016-04-04
forum: New to Ubuntu
---

### Post by germanguy2 on 2016-04-04
Hello, i should say i'm using a live USB with persistence to try out ubuntu after my HDD fried.
The error above happens everytime i connect a flash drive, however, i can still access the flash drive.

Full error:

Unable to mount flash drive.

mount -t "..." exited with exit status 16: mount: can't open /etc/mtab for writing: input/output error.

When i do:

sudo gedit /etc/mtab

It fails to open with the same error, input/output.

How can i fix this?

Currently /media/ubuntu/ contains every mounted flash drive since i rebooted the computer and deleted the folders there, the problem is, i don't have any connected and if i connect another one, it adds one because i can't seem to unmount it, accessing each folder works even though there's no actual flash drive. It also repeats itself, like, drive1,drive2 (it's the same drive)

Can anyone help? I know i'm basically on live CD, but i was hoping this trip to linux would be easier than it's been... :/

Edit: I'm using ubuntu 14.04.4 LTS

---

### Post by sudodus on 2016-04-04
Welcome to the Ubuntu Forums :-)

- Which USB drive are you connecting and disconnecting (the live drive itself or another drive)?
- What are you doing before unplugging (try to unmount or 'eject')?

Please start a terminal window, run the following commands and copy the output into a reply

```
df
cat /etc/mtab
sudo parted -ls
sudo lsblk -fm
```

Please reboot and run the same commands again (without connecting or disconnecting any USB drive) :-)

---

### Post by germanguy2 on 2016-04-04
Thanks.

-Another drive (more than one, but not the live one)
-The drives were all idle, i just unplugged them, but i did try to eject just now and this came up:

Error ejecting /dev/sde: Command-line `eject "/dev/sde"' exited with non-zero exit status 1: unable to open /etc/mtab: Input/output error

I believe the culprit is the mtab file, with what i'm going to post next, it all seems to error on i/o on that file, although i don't know what that file does...

The commands in order before and after reboot:

> df: ‘/run/user/999/gvfs’: Transport endpoint is not connected
Filesystem     1K-blocks    Used Available Use% Mounted on
udev              985476       4    985472   1% /dev
tmpfs             199276    1376    197900   1% /run
/dev/sda1       15124680 5151556   9973124  35% /cdrom
/dev/loop1       1012608 1012608         0 100% /rofs
/cow             3973568 3473692    294772  93% /
none                   4       0         4   0% /sys/fs/cgroup
tmpfs             996360       8    996352   1% /tmp
none                5120       0      5120   0% /run/lock
none              996360    3744    992616   1% /run/shm
none              102400      20    102380   1% /run/user
/dev/sdb1        7813216 4187488   3625728  54% /media/ubuntu/Lexar6
/dev/sdc1        3905124       4   3905120   1% /media/ubuntu/4GB EMTEC2
/dev/sdd1       15345376       8  15345368   1% /media/ubuntu/16GB KINGST

> cat: /etc/mtab: Input/output error

> Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sda: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  15.5GB  15.5GB  primary  fat32        boot, lba


Model:  USB DISK 2.0 (scsi)
Disk /dev/sde: 4011MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  4011MB  4007MB  primary  fat32

> NAME   FSTYPE   LABEL     MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                  sda     14.5G root  disk  brw-rw----
&#9492;&#9472;sda1 vfat     UUI       /cdrom     &#9492;&#9472;sda1  14.5G root  disk  brw-rw----
sde                                  sde      3.8G root  disk  brw-rw----
&#9492;&#9472;sde1 vfat     4GB EMTEC            &#9492;&#9472;sde1   3.7G root  disk  brw-rw----
sr0                                  sr0     1024M root  cdrom brw-rw----
loop0  ext2     casper-rw            loop0    3.9G root  disk  brw-rw----
loop1  squashfs           /rofs      loop1  988.9M root  disk  brw-rw----



After reboot:

> df: ‘/run/user/999/gvfs’: Transport endpoint is not connected
Filesystem     1K-blocks    Used Available Use% Mounted on
udev              985476       4    985472   1% /dev
tmpfs             199276    1372    197904   1% /run
/dev/sda1       15124680 5151556   9973124  35% /cdrom
/dev/loop1       1012608 1012608         0 100% /rofs
/cow             3973568 3469828    298636  93% /
none                   4       0         4   0% /sys/fs/cgroup
tmpfs             996360       8    996352   1% /tmp
none                5120       0      5120   0% /run/lock
none              996360      76    996284   1% /run/shm
none              102400      20    102380   1% /run/user
/dev/sdb1        3905124       4   3905120   1% /media/ubuntu/4GB EMTEC3


> cat: /etc/mtab: Input/output error


> Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sda: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  15.5GB  15.5GB  primary  fat32        boot, lba


Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 4011MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  4011MB  4007MB  primary  fat32


> NAME   FSTYPE   LABEL     MOUNTPOINT        NAME     SIZE OWNER GROUP MODE
sda                                         sda     14.5G root  disk  brw-rw----
&#9492;&#9472;sda1 vfat     UUI       /cdrom            &#9492;&#9472;sda1  14.5G root  disk  brw-rw----
sdb                                         sdb      3.8G root  disk  brw-rw----
&#9492;&#9472;sdb1 vfat     4GB EMTEC /media/ubuntu/4GB &#9492;&#9472;sdb1   3.7G root  disk  brw-rw----
sr0                                         sr0     1024M root  cdrom brw-rw----
loop0  ext2     casper-rw                   loop0    3.9G root  disk  brw-rw----
loop1  squashfs           /rofs             loop1  988.9M root  disk  brw-rw----



There was one flash drive besides the live one plugged in in this whole process, i didn't unplug it or plug it during it, the drive is the 4GB EMTEC .
Thanks for helping!

---

### Post by sudodus on 2016-04-04
- Which version of Ubuntu are you running?

The file **/etc/mtab** is a list of the current mounted devices. It should be possible to read, so there is a serious error in your persistent live system. I had hoped that it would work after reboot.

What you can do is check if there is a version of /etc/mtab in the **casper-rw** file (and in that case remove it). You can check that after booting into a [COLOR="#0000FF"]***live only***[/COLOR] system (remove the boot option 'persistent'). Check with **sudo lsblk -fm** that there is ***[COLOR="#0000FF"]no[/COLOR]*** loop mounted casper-rw device (which there is when you boot in persistent live mode),

```
loop0 ext2 casper-rw loop0 3.9G root disk brw-rw----
```

Then, you can try to mount the file system in the casper-rw file:

```
sudo mount -o loop /cdrom/casper-rw /mnt
```

Then you can browse to **/mnt** and look for **/mnt/etc/mtab** or** /mnt/etc/upper/mtab** and if you find such a file, try to remove it.

```
sudo rm /mnt/etc/mtab
# or
sudo rm /mnt/etc/upper/mtab
```

-o-

If there is no such file, I don't know what is wrong, and can only suggest that you ***save all important files to another drive*** and create a fresh persistent live system.

If you boot from a live Ubuntu system in another USB drive, you can install mkusb (temporarily) into that system and create a persistent live system according to these links

[mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by germanguy2 on 2016-04-05
It gives i/o error when attempting to remove the file, the file description says "inode/x-corrupted type"
Fails with file manager and sudo rm /media/ubuntu/casper-rw/upper/etc/mtab .
What  can i do still? How could i boot into this live system without  persistent from the same drive? The boot options menu isn't any help and  i'm a newb on unix.

Thanks for the help and sorry for the delayed response, been busy.

---

### Post by sudodus on 2016-04-05
Boot live by removing the boot option **persistent**.

See the following link and links from it to learn about boot options. (I think that instead of using the menu, press the Escape key and after that edit the line that appears.)

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

In this case you should remove the boot option (which is opposite to most cases, when you should add some boot option).

---

### Post by germanguy2 on 2016-04-05
Well, i could see the boot options using tab, it's the 14.04.4 LTS version, but i couldn't edit it, it printed off some odd characters on the screen of everything i typed, and pushing the arrows right and left cleared what i just typed, it seems screwed.

I guess i won't waste your time anymore and just try to reinstall this on another drive, it's basically a ubuntu live-test, but since i'm making this almost my daily computer the flash drive must've failed somehow... since i can't change some system settings, (not gray, they just won't change) and can't edit the launcher and couple other things.
I just hope my flash drives still hold the files i put there, since i can see them here good and open the files but...

I'll clear this up and re-install, thanks for the assistance.
One last question, do you have any decent reliable programs to create a persistent system? Because i used the recommended one for Windows at the time (pendrivelinux or something) and i think it installed incorrectly, because the boot screen and other options aren't there but they are on a live 9.04 ubuntu CD that i have.

Thanks again.

---

### Post by sudodus on 2016-04-05
The Ubuntu 14.04.4 LTS iso file should be good. But make sure that the download was successful - check with md5sum with the corresponding string at the following link,

[UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If you boot from a live Ubuntu system in another USB drive, you can install ***mkusb*** (temporarily) into that system and create a persistent live system according to these links

[mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

***Edit:*** It might create problems to do the work in version 9.04 unless you use a very simple tool. Most tools expect a newer version to work correctly. The oldest supported version of Ubuntu is 12.04 LTS, which is 3 years newer.

---

