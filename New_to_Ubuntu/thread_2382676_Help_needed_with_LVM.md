---
title: "Help needed with LVM"
date: 2018-01-16
forum: New to Ubuntu
---

### Post by msilkstone on 2018-01-16
Hi all,

I've been using Ubuntu server a little while now, but am still fairly inexperienced with it, having mainly survived by reading through guides and following instructions. Please forgive my nativity if what I am trying to do seems rudimentary. I've searched through for guides and gotten different instructions depending on the website that I've been reading, if there weren't the possibility of loosing data (and lots of time) I'd give one of them a shot to see what happens, but I really don't want to have to re-setup my little server, if I get something wrong so I'm asking here first.

I currently have 3 physical drives set up with LVM to be read as 1 volume group, the root volume, I believe. Two of these are USB drives and one is an internal drive (I'm using a little netbook as a server).

I have 2x 235gb drives and 1x 300gb drive making a total of around 880gb, but only 100 gb is used. I don't actually know which physical drive is set as /dev/sdxx in the system, though the 300gb drive will be easiest to figure out.
 
I have a couple of additional 500 gb drives and I'd like to alter my arrangement of disks. The main thing I want to do is reduce the LVM so that it is only using 1 internal drive and ideally copy this to one of the new drives. After that, I'd like to create a second LVM out of the remaining disks for backup/storage.
I can likely get the second step done easily enough, but I'm struggling to find a starting point for the first. I'd really appreciate any help that you guys (with a little more experience) might be able to provide)
My disk information is as follows:

 ```
sudo lvmdiskscan
  /dev/PlexServer-vg/swap_1 [       1.84 GiB]
  /dev/sda1                 [     487.00 MiB]
  /dev/PlexServer-vg/root   [     761.51 GiB]
  /dev/mapper/cryptswap1    [       1.84 GiB]
  /dev/sda3                 [     121.10 GiB] LVM physical volume
  /dev/sda5                 [     111.31 GiB] LVM physical volume
  /dev/sdb1                 [     128.00 MiB]
  /dev/sdb2                 [       4.55 TiB]
  /dev/sdc1                 [     298.06 GiB] LVM physical volume
  /dev/sdd1                 [     232.88 GiB] LVM physical volume
  1 disk
  5 partitions
  0 LVM physical volume whole disks
  4 LVM physical volumes
mark@PlexServer:~$ sudo lvmdiskscan -l
  WARNING: only considering LVM devices
  /dev/sda3                 [     121.10 GiB] LVM physical volume
  /dev/sda5                 [     111.31 GiB] LVM physical volume
  /dev/sdc1                 [     298.06 GiB] LVM physical volume
  /dev/sdd1                 [     232.88 GiB] LVM physical volume
  0 LVM physical volume whole disks
  4 LVM physical volumes
mark@PlexServer:~$ sudo pvscan
  PV /dev/sda5   VG PlexServer-vg   lvm2 [111.31 GiB / 0    free]
  PV /dev/sda3   VG PlexServer-vg   lvm2 [121.09 GiB / 0    free]
  PV /dev/sdd1   VG PlexServer-vg   lvm2 [232.88 GiB / 0    free]
  PV /dev/sdc1   VG PlexServer-vg   lvm2 [298.06 GiB / 0    free]
  Total: 4 [763.34 GiB] / in use: 4 [763.34 GiB] / in no VG: 0 [0   ]
mark@PlexServer:~$ sudo pvs
  PV         VG            Fmt  Attr PSize   PFree
  /dev/sda3  PlexServer-vg lvm2 a--  121.09g    0
  /dev/sda5  PlexServer-vg lvm2 a--  111.31g    0
  /dev/sdc1  PlexServer-vg lvm2 a--  298.06g    0
  /dev/sdd1  PlexServer-vg lvm2 a--  232.88g    0
mark@PlexServer:~$ df -h
Filesystem                       Size  Used Avail Use% Mounted on
udev                             857M     0  857M   0% /dev
tmpfs                            177M   13M  165M   8% /run
/dev/mapper/PlexServer--vg-root  750G   43G  677G   6% /
tmpfs                            883M   28K  883M   1% /dev/shm
tmpfs                            5.0M     0  5.0M   0% /run/lock
tmpfs                            883M     0  883M   0% /sys/fs/cgroup
/dev/sda1                        472M  404M   44M  91% /boot
/dev/sdb2                        4.6T  1.1T  3.6T  23% /media/usbhd2
/home/mark/.Private              750G   43G  677G   6% /home/mark
tmpfs                            177M     0  177M   0% /run/user/1000



```

---

### Post by TheFu on 2018-01-16
[https://www.systutorials.com/124416/shrinking-a-ext4-file-system-on-lvm-in-linux/](https://www.systutorials.com/124416/shrinking-a-ext4-file-system-on-lvm-in-linux/) seems a reasonable how-to.

I have a plex server - about 20TB of storage connected, BTW.

LVM is an advanced-intermediate skill. Even simple configs are non-trivial. ;)

