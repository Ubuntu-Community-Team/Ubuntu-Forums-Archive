---
title: "Unable to erase"
date: 2016-02-18
forum: New to Ubuntu
---

### Post by claude9 on 2016-02-18
Hi all
I have 64GB SDCARD plugged, thru an adapter in a USB port in my PC running UBUNTU 14.04...
This peripheral is mounted and here is what sits in /etc/fstab  
 (  /dev/sdc1 /media/claude/SDCARD vfat rw,user,auto,exec,gid=100,uid=1000,umask=002,utf8,codepage=850,shortname=mixed    0    0 )

The peripheral is duly mounted on SDCARD and I am the owner ( claude whch is superuser...)
drwxrwxr-x 11 claude users 16384 janv.  1  1970 SDCARD

I thought that, having all the rights, I could erase completely this memory ( rm -R *)....but no !!!
It seems to be erased ( the SDCARD directory is empty )...but no !!! If you unmount , detach the SD and re attached the SD, all files and directory show up again.
All this to ask
1) How come, having all rights I can't do what I want
2) what has to be done to completely clean this memory 

Completely lost...
rgds
Claude

---

### Post by sudodus on 2016-02-18
Please run the following commands with the SD card connected and mounted. Post the output in a reply (copy and paste to the editing window),

```
df -h
sudo parted -ls  # ... space minus ell ess
sudo lsblk -fm

```

Please check if there is a small switch on the card to make it read-only, and if that is the case, check that it is in the read-write position.

Can you write a file to the SD card, or is it read-only also for writing? If you have bad luck it is failing, still possible to read but not write. There is a term for it, 'gridlocked'. See the following links

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by goofprog on 2016-02-18
I suggest to zero fill the SD card using the dd tool.

---

### Post by claude9 on 2016-02-18
HI

here it is...
Writing...same stuff. It "seems" to be writable ( ,I mean  when I xfer a file, it appears in the window) but If I unmount, eject and plug the card reader back, the file I xferred on the Sd is not there.
It makes me think ( because everything seems normal but in fact no ) Thai i'm not playing with the Sd itself but it's copy.
Is it possible ?
```

claude@claude-Precision-WorkStation-T3400:~$ df -h
Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
udev               2,0G    2,0G     0 100% /dev
tmpfs              397M    1,4M  396M   1% /run
/dev/sdb5           18G    8,6G  8,2G  52% /
none               4,0K       0  4,0K   0% /sys/fs/cgroup
none               5,0M       0  5,0M   0% /run/lock
none               2,0G     80K  2,0G   1% /run/shm
none               100M     56K  100M   1% /run/user
/dev/sdc1           60G     16G   44G  27% /media/claude/SDCARD
claude@claude-Precision-WorkStation-T3400:~$ sudo parted -ls  # ... space minus ell ess
[sudo] password for claude: 
Désolé, essayez de nouveau.
[sudo] password for claude: 
Modèle: ATA WDC WD2500AAJS-7 (scsi)
Disque /dev/sda : 250GB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos

Numéro  Début   Fin     Taille  Type      Système de fichiers  Fanions
 1      32,3kB  21,1GB  21,1GB  primary   ntfs                 démarrage
 2      21,1GB  73,6GB  52,5GB  primary   ntfs
 3      73,6GB  250GB   176GB   extended
 5      73,6GB  126GB   52,8GB  logical   ntfs
 6      126GB   194GB   67,9GB  logical   ntfs
 7      194GB   250GB   55,8GB  logical   ntfs


Modèle: ATA WDC WD2500AAJS-7 (scsi)
Disque /dev/sdb : 250GB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos

Numéro  Début   Fin    Taille  Type      Système de fichiers  Fanions
 1      32,3kB  207GB  207GB   primary   ntfs                 démarrage
 2      207GB   226GB  19,3GB  extended
 5      207GB   226GB  19,3GB  logical   ext4
 3      226GB   228GB  2150MB  primary   linux-swap(v1)
 4      228GB   250GB  21,5GB  primary   ext3


Modèle: Generic- Multi-Card (scsi)
Disque /dev/sdc : 63,9GB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos

Numéro  Début   Fin     Taille  Type     Système de fichiers  Fanions
 1      18,9MB  63,9GB  63,8GB  primary  fat32
```

---

### Post by sudodus on 2016-02-19
When the SD card is mounted like this

```
claude@claude-Precision-WorkStation-T3400:~$ df -h
Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
udev 2,0G 2,0G 0 100% /dev
tmpfs 397M 1,4M 396M 1% /run
/dev/sdb5 18G 8,6G 8,2G 52% /
none 4,0K 0 4,0K 0% /sys/fs/cgroup
none 5,0M 0 5,0M 0% /run/lock
none 2,0G 80K 2,0G 1% /run/shm
none 100M 56K 100M 1% /run/user
**/dev/sdc1 60G 16G 44G 27% /media/claude/SDCARD**
```

