---
title: "problem after installation"
date: 2015-07-26
forum: New to Ubuntu
---

### Post by zkr22 on 2015-07-26
Hi, I'm new on Ubuntu. I formatted my pc for install Ubuntu 14.04 LTS and for caution I removed my data's HardDisk. Now I put back the same HardDisk but Ubuntu doesn't recognize it. Can you help me? Sorry for my english.

---

### Post by zkr22 on 2015-07-26
This is the message:
"Error mounting /dev/sdb2 at /media/zkr/STORAGE: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb2" "/media/zkr/STORAGE"' exited with non-zero exit status 12: Failed to read last sector (976749172): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?"

---

### Post by sandyd on 2015-07-26
Hi, can you post the output of
```

sudo fdisk -l
sudo parted -l
```

Thanks!

---

### Post by Vladlenin5000 on 2015-07-26
Hi and welcome.

Your "data drive" - NTFS formated? - has been used before in a Windows environment, right? Are you sure it hasn't logical errors before? If so then a few questions more...

Was it part of a RAID?
Have you used 'dynamic disks' (or whatever it's called in Windows)?
Each of this alone can render a partition unreadable in other systems...

---

### Post by zkr22 on 2015-07-26
the output for sudo fdisk -1 is:
"[sudo] password for zkr: 
fdisk: opzione non valida -- "1"
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track"

for sudo parted -1 is:
"sudo: pared: command not found"

i'm in trouble??
i think of unmount it and put on windows and i will try to copy my files on another HD, after that i'll format the other hard disk hopin that ubuntu will recognize it.

Thanks

---

### Post by Vladlenin5000 on 2015-07-26
It's "l" as in **l**ist, not 1 (one).

Please copy and paste from post#3 directly. In Terminal either use CTRL+SHIFT+V to paste or right-click > paste.

---

### Post by steeldriver on 2015-07-26
You're typing both commands wrong - the option is 

```

-l

```

(the letter 'ell' - short for list) not the number 'one'

---

### Post by zkr22 on 2015-07-26
for sudo fdisk -l:
"Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 testine, 63 settori/tracce, 60801 cilindri, totale 976773168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Identificativo disco: 0x0005e5c0

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   969478143   484738048   83  Linux
/dev/sda2       969480190   976771071     3645441    5  Esteso
Partition 2 does not start on physical sector boundary.
/dev/sda5       969480192   976771071     3645440   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500104683008 bytes
240 testine, 63 settori/tracce, 64600 cilindri, totale 976766959 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0xf1e1f1e1

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976764910   488382424   42  SFS

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 testine, 63 settori/tracce, 121601 cilindri, totale 1953525168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x00e91eab

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdg1   *          63  1953525167   976762552+   7  HPFS/NTFS/exFAT"




for sudo parted -l:
"Modello: ATA Hitachi HDS72105 (scsi)
Disco /dev/sda: 500GB
Dimensione del settore (logica/fisica): 512B/4096B
Tabella delle partizioni: msdos

Numero  Inizio  Fine   Dimensione  Tipo      File system     Flag
 1      1049kB  496GB  496GB       primary   ext4            avvio
 2      496GB   500GB  3733MB      extended
 5      496GB   500GB  3733MB      logical   linux-swap(v1)


Modello: ATA ST3500841AS (scsi)
Disco /dev/sdb: 500GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: msdos

Numero  Inizio  Fine   Dimensione  Tipo     File system  Flag
 1      32,3kB  500GB  500GB       primary


Modello: Toshiba 2.5"External Har (scsi)
Disco /dev/sdg: 1000GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: msdos

Numero  Inizio  Fine    Dimensione  Tipo     File system  Flag
 1      32,3kB  1000GB  1000GB      primary  ntfs         avvio"

---

### Post by yancek on 2015-07-26
sdb2 shows as a dynamic disk, the SFS at the end of the line.  Microsoft proprietary software and you can't change it from Ubuntu/Linux that I know of.  Take a look at the link below to another post at the forums, particularly post 5 for an explanation and suggestion.

 [http://ubuntuforums.org/showthread.php?t=1669910](http://ubuntuforums.org/showthread.php?t=1669910)

---

### Post by Vladlenin5000 on 2015-07-26
The 'best practice' (by Microsoft) is still connecting it to a Windows system, backup to another drive, re-format, recover backup (if necessary). Converting back to a 'normal' partition without data loss (or moving) can be done with third party, mostly commercial, tools.

---

