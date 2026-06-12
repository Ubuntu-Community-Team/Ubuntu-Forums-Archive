---
title: "Western Digital MyBook Problems"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by saj0577 on 2008-05-28
Well my Western Digital MyBook use to work then i had problems with it so had to delete all partitions on it, now i cant create ext3/ext2 partitons and when i create fat32 partitions they are ready only. 

Any help would be great as its really bugging me.

Thanks
Saj

---

### Post by quelx on 2008-05-28
what is the output of ```
sudo fdisk -l
```

---

### Post by saj0577 on 2008-05-28
> Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0


Thats the relevant bit and thats without any partitions as i delete them again you want me to post it with a partition created on it?

Saj

---

### Post by quelx on 2008-05-28
that's okay

Try using **fdisk** to create the partition

```
sudo fdisk /dev/sdb
```

then **n** > **p** > **1** > (**ENTER**) > (**ENTER**) > **t** > (for fat32 use **b** for ext3/2 use **83**) > **w**

then for FAT32 ```
sudo mkfs.vfat /dev/sdb1
``` or for ext3 ```
sudo mkfs.ext3 /dev/sdb1
```

If Ubuntu doesn't auto mount the drive disconnect it and plug it back in.

---

### Post by saj0577 on 2008-05-28
Trying now wil report in a few minutes.

Saj

---

### Post by saj0577 on 2008-05-28
```
stephen@Stephen-Laptop:~$ sudo fdisk /dev/sdb
[sudo] password for stephen: 

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-60801, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-60801, default 60801): 
Using default value 60801

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 83

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
stephen@Stephen-Laptop:~$ sudo mkfs.ext3 /dev/sdb1
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30531584 inodes, 122096000 blocks
6104800 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000

Writing inode tables: done                            
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir
stephen@Stephen-Laptop:~$ 

```

---

### Post by saj0577 on 2008-05-28
Its the formatting part that throws it everytime.

Saj

---

### Post by quelx on 2008-05-28
without doing anything else do these 
[LIST=1]
[*]disconnnect the drive
[*]reboot and login
[*]open a terminal window
[*]plug the drive in
[/LIST]

After you do these things post the end of ```
dmesg
```; there will be a bunch of USB/SCSI/sd stuff

---

### Post by Stefanie on 2008-05-28
I have the same external HDD and I also had problems with permissions (read-only etc). I followed the advice in the fourth post of this thread, and that solved the problem : [http://ph.ubuntuforums.com/showthread.php?p=4869387](http://ph.ubuntuforums.com/showthread.php?p=4869387) .

---

### Post by saj0577 on 2008-05-28
```
[  492.370407] usb 3-2: new high speed USB device using ehci_hcd and address 2
[  492.509728] usb 3-2: configuration #1 chosen from 1 choice
[  493.184200] usbcore: registered new interface driver libusual
[  493.249947] usbcore: registered new interface driver hiddev
[  184.979885] input: Western Digital External HDD as /devices/pci0000:00/0000:00:1d.7/usb3/3-2/3-2:1.1/input/input7
[  184.995553] input,hidraw0: USB HID v1.11 Device [Western Digital External HDD] on usb-0000:00:1d.7-2
[  184.995805] usbcore: registered new interface driver usbhid
[  184.995926] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  185.040608] Initializing USB Mass Storage driver...
[  185.062437] scsi2 : SCSI emulation for USB Mass Storage devices
[  185.077828] usbcore: registered new interface driver usb-storage
[  185.077835] USB Mass Storage support registered.
[  185.078266] usb-storage: device found at 2
[  185.078269] usb-storage: waiting for device to settle before scanning
[  494.246144] usb-storage: device scan complete
[  494.247647] scsi 2:0:0:0: Direct-Access     WD       5000KS External  106a PQ: 0 ANSI: 4
[  494.252217] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  494.253464] sd 2:0:0:0: [sdb] Write Protect is off
[  494.253474] sd 2:0:0:0: [sdb] Mode Sense: 11 00 00 00
[  494.253482] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  494.256338] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  494.257216] sd 2:0:0:0: [sdb] Write Protect is off
[  494.257225] sd 2:0:0:0: [sdb] Mode Sense: 11 00 00 00
[  494.257231] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  494.257240]  sdb: sdb1
[  494.262868] sd 2:0:0:0: [sdb] Attached SCSI disk
[  494.262961] sd 2:0:0:0: Attached scsi generic sg2 type 0

```

---

### Post by quelx on 2008-05-28
if **fdisk -l /dev/sdb** shows the correct partition table (one giant type 83 Linux partition) try formating again **sudo mkfs.ext3 /dev/sdb1** It looks like Ubuntu was still accessing the drive while the partitions were destroyed then created and formated.  Now that it's been rebooted and there is not a formatted partition for it to automount, it should format okay, should is a big word though...

---

### Post by saj0577 on 2008-05-28
```
stephen@Stephen-Laptop:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux
stephen@Stephen-Laptop:~$ sudo mkfs.ext3 /dev/sdb1
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30531584 inodes, 122096000 blocks
6104800 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000

Writing inode tables: done                            
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir

```


NOTE: it paused for a long time on inode 94

Saj

---

### Post by quelx on 2008-05-28
I'm stumped, sorry I couldn't help you out.

You could try this, format the drive in windows, OSX, or whatever other OS you have handy.  Power the drive down for 10-15 and try the partition/format cycle again.  <shrug>

---

### Post by saj0577 on 2008-05-28
Okay il give it ago.

Thanks anyway :D

Saj

---

### Post by saj0577 on 2008-05-28
You think if i still got warranty just to ask for a replacement?

Saj

---

### Post by inportb on 2008-05-28
Reading the output of your commands... I think it's hinting for you to reboot before formatting. So do the fdisk bit, reboot, then try mkfs.

---

### Post by saj0577 on 2008-05-28
I tried that just and stil same problem, also when i boot with the drive plugged in i get I/O errors on sometning 8 and something 64.

Saj

---

### Post by inportb on 2008-05-28
And what if you don't have the disk plugged while booting?

---

### Post by quelx on 2008-05-28
Try it on a different OS, I've have perfectly good drives not work in Linux but they were fine.  I've also had perfectly bad drives which caused hours of heartache and tears.  The only way WD will replace the drive is if it is tested using their tools at [http://support.wdc.com/](http://support.wdc.com/) and comes up bad.  Perhaps that should be your next step.

---

### Post by saj0577 on 2008-05-28
Yeah i will after its currently formatting on a windows xp machine. its taking its time but what do you expect from usb 1.1 :P 

Saj

---

### Post by seantm on 2008-05-30
Hello Saj,

did you ever get this sorted out? I'm thinking of getting a large external back up drive (1 TB)-oone option is the WD MyBook but I don't want to buy the problems you've been having... I'm running 8.04 Hardy on a Lenovo/IBM thinkpad T61... Please let me know... TIA ~S.

---

### Post by saj0577 on 2008-05-30
Still sorting it i actually think my hard drive is dead full stop so im testing it and then i shall let you know. :)

Saj

---

### Post by ianbrown75 on 2008-06-09
> **quelx said:**
> what is the output of ```
sudo fdisk -l
```
I have followed all of this now I have lost all my information, can you help me?

---