please write to it, for example

```
cd /media/claude/SDCARD
echo 'Hello World' > hi.txt
sync
cat hi.txt

```

The sync command should flush the buffers (write from memory to the device itself). Is there any error output or warning?

After that unmount the partition

```
**cd**
sudo umount /media/claude/SDCARD
```

Is there any error output or warning?

Unplug and plug back again. Mount manually at /mnt and check if the file hi.txt exists

```
sudo mount /dev/sdc1 /mnt
cat /mnt/hi.txt
```

---

### Post by claude9 on 2016-02-19
Here it is..
Only a small message : peripheral busy when umounting SDCARD but Hello world appears again, which BTW is completely different from what I experience...Apparently I can write in this SDcard but it is not stored. I have another SDcard in wich u can write and retains what you have stored...
My guts feeling is that this card is write defective...
Do you agree ?
( Thks btw for yr concern and support..)
```


claude@claude-Precision-WorkStation-T3400:~$ cd /media/claude/SDCARD
claude@claude-Precision-WorkStation-T3400:/media/claude/SDCARD$ echo 'Hello World' > hi.txt
claude@claude-Precision-WorkStation-T3400:/media/claude/SDCARD$ sync
claude@claude-Precision-WorkStation-T3400:/media/claude/SDCARD$ cat hi.txt
Hello World
claude@claude-Precision-WorkStation-T3400:/media/claude/SDCARD$ sudo umount /media/claude/SDCARD
démontage : /media/claude/SDCARD : périphérique occupé.
       (Dans certains cas, des infos sur les processus l'utilisant
        sont récupérables par lsof(8) ou fuser(1))
claude@claude-Precision-WorkStation-T3400:/media/claude/SDCARD$ sudo mount /dev/sdc1 /mnt
claude@claude-Precision-WorkStation-T3400:/media/claude/SDCARD$ cat /mnt/hi.txt
Hello World
```

---

### Post by sudodus on 2016-02-19
Sorry, I forgot that you should change directory from the partition before unmounting it

```
**cd**
sudo umount /media/claude/SDCARD

```

I'm not sure yet, that it is defective. Let us do some more testing (according to post #8, now with one more command) :-)

---

### Post by claude9 on 2016-02-19
One question...
Can we imagine that the card in NOT defective but something has written some kind of I don't know what to prevent further writings...

I'll lauch the whole set of commands...with cd prior to umount...
let's see...

claude@claude-Precision-WorkStation-T3400:~$ cd /media/claude/SDCARD
claude@claude-Precision-WorkStation-T3400:/media/claude/SDCARD$ echo 'Hello World' > hi.txt
claude@claude-Precision-WorkStation-T3400:/media/claude/SDCARD$ sync
claude@claude-Precision-WorkStation-T3400:/media/claude/SDCARD$ cat hi.txt
Hello World
claude@claude-Precision-WorkStation-T3400:/media/claude/SDCARD$ cd
claude@claude-Precision-WorkStation-T3400:~$ sudo umount /media/claude/SDCARD
[sudo] password for claude: 
claude@claude-Precision-WorkStation-T3400:~$ sudo mount /dev/sdc1 /mnt
claude@claude-Precision-WorkStation-T3400:~$ cat /mnt/hi.txt
cat: /mnt/hi.txt: Aucun fichier ou dossier de ce type

hey hey...nothing, file or directory with that name...
dead no ?

---

### Post by sudodus on 2016-02-19
I'm afraid it is dead. Maybe it is no longer identified as /dev/sdc1. Please show the output of

```
sudo lsblk -fm
```

-o-

If you wish, you can install mkusb and try to wipe the drive. This is what *goofprog* suggested, and with a safety belt, to avoid writing to the wrong drive.

