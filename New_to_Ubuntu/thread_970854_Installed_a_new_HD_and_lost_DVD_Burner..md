---
title: "Installed a new HD and lost DVD Burner."
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Temis72 on 2008-11-04
Hi all, i´m new here.
I have Ubuntu 8.04.
I installed a new, small, HD. When i did it i lost the dvd burner.
I have 1 sata, 200 gb disk, as primary.
The 2nd disk is an IDE, wich is set to Primary Slave. It´s using the same hose as the DVD.
The pc detects the dvd and both HD, cos i see it at the bios setup and under Win XP.
I don´t know what to do... Help please.
Thks,

Jorge

---

### Post by sisco311 on 2008-11-04
open a terminal (Applications -> Accessories -> Terminal) and 
post the output of:
```
sudo fdisk -l
```
```
lshw -C disk
```
and
```
cat /etc/fstab
```

---

### Post by Temis72 on 2008-11-04
sudo fdisk -l

Disco /dev/sda: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x931d931d

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       10010    80405293+   7  HPFS/NTFS

Disco /dev/sdb: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xd2d8d2d8

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1       12749   102406311    7  HPFS/NTFS
/dev/sdb2           12750       24320    92944057+   f  W95 Ext'd (LBA)
/dev/sdb5           21673       24320    21270028+   7  HPFS/NTFS
/dev/sdb6           12750       21303    68709942   83  Linux
/dev/sdb7           21304       21672     2963961   82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco

lshw -C disk
jorge@jorge-desktop:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: SAMSUNG SP2004C
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: VM10
       serial: S07GJ1GP500777
       size: 186GiB (200GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d2d8d2d8
  *-disk
       description: ATA Disk
       product: HDS728080PLAT20
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sda
       version: PF2O
       serial: PFD201S2CATMMJ
       size: 76GiB (82GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=931d931d



cat /etc/fstab

desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=28ff1f73-66a2-49c3-8b19-385cdee7bf19 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=52a4758c-d742-4dec-89b2-bf6140e0095d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

As you can see some info is in spanish since i'm from Argentina, ask if translation is needed.
Many thanks in advance.

Jorge

---

