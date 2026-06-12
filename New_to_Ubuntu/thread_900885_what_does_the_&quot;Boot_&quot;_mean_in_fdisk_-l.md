---
title: "what does the &quot;Boot *&quot; mean in fdisk -l"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by garyed on 2008-08-25
I've got four different computers & I can't make any sense out of them when I 
do fdisk -l.

I understand all the other output " device, start,end,blocks,Id,System"  but I don't get what the "*" means under the Boot column.
Can someone enlighten me?

---

### Post by phidia on 2008-08-25
"*" is a bootable partition.

---

### Post by damis648 on 2008-08-25
It is the active partition a the given disk, the partition that boots when the disk is queried to boot by the BIOS.

---

### Post by garyed on 2008-08-25
Is active partition the same as bootable partition?
I ask this because I have some drives that are not used to boot with yet they
still have "*" on partition 1.

---

### Post by sandysandy on 2008-08-25
u can always mark partitions as bootable or remove bootflag with utilities such as gparted.

can u post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR]

regards

---

### Post by caljohnsmith on 2008-08-25
> **damis648 said:**
> It is the active partition a the given disk, the partition that boots when the disk is queried to boot by the BIOS.
I don't think that BIOS can directly boot a partition; that is the job of whatever boot loader you put in the master boot record (MBR). Note only one partition on your HDD can have its boot flag set. Setting the boot flag on a partition is primarily for brainless boot loaders like Windows; the Windows MBR simply looks for the partition marked with the boot flag and assumes that is the partition it should boot. But with a versatile boot manager like Grub, the boot flag makes no difference. Grub can boot Linux or Windows regardless of whether the boot flag is set or not (at least for modern BIOSes).

---

### Post by garyed on 2008-08-25
Here's one of my Computers:
gary@music-desktop:~$ sudo fdisk -l
[sudo] password for gary:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92c092c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92819281

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005598e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       18700   150207718+  83  Linux
/dev/hdb2           18701       19457     6080602+   5  Extended
/dev/hdb5           18701       19457     6080571   82  Linux swap / Solaris
gary@music-desktop:~$ 

/dev/sda is not used for booting at all, just music.

---

### Post by damis648 on 2008-08-25
> **caljohnsmith said:**
> I don't think that BIOS can directly boot a partition; that is the job of whatever boot loader you put in the master boot record (MBR). Note only one partition on your HDD can have its boot flag set. Setting the boot flag on a partition is primarily for brainless boot loaders like Windows; the Windows MBR simply looks for the partition marked with the boot flag and assumes that is the partition it should boot. But with a versatile boot manager like Grub, the boot flag makes no difference. Grub can boot Linux or Windows regardless of whether the boot flag is set or not (at least for modern BIOSes).

I realize this, and that is not what I said. I said what partition the disk will boot, not the BIOS. When the BOIS asks the disk to boot, the active, or bootable, partition is booted. So, yes, only one partition can be active on a given disk.

---

