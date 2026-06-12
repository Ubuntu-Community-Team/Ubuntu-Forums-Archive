---
title: "Not recognized second SATA disk"
date: 2015-03-15
forum: New to Ubuntu
---

### Post by xavi7 on 2015-03-15
Hi all,
         I've been across other posts.. but have been unable to find out why my second SATA disk is not recognized. It is seen in the BIOS (IDE channel 0, slave) and can detect it through dmesg, lshw,.. for what I guess it may be something very easy for any ubuntu user (not unexperienced like me..).


Any ideas?
Thanks

---

### Post by xavi7 on 2015-03-15
dmesg output:
[    1.300262] ata1.01: ATA-9: WDC WD20EZRX-00D8PB0, 80.00A80, max UDMA/133
[    1.300264] ata1.01: 3907027055 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.311980] ata2.00: HPA detected: current 976771055, native 976773168
[    1.311985] ata2.00: ATA-8: WDC WD5000AADS-00M2B0, 01.00A01, max UDMA/133
[    1.311987] ata2.00: 976771055 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.316125] ata1.00: configured for UDMA/100
[    1.320647] ata2.00: configured for UDMA/133
[    1.324242] ata1.01: configured for UDMA/133
[    1.332638] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS40  NL02 PQ: 0 ANSI: 5
[    1.341774] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.341777] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.341879] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.341979] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.343951] scsi 0:0:1:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
[    1.344090] sd 0:0:1:0: [sda] 3907027055 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.344103] sd 0:0:1:0: [sda] 4096-byte physical blocks
[    1.344123] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.344156] sd 0:0:1:0: [sda] Write Protect is off
[    1.344162] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.344201] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.344301] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AADS-0 01.0 PQ: 0 ANSI: 5
[    1.344397] sd 1:0:0:0: [sdb] 976771055 512-byte logical blocks: (500 GB/465 GiB)

---

### Post by oldfred on 2015-03-16
Have you partitioned it and formatted it with gparted?
What format did you use?

With Linux you have to give yourself ownership & permissions to use it. 
And usually best to permanently mount with fstab if an internal drive.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by xavi7 on 2015-03-16
Thanks oldfred, but.. there's something I don't catch... to format and partion it, I should be able to mount it and.. how can I mount it if I can't see it with fdisk -l, for instance?

---

### Post by oldfred on 2015-03-17
Then does BIOS see the drive?
Is this the drive?
[    1.344397] sd 1:0:0:0: [sdb] 976771055 512-byte logical blocks: (500 GB/465 GiB)

I would expect fdisk just to show sda with its partitions and a header for sdb, but then nothing else.
show this:
sudo fdisk -lu
sudo parted -l

Is this an internal drive?

---

### Post by xavi7 on 2015-04-06
Sorry for the delay ... (I was out for a fortnight with nearly absent internet connectivity). Look, the disk is an internal one and is recognized by the BIOS

[    1.344090] sd 0:0:1:0: [sda] 3907027055 512-byte logical blocks: (2.00 TB/1.81 TiB)

And you were right about your predictions: the output from fdisk -l is (and complaints that the disk hasn't got a partition table):

Disk /dev/sda: 2000.4 GB, 2000397852160 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907027055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

El disc /dev/sda no conté una taula de particions vàlida

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005a60b

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1   *        2048   968386559   484192256   83  Linux
/dev/sdb2       968388606   976771071     4191233    5  Estesa
/dev/sdb5       968388608   976771071     4191232   82  Intercanvi Linux / Solaris

---

### Post by xavi7 on 2015-04-06
And gparted gives me the following error:
        **Error: /dev/sda: unrecognised disk label   **             

So...

---

### Post by xavi7 on 2015-04-06
... I guess I simply have to format it. I have read** [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)** and I now start to understand it. However, the question is..

(1) Should I have problems when booting it for the size of the disk (2TB) being bigger than the original one (500GB)? (2) And what about the installing points.. this second one is in sda whereas the original one is in sdb? Should this cause any problem when booting my PC? Should I plug the disk to another slot in the mother board (like sdc?)

By the way, the function of this new disk is for backupping..

---

### Post by oldfred on 2015-04-06
With 2TB you can use MBR(msdos) as that is the max that works with the 35/40 year old MBR partitioning. Back then a 5MB hard drive was large.
If not installing Windows you can use the newer gpt partitioning. All Windows since XP can read a NTFS formatted partition with gpt, but Windows only boots from gpt with UEFI.
Ubuntu can boot from gpt with either UEFI or BIOS if you have an efi partition for UEFI and/or a bios_grub partition for BIOS boot. I actually now format all drives as gpt and have since about 2011 as back then I planned a new UEFI system. But I did not build new UEFI system until a few months ago.

If backing up Windows files you can use NTFS, but if Linux you need ext4 as the format, so ownership & permissions are maintained. Windows does not know about ownership & permissions and that is one of its underlying weaknesses.

Only some very old BIOS have issues booting from very large drives. But I normally suggest a smaller 20 or 25GB / (root) partition at beginning of drive and use rest of drive as /home, /mnt/data, /mnt/backup and/or other partitions depending on what you want.

I like to have an install on every drive and a few flash drives, so I have mulitple ways to boot. And each drive is configured with its own grub2 bootloader and all necessary system partitions, so any other drive is not requried to boot. Although mounting other data partition, those mounts will only give errors if drive has failed, but I can fully boot to run repairs.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
      
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

---