[mkusb](https://help.ubuntu.com/community/mkusb)
[wipe](https://help.ubuntu.com/community/mkusb/wipe)

If mkusb can write the zeros, it will be possible to use, else I think it is dead.

---

### Post by claude9 on 2016-02-19
claude@claude-Precision-WorkStation-T3400:~$ sudo lsblk -fm
[sudo] password for claude: 
NAME   FSTYPE LABEL      MOUNTPOINT         NAME     SIZE OWNER GROUP MODE
sda                                         sda    232,9G root  disk  brw-rw----
&#9500;&#9472;sda1 ntfs   XP_PRO                        &#9500;&#9472;sda1  19,6G root  disk  brw-rw----
&#9500;&#9472;sda2 ntfs   Seven                         &#9500;&#9472;sda2  48,9G root  disk  brw-rw----
&#9500;&#9472;sda3                                      &#9500;&#9472;sda3     1K root  disk  brw-rw----
&#9500;&#9472;sda5 ntfs   Data_xp                       &#9500;&#9472;sda5  49,1G root  disk  brw-rw----
&#9500;&#9472;sda6 ntfs                                 &#9500;&#9472;sda6  63,2G root  disk  brw-rw----
&#9492;&#9472;sda7 ntfs                                 &#9492;&#9472;sda7  51,9G root  disk  brw-rw----
sdb                                         sdb    232,9G root  disk  brw-rw----
&#9500;&#9472;sdb1 ntfs   Data_Seven                    &#9500;&#9472;sdb1 192,8G root  disk  brw-rw----
&#9500;&#9472;sdb2                                      &#9500;&#9472;sdb2     1K root  disk  brw-rw----
&#9500;&#9472;sdb3 swap              [SWAP]             &#9500;&#9472;sdb3     2G root  disk  brw-rw----
&#9500;&#9472;sdb4 ext3                                 &#9500;&#9472;sdb4    20G root  disk  brw-rw----
&#9492;&#9472;sdb5 ext4              /                  &#9492;&#9472;sdb5    18G root  disk  brw-rw----
sdd                                         sdd     59,5G root  disk  brw-rw----
&#9492;&#9472;sdd1 vfat   SDCARD     /media/claude/SDCA &#9492;&#9472;sdd1  59,5G root  disk  brw-rw----
sr0                                         sr0     1024M root  cdrom brw-rw----

Aaaaarg !!! now it is sdd1...but in my /etc/fstab, the mounting line still begins with /dev/sdc1 and I've checked, the mount point is not SDCARD but SDCARD1...
it's becoming darker and darker !!!

In ubuntu's doc,  dd section, I've found a script to complelely wipe a partiton 
(#!/bin/bash
for n in `seq 7`; do dd if=/dev/urandom of=/dev/sdc1 bs=8b conv=notrunc; done)
and make this an exec file...
I've tried...did not work...my previous files still present
I think I can conclude this Sdcard is dead...Requiescat !!!
and thks again for yr time
Claude

---

### Post by sudodus on 2016-02-19
These things happen, and it is 'normal'. You cannot assume, that a drive is identified as the same device /dev/sdx. Now, if you mount it,

```
sudo mount /dev/sdd1 /mnt
cat /mnt/hi.txt
```

maybe you can read the file, which would prove that you can still write to the pendrive :-)

-o-

It is better to use the UUID as identifier for the drive, for example like this (in /etc/fstab)

```
UUID=xxxx-xxxx /media/claude/SDCARD vfat rw,user,auto,exec,gid=100,uid=1000,umask=002,utf8, codepage=850,shortname=mixed 0 0
```

The actual string xxxx-xxxx is found via the command

```
sudo blkid
```

for the partition in the SD card.

***Edit:***

1. It should be ```
UUID=xxxx-xxxx ...
``` in the first field to identify via the UUID (instead of the partitions block device /dev/sdxy)

2. Repair:

- Boot a live system for example from an Ubuntu install DVD or USB drive.

- Mount the internal drive's root file system, 

```
/dev/sdb5           18G    8,6G  8,2G  52% /
```

It is probably sdb5 as before, but the drive letter b might be replaced by another letter, when seen from the live system.

```
sudo mount /dev/sdb5 /mnt
```

- Edit fstab of the installed system to look like it should with UUID=xxxx-xxxx in the first field (as described in the next post)

```
sudo nano /mnt/etc/fstab
```

- Save the file. Shutdown. Remove the Ubuntu install DVD or USB drive and reboot.

---

### Post by sudodus on 2016-02-19
Sorry for a mistake in the previous post. The identification in /etc/fstab can be

```
UUID=xxxx-xxxx
```
where you find xxxx-xxxx from ```
sudo blkid
```
or
```
LABEL=SDCARD
```

But if you have many SD cards, you'd better edit the label to a unique string, for example 'SD1', 'SD2', etc. You can edit the label with for example ***gparted***.

See ```
man fstab
``` for more details about 'The first field'

```
       The first field (fs_spec).
              This field describes the block special device or remote filesystem to be mounted.

              For  ordinary mounts it will hold (a link to) a block special device node (as created by
              mknod(8)) for the device to be mounted,  like  `/dev/cdrom'  or  `/dev/sdb7'.   For  NFS
              mounts one will have <host>:<dir>, e.g., `knuth.aeb.nl:/'.  For procfs, use `proc'.

              Instead  of  giving the device explicitly, one may indicate the (ext2 or xfs) filesystem
              that is to be mounted by its UUID or volume label  (cf.   e2label(8)  or  xfs_admin(8)),
              writing  LABEL=<label>  or  UUID=<uuid>, e.g., `LABEL=Boot' or `UUID=3e6be9de-8139-11d1&#8208;
              -9106-a43f08d823a6'.  This will make the system more robust: adding or removing  a  SCSI
              disk changes the disk device name but not the filesystem volume label.

              Note  that  mount(8) uses UUIDs as strings. The string representation of the UUID should
              be based on lower case characters.
```

---

