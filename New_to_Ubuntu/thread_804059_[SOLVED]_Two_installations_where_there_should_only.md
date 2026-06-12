---
title: "[SOLVED] Two installations where there should only be one???"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by tropdoug on 2008-05-22
Morning everyone, 

and so I go on in the continuing saga of messing my system up.

Background:-  I had two partitions on one disk to which i installed gutsy gibbon in one and winXP is already on the other. I have a second internal disk, now formatted to ext3. As I learnt things here and on the net it became clear that a better arrangement was to have[COLOR=Blue] / [/COLOR]on one partition and [COLOR=Blue]/home [/COLOR]on another disk or partition. I decided to utilise the other disk. 

I used the live cd and re partitioned creating another [COLOR=Blue]Ext3[/COLOR] partition to contain[COLOR=Blue] /home
[/COLOR]
I then tried to move the home dir via instructions found from physcocats. I did something wrong and basically lost the ability to boot into the system. So after a while I reinstalled the system. Now when it came to the partitioner, I decide to use it to prepare the partitions correctly, so formatted sda2 for[COLOR=Blue] / [/COLOR]and ticked sdb1 for[COLOR=Blue] /home[/COLOR]

all went well, (or so I thought) However yesterday I noticed all these extra entries on the grub menu list, and when I looked properly I could see that it appears as if I have two Linux OS's one on sda2 and another on sdb1 which is not good. 

Here is my df - l, return, fdisk return and menu list return. If I am correct, what do I need to do to remove the superfluous one on sdb1?

```
douglas@desktop:~$ df -l
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda2             46181576   2906904  40928784   7% /
varrun                  517816       208    517608   1% /var/run
varlock                 517816         0    517816   0% /var/lock
udev                    517816       120    517696   1% /dev
devshm                  517816         0    517816   0% /dev/shm
lrm                     517816     34696    483120   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             73939452  52332416  17851044  75% /home


``````
 douglas@desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4eab4176

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3888    31230328+   7  HPFS/NTFS
/dev/sda2            3889        9729    46917832+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3657373

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extended
/dev/sdb5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdh: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1       38913   312568641    c  W95 FAT32 (LBA)
douglas@desktop:~$ 


``````
 ## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b3b727c5-b145-4494-aa31-aa986f715b52 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b3b727c5-b145-4494-aa31-aa986f715b52 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c64ef25f-d19f-42f2-93a4-829da848c4a9 ro quiet splash 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c64ef25f-d19f-42f2-93a4-829da848c4a9 ro single 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 7.10, memtest86+ (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/memtest86+.bin  
savedefault
boot

douglas@desktop:~$ 


```I know thats a lot for one post, but if someone knows what I have done and can help me undo it, that would be fantastic   :confused:

---

### Post by meierfra. on 2008-05-22
Yes, it looks like  your old ubuntu did not get erased.  Would you post the output of

```
mount
```

and 

```
cat /etc/fstab
```

so that we can figure out the location of /home

---

### Post by tropdoug on 2008-05-23
```
douglas@desktop:~$ sudo mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sdb1 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
douglas@desktop:~$ 

``````
douglas@desktop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b3b727c5-b145-4494-aa31-aa986f715b52 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=c64ef25f-d19f-42f2-93a4-829da848c4a9 /home           ext3    defaults        0       2
# /dev/sdb5
UUID=79dd635c-adee-4702-a5e0-b4cc9ace54a5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
douglas@desktop:~$ 

```Well I am certainly no expert, but looking at those, it appears to me that the correct boot sequence and mounts are occurring, which if I am correct just leaves me to edit the grub menu and actually remove the second image to free up the room on sdb1, would that be a reasonable thought?

---

### Post by meierfra. on 2008-05-23
You got it right. Just make sure sure that you don't deleted your personal home folder (the folder which has your user name as a name) 

You might also think about backing up  your personal home folder and reformat  /dev/sdb1. Just to make sure that you old install gets completely erased.

---

### Post by tropdoug on 2008-05-23
> **meierfra. said:**
> You got it right. Just make sure sure that you don't deleted your personal home folder (the folder which has your user name as a name) 

You might also think about backing up  your personal home folder and reformat  /dev/sdb1. Just to make sure that you old install gets completely erased.



Hmmm, I took the chicken way out cos I am a little nervous about reformatting and losing the symlinks etc to the home directory. Sooooo I used ```
 sudo rm -R -d -v 
```to remove all the doubled up directories, which worked well, but I am left with my /home/douglas directory which is what I want and a file [COLOR=Blue]vmlinux [/COLOR]with a broken symlink.the[COLOR=Blue] rm [/COLOR]command will not remove that because its not a directory and I can't delete it via the gui as I don't have permission. I tried changing ownership and permissions but it wont let me. [COLOR=Blue]Any suggestions just to get rid of this last bit. [/COLOR]Oh I I edited the grub menu.lst removed the extra entries and all is good on boot. 

:)

---

### Post by meierfra. on 2008-05-23
Is the file really "vmlinux" ? Or is it "vmlinuz"?

```
sudo rm vmlinuz
```
should delete it.

If not,  try

```
sudo apt-get install symlinks
sudo symlinks -d  /home 
```

This will deleted all broken symlinks in /home (but not in any subdirectories)

---

### Post by tropdoug on 2008-05-24
Ooops, the value of peering closer at the monitor is a lesson to learn, perhaps I should renew my glasses for a better pair. 

all cleaned up now, thanks a lot for the patient help

---