The file system used will require different instructions.  Redhad will often use XFS which isn't designed to be shrunk - ever.  SuSE might use btrfs which includes a volume manager and LVM wouldn't be used.  Same for ZFS.  I'll assume ext4, since it is a good, safe, general purpose file system and the default for Ubuntu. EXT4 can be shrunk and expanded.  The LVM tools on Ubuntu can be asked to deal with expansion. I don't know about file system reduction.

You are planning brain surgery. Since you want to move to a different boot disk, you might as well unplug everything and start with a fresh install with a single disk connected.

As a review, here's the different layers:
* files
* directories
* file system
* LV
* VG
* PV
* Partition
* Disk
Since what you are planning goes all the way down to the PV layer - you want to move disks - I'd start over.  That would be faster, IMHO.

Disk layout is a personal thing.  Ask if you'd like advice. Give it a few days, so folks can consider.

Mainly, I wouldn't use LVM on USB connected disks, especially of they are portable.  An external USB3 disk array might be ok, but I've had those connections become loose over time from the little vibrations cause by cooling fans.  eSATA is much better connection and uses the full SATA instruction set.

I wouldn't use LVM on backup storage either.  Since Plex allows adding multiple directories to a single library, using LVM to merge all the "Movies" into a single virtual partition (LV) just isn't necessary.  I have 3-4 different disks included in a single Plex library. It doesn't change anything as far as the media playback/viewing/organization appears.

I love LVM for OS and non-media data.  Taking a snapshot and using that as a backup source is a wonderful thing.  Media just doesn't need snapshots for backups to work.  IMHO.

Everyone has different experiences.  I lost 80% of my data thanks to poor LVM use and 1 failed HDD about 15 yrs ago.  I was spanning disks and merging them into a single LV.  I didn't have backup religion then, like I do now.  So my disk layouts are as simple as possible and only complex when that is helpful.

Of course, there are others with different opinions.  I'd love to see their take on this and conflicting suggestions. Lots of experienced people here.

---

### Post by DuckHook on 2018-01-16
> **TheFu said:**
> … I didn't have backup religion then, like I do now…
Preposterous! Outrageous! Outlandish!

Our backup ***KING*** didn't always have the religion? Impossible. :P

---

### Post by joebeasley on 2018-01-16
1. Backup All DATA

2. Follow [http://www.tldp.org/HOWTO/LVM-HOWTO/removeadisk.html]("http://www.tldp.org/HOWTO/LVM-HOWTO/removeadisk.html")

Warning.... PVMOVE is slow and moving logical volumes can cause data loss.  (See step 1)

---

### Post by msilkstone on 2018-01-17
Thanks for the links and tips. I know it would be easier to start all over again, but I have a fair few services running that I have forgotten how to set up and configure. At the moment, it's running as a book server, DDNS updater, plex server, file server, home security camera server and more . . . It'll likely take me a whole day to get everything configured again, which is what I'm trying to avoid :(

I also have no idea how to backup/restore a vg on Ubuntu :(

I know that usb drives are bad, and I've had a few problems already, which is one of the reasons I want to increase the capacity of the internal drive. I can then just use the external drive for non-essential backup/storage.

> **joebeasley said:**
> 1. Backup All DATA

2. Follow [http://www.tldp.org/HOWTO/LVM-HOWTO/removeadisk.html](http://www.tldp.org/HOWTO/LVM-HOWTO/removeadisk.html)

Warning.... PVMOVE is slow and moving logical volumes can cause data loss. (See step 1)

Will this work while the vg is mounted? 

I've read on many guides that the vg needs to be unmounted as my vg is the root filesystem.

---

### Post by TheFu on 2018-01-17
> **msilkstone said:**
> Thanks for the links and tips. I know it would be easier to start all over again, but I have a fair few services running that I have forgotten how to set up and configure. At the moment, it's running as a book server, DDNS updater, plex server, file server, home security camera server and more . . . It'll likely take me a whole day to get everything configured again, which is what I'm trying to avoid :(

I also have no idea how to backup/restore a vg on Ubuntu :(

I know that usb drives are bad, and I've had a few problems already, which is one of the reasons I want to increase the capacity of the internal drive. I can then just use the external drive for non-essential backup/storage.



Will this work while the vg is mounted? 

I've read on many guides that the vg needs to be unmounted as my vg is the root filesystem.

No. The LV cannot be mounted.  Use a live-boot Linux (CD/DVD/Flash drive) to perform this work.  Just install the LVM and any other disk tools as needed.

If you keep the exact commands used to make the PVs, VGs, and LVs with your backups, then you have the method to restore them.

vgexport and vgimport might be helpful.

---

### Post by joebeasley on 2018-01-17
> **msilkstone said:**
> 
Will this work while the vg is mounted? 

I've read on many guides that the vg needs to be unmounted as my vg is the root filesystem.

NO.  Boot from CD/USb stick.

---

