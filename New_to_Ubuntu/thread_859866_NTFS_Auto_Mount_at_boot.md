---
title: "NTFS Auto Mount at boot"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by bravepc on 2008-07-15
Dear friends:

This is my fdisk output. I want to auto mount [NTFS / FAT SDA2,5,6,8] at boot. Please guide me step by step. Ubuntu Studio 8.04 is my O.S.

Regards from Costa Rica,

Luis-Alberto
**************************************

bravepc@linux-adri:~$ sudo fdisk -l

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xce23ce23

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5471    43945776   83  Linux
/dev/sda2            5472        9729    34202385    f  W95 Ext'd (LBA)
/dev/sda5            5738        9025    26410828+   7  HPFS/NTFS
/dev/sda6            9724        9729       48163+   b  W95 FAT32
/dev/sda7            5472        5737     2136582   82  Linux swap / Solaris
/dev/sda8            9026        9723     5606653+   b  W95 FAT32

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdb: 1021 MB, 1021313024 bytes
15 cabezas, 46 sectores/pista, 2890 cilindros
Unidades = cilindros de 690 * 512 = 353280 bytes
Identificador de disco: 0x00000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1        2891      997256    6  FAT16

Disco /dev/sdc: 1021 MB, 1021313024 bytes
255 cabezas, 63 sectores/pista, 124 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x7a72416a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1               1         124      995998+   6  FAT16

---

### Post by Inxsible on 2008-07-15
> **bravepc said:**
> Dear friends:

This is my fdisk output. I want to auto mount [NTFS / FAT SDA2,5,6,8] at boot. Please guide me step by step. Ubuntu Studio 8.04 is my O.S.

Regards from Costa Rica,

Luis-Alberto
**************************************

bravepc@linux-adri:~$ sudo fdisk -l

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xce23ce23

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5471    43945776   83  Linux
/dev/sda2            5472        9729    34202385    f  W95 Ext'd (LBA)
/dev/sda5            5738        9025    26410828+   7  HPFS/NTFS
/dev/sda6            9724        9729       48163+   b  W95 FAT32
/dev/sda7            5472        5737     2136582   82  Linux swap / Solaris
/dev/sda8            9026        9723     5606653+   b  W95 FAT32

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdb: 1021 MB, 1021313024 bytes
15 cabezas, 46 sectores/pista, 2890 cilindros
Unidades = cilindros de 690 * 512 = 353280 bytes
Identificador de disco: 0x00000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1        2891      997256    6  FAT16

Disco /dev/sdc: 1021 MB, 1021313024 bytes
255 cabezas, 63 sectores/pista, 124 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x7a72416a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1               1         124      995998+   6  FAT16Disco -- makes me think of a different era !! ;)

Oh ..i know it means disk :)

You will need to add the mount entries in the fstab file. Here's a great link to understand fstab

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by weirdfox on 2008-07-15
I suggest that you use ntfs-3g to mout your partition (as opposed to the old ntfs driver).

To do so, first make sure you have ntfs-3g installed:
```
sudo apt-get install ntfs-3g
```
Then edit your ftsab.  Here's one of my entry to */etc/fstab*
```
/dev/sdb1   /mnt/portable-ntfs      ntfs-3g   rw,users,gid=user,dmask=002,fmask=133,nls=utf8 	0 	0
```
Just change the partition path for your NTFS partition and the mount-pount to your preferd location.
I'm not sure, but you may also have to change the NLS.

I hope this helps !

---

