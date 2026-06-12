---
title: "non-existent drive"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by pjbh1 on 2014-03-19
Trying to install 12.04 LS on an Asus eeepc 901.  It believes there is a second hard drive, /dev/sdb.  Disk utility reports it as Model ATA IS]S-PHI[ON [SL((((((, size 73Gb, 2048 rpm!  There is no such device, but the system persistently tries to read from it, meaning that booting, for example, takes several hours.  There is nothing relating to sdb in /etc/fstab.  umount /dev/sdb says it isn't mounted.  It isn't related to the SD card slot as that works fine, mounting as sdc.  I tried running boot-repair (which took over an hour!); the result is at [http://paste.ubuntu.com/7122494/](http://paste.ubuntu.com/7122494/) How can I convince it there is no such drive?
Thanks, Peter
[h=3][/h]

---

### Post by UltimateCat on 2014-03-20
That's really odd that some how the system is saying that you have a second drive.
So....I'm puzzled unless you have a external drive plugged in to one of your usb ports--

Looking at the output from the fdisk -l command you really only have the one drive:-
```

Disk /dev/sda: 32.3 GB, 32296140800 bytes
255 heads, 63 sectors/track, 3926 cylinders, total 63078400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6259

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    60999679    30498816   83  Linux
/dev/sda2        61001726    63076351     1037313    5  Extended
/dev/sda5        61001728    63076351     1037312   82  Linux swap / Solaris
```

Check in the BIOS and see if your machine is set to boot to hard drive first. (Boot order)
[http://www.whitecanyon.com/how-to-change-boot-order](http://www.whitecanyon.com/how-to-change-boot-order)

If it helps my boot order is DVD/CDROM drive first than if I do not have a DVD/CD in the drive at start up it automatically boots to the HDD.

Sorry but I don't know how to tell your machine that there is not such device --(aside from deleting that line in that /etc/fstab file) But you already said that there isn't
anything sdb related in that file-- That's just crazy---:confused:
Maybe another member or Moderator will know.

Here's the spec's on your computer; it might help others that chime in to help-
Looking at it your Asus has a 40 GB SSD--
[http://event.asus.com/eeepc/microsites/901_1000/en/specifications.html](http://event.asus.com/eeepc/microsites/901_1000/en/specifications.html)

Do you have a external hard drive plugged into your laptop via usb?

---

### Post by slooksterpsv on 2014-03-20
You may want to see if a BIOS update is available for the machine.

Out of curiousity, do you have any USB drives, SD Card, anything like that attached? Even just a basic USB hub, VGA monitor, etc.?

What does the following command output:
```

lsblk

```

---

### Post by pjbh1 on 2014-03-20
lsblk shows four lines referring to sda (1,2,5) and then
sdb  8:16  0  67.8G 0 disk

There is nothing else plugged into it.  The internal SSD was upgraded from the original to 32Gb some years ago, to help fit Win xp bloatware.  I've overwritten xp.  Boot order I set to USB first, in order to install ubuntu, but the usb stick is no longer plugged in.

---

### Post by slooksterpsv on 2014-03-20
There's gotta be something else hmm... Let's just take a whole bunch of logs from your system and see what they say, run the following commands and paste the output in code brackets here. Here's the few I'd like you to run:

sudo lshw  - this one will be LONG, you may want to pipe it like so (then open it and copy paste):
sudo lswh > lshwlog.txt

lspci

lsusb

---

### Post by slooksterpsv on 2014-03-20
Try this one too:

sudo parted -l

---

### Post by pjbh1 on 2014-03-20
I'm afraid I don't know what code brackets are.  Here's the disk bit of lshw, which I assume is the relevant bit.

    *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: RunCore  32G-C
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sda
             version: J090
             serial: 000900005125
             size: 30GiB (32GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000e6259
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 8bd88bb2-f2a8-455f-9d7d-78690ee7ef75
                size: 29GiB
                capacity: 29GiB
                capabilities: primary bootable journaled extended_attributes lar
ge_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-03-17 07:11:11 filesystem=ext4 lastm
ountpoint=/ modified=2014-03-17 07:37:51 mount.fstype=ext4 mount.options=rw,rela
time,errors=remount-ro,data=ordered mounted=2014-03-19 23:32:31 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.1.0,2
                logical name: /dev/sda2
                size: 1013MiB
                capacity: 1013MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1013MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: IS]S-PHI[ON [SL
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: \S\2
             serial: [OY1=8:2=3( ( ( ( (
             size: 67GiB (72GB)
             configuration: ansiversion=5


lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe
04:00.0 Ethernet controller: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)

lsusb
Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sudo parted -l
Model: ATA RunCore 32G-C (scsi)
Disk /dev/sda: 32.3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  31.2GB  31.2GB  primary   ext4            boot
 2      31.2GB  32.3GB  1062MB  extended
 5      31.2GB  32.3GB  1062MB  logical   linux-swap(v1)


Error: /dev/sdb: unrecognised disk label           

Thanks, Peter

---

### Post by slooksterpsv on 2014-03-20
It looks like there is actually a secondary drive in the system. 

[http://liliputing.com/2008/07/how-to-add-hard-drive-to-eee-pc-901.html](http://liliputing.com/2008/07/how-to-add-hard-drive-to-eee-pc-901.html)

I don't know if that will help, but according to Linux yes there are 2 different physical drives in the system.

---

### Post by pjbh1 on 2014-03-21
It would indeed appear to be some remnant of the old drive that remained after the upgrade to a 32Gb main drive.  It was disabled in BIOS, yet still doggedly showed up in Ubuntu.  However, now it won't even reach the BIOS on power up, so I guess it's deceased.  Thanks you for your help
Peter

---

### Post by slooksterpsv on 2014-03-21
If you can remove the drive (if it's still physically in the computer) that would help Otherwise I'd say reset your CMOS.

Remove battery, remove power cord, if the CMOS battery is accessible, remove that; let computer sit for at least 30 min. and plug just the power cord in and see if it shows up still - if it wasn't a physical drive in the system.

---

