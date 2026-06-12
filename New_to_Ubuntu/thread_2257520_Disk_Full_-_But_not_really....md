---
title: "Disk Full - But not really..."
date: 2014-12-20
forum: New to Ubuntu
---

### Post by matt164 on 2014-12-20
I was trying to scp a .sql dump file over to my Ubuntu Server and it gave me an initial disk is full error after some google searching I was able to run sudo apt-get clean and this allowed me to create a temp file.  However here in lies my issue here is some sample output: 

matt@UbuntuServ12:~$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
**/dev/mapper/UbuntuServ12--vg-root  1.6G  1.4G  193M  88% /**
udev                               1.5G  4.0K  1.5G   1% /dev
tmpfs                              303M  360K  302M   1% /run
none                               5.0M     0  5.0M   0% /run/lock
none                               1.5G     0  1.5G   0% /run/shm
/dev/sda1                          236M   60M  164M  27% /boot
overflow                           1.0M     0  1.0M   0% /tmp
matt@UbuntuServ12:~$ sudo fdisk -l /dev/sda


**Disk /dev/sda: 100.0 GB, 100030242816 bytes**
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007276b


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   195371007    97434625    5  Extended
/dev/sda5          501760   195371007    97434624   8e  Linux LVM
matt@UbuntuServ12:~$



I have a 100GB drive in there yet for some reason its saying that  [B]/dev/mapper/UbuntuServ12--vg-root  1.6G  1.4G  193M  88% / 

[/B]Im assuming it has something to do with my partition scheme, but I'm way too new to this to know exactly what. 

Someone please help!!!

SOLVED: 

sudo lvextend --size 50G /dev/UbuntuServ12-vg/root
  Extending logical volume root to 50.00 GiB
  Logical volume root successfully resized
matt@UbuntuServ12:~$ sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/UbuntuServ12-vg/root
  VG Name                UbuntuServ12-vg
  LV UUID                23Qe1q-urOm-iFJd-MT6A-81w2-4lJ5-BWBBnh
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                50.00 GiB
  Current LE             12800
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0


  --- Logical volume ---
  LV Name                /dev/UbuntuServ12-vg/swap_1
  VG Name                UbuntuServ12-vg
  LV UUID                Z9LfbP-8XFL-pnKS-BI77-QSg0-5mvH-6Z9U0T
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                2.99 GiB
  Current LE             765
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1


att@UbuntuServ12:~$ sudo resize2fs /dev/UbuntuServ12-vg/root
resize2fs 1.42 (29-Nov-2011)
Filesystem at /dev/UbuntuServ12-vg/root is mounted on /; on-line resizing required
old_desc_blocks = 1, new_desc_blocks = 4
The filesystem on /dev/UbuntuServ12-vg/root is now 13107200 blocks long.


matt@UbuntuServ12:~$ df
Filesystem                        1K-blocks    Used Available Use% Mounted on
/dev/mapper/UbuntuServ12--vg-root  51618172 1374980  48116480   3% /
udev                                1536612       4   1536608   1% /dev
tmpfs                                309268     360    308908   1% /run
none                                   5120       0      5120   0% /run/lock
none                                1546332       0   1546332   0% /run/shm
/dev/sda1                            240972   61051    167480  27% /boot
overflow                               1024       0      1024   0% /tmp
matt@UbuntuServ12:~$

---

