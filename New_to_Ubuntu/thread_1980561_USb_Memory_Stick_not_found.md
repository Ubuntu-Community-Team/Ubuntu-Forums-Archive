---
title: "USb Memory Stick not found"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by pottzie on 2012-05-15
I have Ubuntu 12.04, 64 bit. When I plug in a memory stick, it doesn't show up anywhere. I'm using Gnome. lsusb shows it in the terminal, and the led on the memory stick is on. Tried opening "files" to see if it was there, but no dice.

---

### Post by roelforg on 2012-05-15
Open your file manager and see if there's an entry for it there.

Ubuntu typically automounts a usb to some directory in /media

---

### Post by pottzie on 2012-05-15
No,tried that. Nothing except the normal directories.

---

### Post by roelforg on 2012-05-15
> **pottzie said:**
> No,tried that. Nothing except the normal directories.

```

ls /dev/sd*
ls /media
ls /mnt

```
and post the output

---

### Post by pottzie on 2012-05-15
I included the last line from lsusb so you can see the memory stick too. ls /media and ls /mnt came up empty.


```
Bus 001 Device 006: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
larry@larry-Dell-DXP051:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sdb
larry@larry-Dell-DXP051:~$ ls /media
larry@larry-Dell-DXP051:~$ 
larry@larry-Dell-DXP051:~$ ls /mnt
larry@larry-Dell-DXP051:~$ 

```

---

### Post by roelforg on 2012-05-15
> **pottzie said:**
> I included the last line from lsusb so you can see the memory stick too. ls /media and ls /mnt came up empty.


```
Bus 001 Device 006: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
larry@larry-Dell-DXP051:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sdb
larry@larry-Dell-DXP051:~$ ls /media
larry@larry-Dell-DXP051:~$ 
larry@larry-Dell-DXP051:~$ ls /mnt
larry@larry-Dell-DXP051:~$ 

```

Try this:
```

sudo mkdir /media/myusb
sudo mount /dev/sdb /media/myusb

```

If my hunch is right, you should be able to access the usb at /media/myusb
My hunch is that you formatted the stick using a formatter that, for some reason, didn't install a partition table but just treated the usb drive as if it's one partition.
When that happens, instead of /dev/sdb being direct access for the entire drive (useful for mbr installing, wiping, etc) and /dev/sdb<number> the partitions; you have /dev/sdb as the partition, the automounter only mounts partitions in the form of /dev/sdb<number>

If my hunch turned out correct, i advise copying all the files off the disk and using gparted to repartition the drive and install a partitiontable, and copy the files back to the (now erased but recorgnised by the automounter) drive.

---

### Post by pottzie on 2012-05-15
You may be right on the format- I have no idea what it is, although I never format my memory sticks.

 What it returned:
mount: no medium found on /dev/sdb

---

### Post by roelforg on 2012-05-15
> **pottzie said:**
> You may be right on the format- I have no idea what it is, although I never format my memory sticks.

 What it returned:
mount: no medium found on /dev/sdb

Forgot a part, i assume the stick is formatted as fat32 (most are nowadays)
```

mount ** -t vfat ** /dev/sdb /media/myusb

```

---

### Post by pottzie on 2012-05-15
It's being stubborn, I guess.

```
root@larry-Dell-DXP051:/home/larry# mount  -t vfat  /dev/sdb /media/myusb
mount: no medium found on /dev/sdb
```

---

### Post by roelforg on 2012-05-15
> **pottzie said:**
> It's being stubborn, I guess.

```
root@larry-Dell-DXP051:/home/larry# mount  -t vfat  /dev/sdb /media/myusb
mount: no medium found on /dev/sdb
```

Try posting the output of:
```

sudo fdisk -l
sudo lshw -C disk
sudo blkid

```

---

### Post by pottzie on 2012-05-15
Phew! This is getting serious!
```

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000adfcb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    54444031    27220992   83  Linux
/dev/sda2        54446078    58632191     2093057    5  Extended
/dev/sda5        54446080    58632191     2093056   82  Linux swap / Solaris
root@larry-Dell-DXP051:/home/larry# lshw -C disk
  *-cdrom:0 
    description: DVD reader
       product: DVD-ROM DDU1615
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/sr0
       version: FDS2
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD-RAM writer
       product: DVDRAM GSA-H10L
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr1
 version: LL10
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: MD00300-BJDW
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: 21.0
       serial: MW0WCAL74872026
       size: 27GiB (30GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000adfcb
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
root@larry-Dell-DXP051:/home/larry# blkid
/dev/sda1: UUID="c6f613e2-9e48-4afc-8594-09f27fd002e2" TYPE="ext4" 
/dev/sda5: UUID="48e3c016-fcd7-4524-ac00-18e05193e188" TYPE="swap" 
             

```

---

### Post by roelforg on 2012-05-15
> **pottzie said:**
> Phew! This is getting serious!
```

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000adfcb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    54444031    27220992   83  Linux
/dev/sda2        54446078    58632191     2093057    5  Extended
/dev/sda5        54446080    58632191     2093056   82  Linux swap / Solaris
root@larry-Dell-DXP051:/home/larry# lshw -C disk
  *-cdrom:0 
    description: DVD reader
       product: DVD-ROM DDU1615
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/sr0
       version: FDS2
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD-RAM writer
       product: DVDRAM GSA-H10L
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr1
 version: LL10
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: MD00300-BJDW
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: 21.0
       serial: MW0WCAL74872026
       size: 27GiB (30GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000adfcb
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
root@larry-Dell-DXP051:/home/larry# blkid
/dev/sda1: UUID="c6f613e2-9e48-4afc-8594-09f27fd002e2" TYPE="ext4" 
/dev/sda5: UUID="48e3c016-fcd7-4524-ac00-18e05193e188" TYPE="swap" 
             

```

I'm starting to think this usb has been wiped clean of all data.
If you can use it from another system, use that and copy the files.
Because you're gonna have to repartition the thing.

---

### Post by Boyntonstu on 2012-05-15
I am also having difficulty:

boyntonstu@boyntonstu-s5704y:~$ sudo mkdir /media/myusb
[sudo] password for boyntonstu: 
boyntonstu@boyntonstu-s5704y:~$ sudo mount /dev/sdb /media/myusb
mount: /dev/sdb already mounted or /media/myusb busy
boyntonstu@boyntonstu-s5704y:~$ cd /dev/sdb
bash: cd: /dev/sdb: Not a directory
boyntonstu@boyntonstu-s5704y:~$ sudo mount /dev/sdb /media/myusb
mount: /dev/sdb already mounted or /media/myusb busy
boyntonstu@boyntonstu-s5704y:~$ cd /dev/sdb:
bash: cd: /dev/sdb:: No such file or directory
boyntonstu@boyntonstu-s5704y:~$


boyntonstu@boyntonstu-s5704y:~$ cd /media/myusb
boyntonstu@boyntonstu-s5704y:/media/myusb$ ls
boyntonstu@boyntonstu-s5704y:/media/myusb$ cd ..
boyntonstu@boyntonstu-s5704y:/media$ ls
myusb  OS  STU EXT HD
boyntonstu@boyntonstu-s5704y:/media$

---

### Post by pottzie on 2012-05-15
This is the first time I've attempted to read a memory stick since I installed 12.04. I just tried 3 other sticks, and none of them are showing up. Nothing pops up on screen, nothing shows up under file systems, and lsusb shows them in the terminal.

 Possible that it has something to do with the fact that I'm using Gnome?

---

