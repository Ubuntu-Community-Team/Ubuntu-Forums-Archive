---
title: "[SOLVED] how to mount 2nd"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by DarinB on 2008-11-01
in intrepid i have to mount a 2 hard drive automatically that contains all my music. i can't find my how to from my clean install of hardy.

---

### Post by meindian523 on 2008-11-01
Do you mean you clean installed Intrepid and want to know how to automatically mount your 2nd hard drive?

---

### Post by reg4c on 2008-11-01
If it is an NTFS drive then go to Add/Remove and search for NTFS and you will find NTFS configuration tool
Install it, and it will appear in Apps > System Tools
When you start it select all the drives you want to also support for external and internal devices.

Cheers

---

### Post by DarinB on 2008-11-01
yes i did a clean install of Intrepid, 
it is ext3.

---

### Post by taurus on 2008-11-01
Just add an entry in /etc/fstab to have it mounted automatically each time you boot Ubuntu.

```
/dev/sdb1   /music   ext3   defaults   0   1
```
Or use the UUID instead of /dev/sdb1 if you wish.

---

### Post by DarinB on 2008-11-01
how to edit fstab

---

### Post by taurus on 2008-11-01
```
gksudo gedit /etc/fstab
```

---

### Post by DarinB on 2008-11-01
i messed up in the properties section of the 2 hard drive i added the mount point to properties> drive tab> setting i typed in the info that was above in the boxes then re booted no i get these errors and i don't know how to go back and remove the stuff i added or fix it i will try to post the screen shots [IMG]file:///home/darin/Desktop/can%20not%20mount[/IMG]
[IMG]file:///home/darin/Desktop/unable%20to%20mount%202.png[/IMG]

---

### Post by DarinB on 2008-11-01
humm i don't know how to added the screen shots this clean install is getting to be a drag

---

### Post by DarinB on 2008-11-01
i am now unable to mount at albettel i get error messages.
so i will try to explain it more clearly i  added the mount point manually to the properties tab of the 2 hd by manually mounting the 2 dh then i went to >properties>drive tab>setings i typed the info in there and now it comes up that the 2hd is un-mountable because the mount point is entered incorrectly. How do i fix this massive dilemma.

---

### Post by taurus on 2008-11-01
Can you post the outputs of these commands from a terminal, Applications -> Accessories -> Terminal?

```
sudo fdisk -l
cat /etc/fstab
ls -la /
df -h
```

---

### Post by DarinB on 2008-11-01
darin@darin-desktop:~$ sudo fdisk -l
[sudo] password for darin: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ae79d16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19175   154023156   83  Linux
/dev/sda2           19176       19457     2265165    5  Extended
/dev/sda5           19176       19457     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcaf8909d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux
Note: sector size is 2048 (not 512)

Disk /dev/sde: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 926 cylinders
Units = cylinders of 15810 * 2048 = 32378880 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1           4       96264    0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 2)
Partition 1 has different physical/logical endings:
     phys=(2, 254, 63) logical=(3, 12, 21)
Partition 1 does not end on cylinder boundary.
/dev/sde2               4         927    29206168    b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(3, 0, 1) logical=(3, 12, 22)
Partition 2 has different physical/logical endings:
     phys=(911, 254, 62) logical=(926, 180, 59)
