---
title: "[SOLVED] Upgraded can't browse Windows  now"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by dmsellers on 2008-10-10
I dual boot Xubuntu and Windows XP. I upgraded to Xubuntu 8.04 from a previous version and now I cannot find windows in the file system explorer. Any advice on how I can find it?

David

---

### Post by Orange_and_Green on 2008-10-10
Hi David,

please post the output of ```
sudo fdisk -l
``` and ```
sudo cat /etc/fstab
```.

---

### Post by rVan on 2008-10-10
hi..
my xubuntu also do the same thing like him.
below are the output of the code.. 


> **Orange_and_Green said:**
> Hi David,

please post the output of ```
sudo fdisk -l
``` and ```
sudo cat /etc/fstab
```.

ervan@ervan-desktop:~$ sudo fdisk -l
[sudo] password for ervan: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf5ebf5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9664    62267940    f  W95 Ext'd (LBA)
/dev/sda5            1913        5736    30716248+   7  HPFS/NTFS
/dev/sda6            5737        8983    26081496    7  HPFS/NTFS
/dev/sda7            8984        9591     4883728+  83  Linux
/dev/sda8            9592        9664      586341   82  Linux swap / Solaris
ervan@ervan-desktop:~$ 

ervan@ervan-desktop:~$ sudo cat /etc/fstab
[sudo] password for ervan: 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=41566732-2979-4dc6-ada5-91d777bcc9b5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=dd55b955-d799-4af7-96a7-8c883f60f5f5 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
ervan@ervan-desktop:~$

---

### Post by Orange_and_Green on 2008-10-10
**This is in response to Rvan, based on the configuration of Rvan's system. The OP's config may be different so dmsellers don't try this blindly and post your output first.**

@rVan:

Hello rVan :) 
Please type ```
id ervan
```. You should get a long output that starts with "uid=" followed by a number. That's your UID. Make a note of that number.

Then try the following:

```
sudo -s
mkdir /media/Windows
mkdir /media/WinData1
mkdir /media/WinData2
cp /etc/fstab /etc/fstab.bak
gedit /etc/fstab
```

In the text editor, add the following lines:

```
/dev/sda1 /media/Windows ntfs defaults,uid=YOUR_UID,gid=46,umask=0037 0 1
/dev/sda5 /media/WinData1 ntfs defaults,uid=YOUR_UID,gid=46,umask=0037 0 1
/dev/sda6 /media/WinData2 ntfs defaults,uid=YOUR_UID,gid=46,umask=0037 0 1
```

where YOUR_UID is the number you had noted previously, and save. Then reboot. Good luck:KS

---

### Post by dmsellers on 2008-10-11
Here are the results I get:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       12099    35744625   83  Linux
/dev/sda3           12100       12161      498015   82  Linux swap / Solaris
david@laptop:~$ man cat

[2]+  Stopped                 man cat
david@laptop:~$ sudo cat /etc/fstab
sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=dfa5fe3d-a936-4c88-a572-dcf6f5d03d54 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=224080D04080ABDB /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=1158b4b9-929f-42bf-97c9-a305f1d5d8ab none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by rVan on 2008-10-11
i had tried what u said. but i still can't find my windows partition.
here is the output of the code.


ervan@ervan-desktop:~$ id ervan
uid=1000(ervan) gid=1000(ervan) groups=1000(ervan),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),121(sambashare)

ervan@ervan-desktop:~$ sudo -s
[sudo] password for ervan: 
root@ervan-desktop:~# mkdir /media/Windows
mkdir: cannot create directory `/media/Windows': File exists
root@ervan-desktop:~# mkdir /media/WinData1
mkdir: cannot create directory `/media/WinData1': File exists
root@ervan-desktop:~# mkdir /media/WinData2
mkdir: cannot create directory `/media/WinData2': File exists
root@ervan-desktop:~# cp /etc/fstab /etc/fstab.bak
root@ervan-desktop:~# gedit /etc/fstab


in the text editor:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=41566732-2979-4dc6-ada5-91d777bcc9b5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=dd55b955-d799-4af7-96a7-8c883f60f5f5 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sda1/media/Windows ntfs defaults,uid=1000(ervan) gid=1000(ervan) groups=1000(ervan),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),121(sambashare),gid=46,umask=0037 0 1
/dev/sda5/media/WinData1 ntfs defaults,uid=1000(ervan) gid=1000(ervan) groups=1000(ervan),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),121(sambashare),gid=46,umask=0037 0 1
/dev/sda6/media/WinData2 ntfs defaults,uid=1000(ervan) gid=1000(ervan) groups=1000(ervan),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),121(sambashare),gid=46,umask=0037 0 1

---

### Post by Orange_and_Green on 2008-10-11
@rvan: You need to separate the options in /etc/fstab with COMMAS, no spaces; also, just use the UID. For example, 

THIS IS WRONG /dev/sda1/media/Windows ntfs defaults,uid=1000(ervan) gid=1000(ervan) groups=1000(ervan),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),121(sambashare),gid=46,umask=0037 0 1

THIS IS CORRECT
/dev/sda1/media/Windows ntfs defaults,uid=1000,gid=46,umask=0037 0 1

So, the correct entries are:

```
/dev/sda1/media/Windows ntfs defaults,uid=1000,gid=46,umask=0037 0 1
/dev/sda5/media/WinData1 ntfs defaults,uid=1000,gid=46,umask=0037 0 1
/dev/sda6/media/WinData2 ntfs defaults,uid=1000,gid=46,umask=0037 0 1 
```

---

### Post by Orange_and_Green on 2008-10-11
@dmsellers:

Please type:
```
id david
```

You should get a long output that starts with "uid=" followed by a number. That's your UID. Make a note of that number. NOTE: ONLY THE NUMBER, not the rest of that long output, just the first number.

Then try the following:

Code:

sudo -s
mkdir /media/Windows
cp /etc/fstab /etc/fstab.bak
gedit /etc/fstab

In the text editor, add the following line:

```
/dev/sda1 /media/Windows ntfs defaults,uid=YOUR_UID,gid=46,umask=0037 0 1
```

where YOUR_UID is the number you had noted previously, and save. Then reboot. Good luck

---

### Post by dmsellers on 2008-10-14
I now have 2 folders of my Windows partition. As it turns out it was not gone simply not displayed in the spot I was used to. Thanks for all the help.

---

