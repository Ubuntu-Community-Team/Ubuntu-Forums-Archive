---
title: "Mounting NTFS drives"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Dom Rivers on 2008-08-11
I've finally made the full jump from XP to Ubuntu after XP started blue screening on startup, pretty happy so far, my main problem thus far is that I've put Ubuntu on a secondary IDE drive leaving my unwell copy of windows on a SATA 2 drive still in the machine, now both this IDE drive and the SATA drive have masses (about 40gb between them) of Jpegs and Nikon .Nef files I need, firstly Ubuntu doesn't see the IDE drive it's installed on as having any NTFS section that could be searched and secondly it fails to mount the two partitions on the Sata drive (though it sees them) claiming them to be in use and to go into windows and shut down properly (erm nope can't do that). I've tried to write a piece of gobbledygook that it recommended when it wouldn't mount in the terminal pane but it says "only root can do that" a phrase so startlingly meaningless in English that it has me foxed.

  Do you think this ubuntu installation has done for all my photo's on this IDE drive too.....

---

### Post by cdtech on 2008-08-11
Open a terminal within Ubuntu and type:
```
sudo fdisk -l
```
This will list the drives and partitions we can mount.

Paste them back here so we can have a look see.

---

### Post by Dom Rivers on 2008-08-11
[sudo] password for dom: 
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
dom@dom-desktop:~$


Aha, it all comes clear  :-)

---

### Post by satanik on 2008-08-11
You more than likely will need to install 3G-ntfs:

sudo apt-get install ntfs-3g ntfs-config

edit:
Also, that was an 'el' not a one posted above

---

### Post by Dom Rivers on 2008-08-11
> **satanik said:**
> You more than likely will need to install 3G-ntfs:

sudo apt-get install ntfs-3g ntfs-config

edit:
Also, that was an 'el' not a one posted above


Yeeees, you now appear to be speaking in tongues , I'll try doing the fdisk thing with an l this time :)
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93069457

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19633   157702041    7  HPFS/NTFS
/dev/sda2           19634       30401    86493959    7  HPFS/NTFS

Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf64c95b8

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9587    77007546   83  Linux
/dev/hdc2            9588        9964     3028252+   5  Extended
/dev/hdc5            9588        9964     3028221   82  Linux swap / Solaris
dom@dom-desktop:~$ 

There, that's better, there should be an 80gb maxtor IDE drive with a bunch of jpegs formatted in NTFS with this ubuntu also on there and a 250gb WD sata drive in two partitions, one call WD O/S and the other csalled WD freespace.

---

### Post by kansasnoob on 2008-08-11
> **satanik said:**
> You more than likely will need to install 3G-ntfs:

sudo apt-get install ntfs-3g ntfs-config

edit:
Also, that was an 'el' not a one posted above

+1

And, if that doesn't get you what you want try:

```
sudo apt-get install ntfs-config
```

If that still doesn't get you what you want then try ntfsprogs which is also in the repos but read the wiki:

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

---

### Post by Dom Rivers on 2008-08-11
Well this happened, I'll now go into system and err...try to mount :)

dom@dom-desktop:~$ sudo apt-get install ntfs-3g ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
The following NEW packages will be installed
  ntfs-config
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 42.5kB of archives.
After this operation, 442kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe ntfs-config 0.5.5-0ubuntu1 [42.5kB]
Fetched 42.5kB in 0s (155kB/s)   
Selecting previously deselected package ntfs-config.
(Reading database ... 104019 files and directories currently installed.)
Unpacking ntfs-config (from .../ntfs-config_0.5.5-0ubuntu1_i386.deb) ...
Setting up ntfs-config (0.5.5-0ubuntu1) ...
dom@dom-desktop:~$

---

### Post by Dom Rivers on 2008-08-11
Nope, still unable to mount volume and still no clue as, or access, to the further contents of the drive this OS is on....boo.
  May have to get another drive and put a fresh install of windies on it just to rescue my photos...double boo.

---

### Post by cdtech on 2008-08-11
3g is not needed anymore for the latest kernel....

Secondly you will need to create a directory to mount the NTFS partitions:
```
sudo mkdir /mnt/sda1 && sudo mkdir /mnt/sda2
```
Next you'll need to mount both partitions to those directories:
```
sudo mount -t ntfs /dev/sda1 /mnt/sda1 && sudo mount -t ntfs /dev/sda2 /mnt/sda2
```
Now you can go into "places" and browse those partitions....

---

### Post by Dom Rivers on 2008-08-12
Thanks for everyones help, unfortunately it was to no avail and I went out and bought a drive caddy and rescued what jpegs I could to my wifes XP laptop, sadly, in installing Ubunto to the whole drive on my main backup HD it seems I have rendered the 40gb of Jpegs unseeable.

---

### Post by LowSky on 2008-08-12
dude did you run ntfs-config?

---

### Post by Dom Rivers on 2008-08-12
> **LowSky said:**
> dude did you run ntfs-config?

No I didn't (I really am a total, total, Linux noob, I first clapped eyes on Linux 4 days ago), fact of the matter is I wouldn't know how, all I did with all the other advice in here was cut and paste into the terminal and then try to find the drives in the "Places", "Computer" bit.

  I chose Ubuntu because I had heard it could browse NTFS file systems "out of the box"

---

