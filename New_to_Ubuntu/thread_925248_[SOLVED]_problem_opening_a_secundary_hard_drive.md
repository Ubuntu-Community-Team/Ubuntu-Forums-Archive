---
title: "[SOLVED] problem opening a secundary hard drive"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by error404 on 2008-09-20
I installed ubunutu on a hd so I could get then information from another harddrive (that was runing windows xp).

However, when I try to open the harddrive it says: "Unable to mount the volume...."

It's a compaq presario and the hd comes with a partition with the os and drivers. I can access that partition just fine!! what's wrong with the other one???

---

### Post by error404 on 2008-09-20
also, I forgot to mention I'm running ubuntu in safe-mode because of the monitor configuration!! how can i change that so when it start it has the right configuration!

---

### Post by bumanie on 2008-09-20
Post ouput of > sudo fdisk -lu > cat /etc/fstab

---

### Post by sayakb on 2008-09-20
Seems like the drive is locked due to usage under Windows.
If the drive is /dev/sdb1 (say), then at a terminal, type in:
```
sudo mkdir /media/drive_win
sudo mount /dev/sdb1 /media/drive_win -o force
```

Check the /dev/*** link for the drive by typing **sudo fdisk -l**

---

### Post by error404 on 2008-09-20
> **bumanie said:**
> Post ouput of
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   471748724   235874331    7  HPFS/NTFS
/dev/sda2       471764790   488392064     8313637+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00055ce3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   619466399   309733168+  83  Linux
/dev/sdb2       619466400   625137344     2835472+   5  Extended
/dev/sdb5       619466463   625137344     2835441   82  Linux swap / Solaris

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=f1f27060-cdc2-4401-acd3-4bb2fb390fa9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=e2a79698-c7b0-4e57-bb52-85baf01b5a1d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by error404 on 2008-09-20
> **LinuxIsInnovation said:**
> Seems like the drive is locked due to usage under Windows.
If the drive is /dev/sdb1 (say), then at a terminal, type in:
```
sudo mkdir /media/drive_win
sudo mount /dev/sdb1 /media/drive_win -o force
```

Check the /dev/*** link for the drive by typing **sudo fdisk -l**

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1   *           1       29365   235874331    7  HPFS/NTFS**
/dev/sda2           29367       30401     8313637+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00055ce3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38560   309733168+  83  Linux
/dev/sdb2           38561       38913     2835472+   5  Extended
/dev/sdb5           38561       38913     2835441   82  Linux swap / Solaris

```

```
sudo mount /dev/sda1 /media/drive_win -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.

```

now it's working!!! :guitar:

thanks a lot!!!!!!

---

### Post by sayakb on 2008-09-20
Glad I could help!
Please mark the thread as solved (Thread tools->Mark thread as solved)

---

