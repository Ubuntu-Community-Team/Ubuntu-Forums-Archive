---
title: "Hard Drive Troubles"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Toddeus on 2008-07-12
I'm having trouble mounting a hard drive in Xubuntu.

Here is what I tried and the result.  Any suggestions? 

 sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3bf23bf1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26       30401   243995220   8e  Linux LVM

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02380238

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29644   238115398+  83  Linux
/dev/sdb2           29645       30401     6080602+   5  Extended
/dev/sdb5           29645       30401     6080571   82  Linux swap / Solaris
todd@todd-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             224G  3.6G  209G   2% /
varrun               1014M   92K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   92K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             190M   13M  168M   7% /media/_boot
/dev/sdb1             224G  3.6G  209G   2% /mnt/My80GigDrive

todd@todd-desktop:~$ sudo mount /dev/sda2 /mnt/fedora
mount: unknown filesystem type 'LVM2_member'

---

### Post by Toddeus on 2008-07-12
todd@todd-desktop:~$ sudo pvs
  PV         VG         Fmt  Attr PSize   PFree 
  /dev/sda2  VolGroup00 lvm2 a-   232.69G 32.00M
todd@todd-desktop:~$ lvdisplay /dev/Volgroup00
  /var/lock/lvm/V_Volgroup00: open failed: Permission denied
  Can't lock Volgroup00: skipping
todd@todd-desktop:~$ sudo lvdisplay /dev/VolGroup00
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper 1.02.20 (2007-06-15)(compat) and kernel driver 
  --- Logical volume ---
  LV Name                /dev/VolGroup00/LogVol00
  VG Name                VolGroup00
  LV UUID                tLCJL0-OqHp-3pxr-rre2-x9RA-JoeB-ZDN3xR
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                230.72 GB
  Current LE             7383
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
   
  --- Logical volume ---
  LV Name                /dev/VolGroup00/LogVol01
  VG Name                VolGroup00
  LV UUID                12rYdH-yDA4-6DTs-KyeB-uedB-Ioqq-OfB8hP
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                1.94 GB
  Current LE             62
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
todd@todd-desktop:~$ sudo mount  /dev/VolGroup00/LogVol00 /mnt/fedora
mount: special device /dev/VolGroup00/LogVol00 does not exist
todd@todd-desktop:~$ sudo mount  /dev/VolGroup00/LogVol00
mount: can't find /dev/VolGroup00/LogVol00 in /etc/fstab or /etc/mtab

---

### Post by Polygon on 2008-07-12
what happens when you try and mount it? what command are you trying to run?

---

### Post by Traumadog on 2008-07-12
Hello Toddeus,

Did a bit of research and found a "How To" on accessing a Fedora Logical Volume (LVM) from Ubuntu.  

[http://www.linux-sxs.org/storage/fedora2ubuntu.html](http://www.linux-sxs.org/storage/fedora2ubuntu.html)

Hope it helps.

Best wishes,  :)

Traumadog.

---

### Post by Toddeus on 2008-07-12
Worked like a charm Traumadog.  Thanks a lot.  I never realized I had to activate it.  I wish I would've come across that in my many searches.

---

### Post by Traumadog on 2008-07-12
> **Toddeus said:**
> Worked like a charm Traumadog.  Thanks a lot.  I never realized I had to activate it.  I wish I would've come across that in my many searches.

Glad I was able to help.

Best wishes,

Traumadog. :)

---