darin@darin-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1   /music   ext3   defaults   0   1
# /dev/sdb5
UUID=6e020492-7bb1-4b19-be11-f6ef3c3ff128 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
darin@darin-desktop:~$ ls -la /
total 88
drwxr-xr-x  20 root root  4096 2008-10-31 22:43 .
drwxr-xr-x  20 root root  4096 2008-10-31 22:43 ..
drwxr-xr-x   2 root root  4096 2008-10-31 22:52 bin
drwxr-xr-x   3 root root  4096 2008-10-31 22:53 boot
lrwxrwxrwx   1 root root    11 2008-10-31 22:32 cdrom -> media/cdrom
drwxr-xr-x  15 root root 14580 2008-11-01 12:48 dev
drwxr-xr-x 126 root root 12288 2008-11-01 12:48 etc
drwxr-xr-x   3 root root  4096 2008-10-31 22:39 home
lrwxrwxrwx   1 root root    32 2008-10-31 22:43 initrd.img -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root  4096 2008-10-31 22:52 lib
drwx------   2 root root 16384 2008-10-31 22:31 lost+found
drwxr-xr-x   5 root root  4096 2008-11-01 12:48 media
drwxr-xr-x   2 root root  4096 2008-10-20 08:27 mnt
drwxr-xr-x   2 root root  4096 2008-10-29 18:53 opt
dr-xr-xr-x 121 root root     0 2008-11-01 12:47 proc
drwxr-xr-x  11 root root  4096 2008-11-01 12:46 root
drwxr-xr-x   2 root root  4096 2008-10-31 22:52 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 18:53 srv
drwxr-xr-x  12 root root     0 2008-11-01 12:47 sys
drwxrwxrwt  11 root root  4096 2008-11-01 12:48 tmp
drwxr-xr-x  11 root root  4096 2008-10-29 18:58 usr
drwxr-xr-x  15 root root  4096 2008-10-29 19:12 var
lrwxrwxrwx   1 root root    29 2008-10-31 22:43 vmlinuz -> boot/vmlinuz-2.6.27-7-generic
darin@darin-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 378M     0  378M   0% /lib/init/rw
varrun                378M  100K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M  2.9M  375M   1% /dev
tmpfs                 378M  348K  378M   1% /dev/shm
rootfs                145G   26G  112G  19% /
lrm                   378M  2.0M  376M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sde2              28G  954M   27G   4% /media/DARIN'S IPO
darin@darin-desktop:~$

---

### Post by taurus on 2008-11-01
You need to edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and remove the # in front of /dev/sdb1.

```
**[COLOR="Blue"]#[/COLOR]**/dev/sdb1 /music ext3 defaults 0 1
```
Save it and exit gedit editing window.  Then, you need to create a new mount point, /music, to mount it to.

```
sudo mkdir /music
```
Now, mount it and see what happens.

```
sudo mount -a
df -h
```

---

### Post by DarinB on 2008-11-01
darin@darin-desktop:~$ gksudo gedit /etc/fstab

darin@darin-desktop:~$ 
darin@darin-desktop:~$ sudo mkdir /music
darin@darin-desktop:~$ sudo mount -a
darin@darin-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 378M     0  378M   0% /lib/init/rw
varrun                378M  100K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M  2.9M  375M   1% /dev
tmpfs                 378M  348K  378M   1% /dev/shm
rootfs                145G   26G  112G  19% /
lrm                   378M  2.0M  376M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sde2              28G  954M   27G   4% /media/DARIN'S IPO
/dev/sdb1              74G   51G   20G  73% /music

---

### Post by taurus on 2008-11-01
> **DarinB said:**
> darin@darin-desktop:~$ gksudo gedit /etc/fstab

darin@darin-desktop:~$ 
darin@darin-desktop:~$ sudo mkdir /music
darin@darin-desktop:~$ sudo mount -a
darin@darin-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 378M     0  378M   0% /lib/init/rw
varrun                378M  100K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M  2.9M  375M   1% /dev
tmpfs                 378M  348K  378M   1% /dev/shm
rootfs                145G   26G  112G  19% /
lrm                   378M  2.0M  376M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sde2              28G  954M   27G   4% /media/DARIN'S IPO
**[COLOR="Blue"]/dev/sdb1              74G   51G   20G  73% /music[/COLOR]**

There you go.

```
ls -la /music
```

---

### Post by DarinB on 2008-11-01
darin@darin-desktop:~$ ls -la /music
total 100
drwxrwxrwx   6 darin darin  4096 2008-08-08 17:04 .
drwxr-xr-x  21 root  root   4096 2008-11-01 13:03 ..
drwx------   2 root  root  16384 2007-08-27 16:55 lost+found
drwxrwxr-x 614 darin darin 24576 2008-09-25 12:11 My Music
drwx------   4 darin darin  4096 2008-05-12 19:43 .Trash-1000
drwx------   2 darin darin 49152 2008-04-20 09:24 .Trash-darin
darin@darin-desktop:~$

---

### Post by taurus on 2008-11-01
I assume all your music is in /music/My Music now.

```
cd /music/"My Music"
-or-
cd /music/My\ Music
ls -la
```
Otherwise, you can navigate to it with nautilus or whatever file manager you're using.

---

### Post by DarinB on 2008-11-01
i see it is now mounted to the file system under music...thank you you're a genius!! 
now i wish i knew what i did by adding that info into the settings.
i will re read the posts you gave me to see if i can learn what you did.
Thank you! Thank You! Thank You!

---

