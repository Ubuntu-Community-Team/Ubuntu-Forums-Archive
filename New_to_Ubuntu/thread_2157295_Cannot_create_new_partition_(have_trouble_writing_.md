---
title: "Cannot create new partition (have trouble writing out superblocks)"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2013-06-24
Hi, I have a removable hard drive whose layout is shown in the screenshot. There are about 140 G of unallocated space on the right. I am trying to create an ext 4 partition of the rightmost 30G of that unallocated space with gparted and get the following error

```
create new ext4 file system  00:01:41    ( ERROR )
         
mkfs.ext4 -j -O extent -L "test" /dev/sdb7
         
Filesystem label=test
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
2621440 inodes, 10479360 blocks
523968 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
320 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: 81/320
mke2fs 1.42.5 (29-Jul-2012)

Warning, had trouble writing out superblocks.
```

I have created partitions on different parts of the 140G (now) unallocated space in the past without problems.However, trying to use the last 30Gs always failed. In fact before I cleaned up my clutters today I used to make /dev/sdb2  the extended partition to exclude the last 30G and everything was fine. I am wondering if that part of the hard drive is damaged and if there is a way to reclaim it. 

Thanks.

---

### Post by natecgraham on 2013-06-26
I'm fairly new to Linux and GParted, but from the guides I've seen, you can't create a 4th partition.

---

### Post by oldfred on 2013-06-26
I have only used gparted to create partitions. But as long as you are creating a partition inside the extended partition as sdb7 you should be ok.

---

### Post by monkeybrain2012 on 2013-06-26
> **oldfred said:**
> I have only used gparted to create partitions. But as long as you are creating a partition inside the extended partition as sdb7 you should be ok.

Hi,

It should be OK. but it is not working because of the "have trouble writing out superblocks" error. As I said this only happens if I try to create a partition using that last 30G or so, but I can do it elsewhere. I am wondering if that part of the hd (the last 30G) is damaged and if there is a way to check it or repair it,

Thanks.

---

### Post by VMC on 2013-06-26
Try and see if gparted can create the partition without errors.

---

### Post by monkeybrain2012 on 2013-06-26
> **VMC said:**
> Try and see if gparted can create the partition without errors.

Yeah I tried and it gave the errors I posted. That was the whole purpose of this thread. :)

---

### Post by oldfred on 2013-06-26
Then in Disk Utility or Disks, click on the drive. And what does it say about drive? It can show all the details of hard drive Smart Status. All I really know is green or passed is good.

---

### Post by zrdc28 on 2013-06-27
smartctl  -test=short /dev/sda

smartctl -a /dev/sda to look at tests

smartctl -H /dev/sda check overall health of hard drive

smartctl -l error /dev/sda  will flag errors on hdd

you might have to install " apt-get install smartmontools "

---

### Post by newb85 on 2013-06-27
Those are helpful commands, but...
Please check your syntax when posting terminal commands, including sudo when necessary, and per the Code of Conduct, place them in code tags:
```
sudo smartctl **--test=short** /dev/sda
sudo smartctl -a /dev/sda
sudo smartctl -H /dev/sda
sudo smartctl -l error /dev/sda
```

---

### Post by VMC on 2013-06-27
> **monkeybrain2012 said:**
> Yeah I tried and it gave the errors I posted. That was the whole purpose of this thread. :)

OK. I thought you executed the command yourself. Then you might try the command using different options, "-c" will check for bad blocks before building the system. Also "-v" will use the verbose output. You might try using a different FS.























' will check

---

### Post by monkeybrain2012 on 2013-06-28
Hi,

Ran all these commands and the outputs are not very informative. :)

```
sudo smartctl --test=short /dev/sdb

smartctl 5.43 2012-06-30 r3573 [i686-linux-3.9.6-030906-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

Smartctl: Device Read Identity Failed: Unknown error

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
bee@raring:~$ sudo smartctl -a /dev/sdb
smartctl 5.43 2012-06-30 r3573 [i686-linux-3.9.6-030906-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

Smartctl: Device Read Identity Failed: Unknown error

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
bee@raring:~$ sudo smartctl -H /dev/sdb
smartctl 5.43 2012-06-30 r3573 [i686-linux-3.9.6-030906-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

Smartctl: Device Read Identity Failed: Unknown error

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
bee@raring:~$ sudo smartctl -l error /dev/sdb
smartctl 5.43 2012-06-30 r3573 [i686-linux-3.9.6-030906-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

Smartctl: Device Read Identity Failed: Unknown error

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```

Are there other ways to find out? Thanks

---

### Post by newb85 on 2013-06-28
smartctl was unable to identify what kind of drive it is.  You can probably feed it that information with the -d option, but then you need to know what to feed it.  Please run
```
sudo lshw -C disk
sudo lshw -C storage
sudo parted -l
```

for those details.

---

### Post by monkeybrain2012 on 2013-06-28
Hi, here they are.

```
$ sudo lshw -C disk
[sudo] password for monkeybrain: 
  
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=0006b6bf

monkeybrain@ubu1204:~$ sudo lshw -C storage
  *-storage               
       description: SATA controller
       product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: storage msi pm ahci_1.0 bus_master cap_list
       configuration: driver=ahci latency=0
       resources: irq:45 ioport:18f0(size=8) ioport:18e4(size=4) ioport:18e8(size=8) ioport:18e0(size=4) ioport:18c0(size=32) memory:fc204000-fc2047ff
  *-scsi:0
       physical id: 2
       logical name: scsi0
       capabilities: emulated
  *-scsi:1
       physical id: 3
       logical name: scsi1
       capabilities: emulated
  *-scsi:2
       physical id: 5
       bus info: usb@2:3
       logical name: scsi6
       capabilities: emulated scsi-host
       configuration: driver=usb-storage


monkeybrain@ubu1204:~$ sudo parted -l
Model: ATA ST9250315AS (scsi)

Model:  Mass Storage Device (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  21.5GB  21.5GB  primary   ext4            boot
 2      21.5GB  213GB   192GB   extended
 5      21.5GB  167GB   145GB   logical   ext4
 6      167GB   170GB   3222MB  logical   linux-swap(v1)
 7      170GB   186GB   16.2GB  logical   ext4
 8      186GB   213GB   26.8GB  logical   ext4
```

I only show the parts for /dev/sdb to avoid to much clutterings. /dev/sda is the internal hard disk.

---

### Post by newb85 on 2013-06-29
It looks to me like the line
```
Model: ATA ST9250315AS (scsi)
```
is an artifact from the sda listing, and your sdb is SCSI.  I don't think parted would give two Model: entries.  If that line *is* part of the sdb listing, the drive is an SCSI to ATA translation (SAT).

This command should determine which it is and execute accordingly.

```
sudo smartctl --test=short -d sat,auto /dev/sdb
```

Please post the results.

---

