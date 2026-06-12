---
title: "The disk drive for UUID is not ready or not present. Swap not active at startup."
date: 2015-03-18
forum: New to Ubuntu
---

### Post by Snortley on 2015-03-18
At some point, not sure exactly when, I started getting this message at startup:

The disk drive for UUID=46203a8d-c1a6-4801-88eb-c2c1af251390 is not ready or not present.
Wait to continue, press S to skip mounting, or M for manual recovery.

That UUID was given for cryptswap1 in fstab, but blkid showed a different UUID, so I tried editing fstab with the UUID from blkid. That didn't help. Now I get the message at startup with that UUID instead. Now blkid gives yet another UUID for cryptswap1.

Once the system starts, sysinfo shows no active swap. In gnome-disks, I can manually activate cryptswap1, and then sysinfo shows swap as active.

So how can I get the swap to activate at startup?

I am using Xubuntu 14.04, which was installed through the Software Updater as an upgrade from Saucy.

Output from blkid:
/dev/sda2: UUID="ae2463d2-3388-49a6-9f16-b5463893ea7b" TYPE="ext4" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0511" TYPE="vfat" 
/dev/sdb2: UUID="C4E04893E0488D9C" TYPE="ntfs" 
/dev/sdc1: LABEL="My Passport" UUID="4E1AEA7B1AEA6007" TYPE="ntfs" 
/dev/mapper/cryptswap1: UUID="4b5f09be-0f34-42e7-90cc-d59ef4dccd78" TYPE="swap"

Contents of fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda2 :
UUID=ae2463d2-3388-49a6-9f16-b5463893ea7b    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb2 :
UUID=C4E04893E0488D9C    /media/snortley/C4E04893E0488D9C    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0
#Entry for /dev/sdc1 :
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0
#Entry for /dev/mapper/cryptswap1 :
UUID=b2a3ea39-9264-4d1a-bd3d-ba522312ef73    none    swap    sw    0    0
#Entry for /dev/sdd1 :

#UUID=6c561103-e978-4944-87ad-2f96b1f9f55a    none    swap    sw    0    0

UUID=4E1AEA7B1AEA6007 /mnt/usb-WD_My_Passport_0748_575838314335323033333739-0:0-part1 ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8,x-gvfs-show 0 0
UUID=42560C18560C0EFB /mnt/usb-Kingston_DataTraveler_2.0_0014785ED75CA92145A50166-0:0-part1 auto nosuid,nodev,nofail,noauto 0 0

output of sudo fdisk -l:
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f4bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2046    11718655     5858305    5  Extended
/dev/sda2   *    31250432   156248063    62498816   83  Linux
/dev/sda5            4096    11718655     5857280   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x84891eec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      112454       56196   de  Dell Utility
/dev/sdb2   *      112455   156216059    78051802+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023f15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953458175   976728064    7  HPFS/NTFS/exFAT

Disk /dev/mapper/cryptswap1: 5997 MB, 5997854720 bytes
255 heads, 63 sectors/track, 729 cylinders, total 11714560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc22f0720

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table


Gnome-Disks shows partition /dev/sda5 as a swap partition.

However, GParted shows /dev/sda5 as "unknown" file system. Info output is:

File system:   unknown
Size:          5.59 GiB
Flags:

Path:          /dev/sda5
Status:        Not mounted
Label:
UUID:

First sector:  4096
Last sector:   11718655
Total sectors: 11714560

Warning:
Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sda5 is missing


Any ideas, anyone?

---

### Post by Bucky Ball on 2015-03-18
Welcome. Looks like you have an encrypted or LVM swap? Any reason for that? I'd delete it and create a regular /swap partition. Possibly at the root of your current issues.

Also, please use [code] tags for terminal output. Neater and easier to read. See the last link in my signature for how. ;)

---

### Post by egeezer on 2015-03-18
Note that your blkid output shows no swap partition on /dev/sda.

---

### Post by Snortley on 2015-03-18
Yes; it seems I have some sort of encrypted swap. Not sure how I ended up with that.

How would I go about deleting it? I've tried to delete the swap partition that shows in GParted, but I just get a message saying the drive is busy, or something like that, even if the swap isn't active at the time, and even after a swapoff command.

---

### Post by dino99 on 2015-03-18
you only can format a partition when unmunted (not active)
so boot from a cd or usb key to be able to format that swap partition

---

### Post by egeezer on 2015-03-18
I don't know a thing about gnome-disks (never used the new gnome), but can you manually DEactivate cryptswap1, and then run Gparted to see if it is still immune to swapoff/unmount operations?
At worst, you could download and burn an independent Gparted, boot it, and look at your system from the outside, as it were.  That should give the option of removing the swap.

And as Bucky Ball said, by all means install an ordinary /swap.

---

### Post by Snortley on 2015-03-18
OK. I guess the first thing I need to do is disable encrypted swapping. Then I'll see how things work from there. If necessary, I'll try booting from a CD and do some work on the swap partition. May find some time to attempt at least some of this tomorrow.

---

### Post by sudodus on 2015-03-18
There is a bug affecting encrypted swapping (as part of 'Encrypted **home**'). See this link

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

Please mark **[COLOR=#006400]'[/COLOR][[COLOR=#006400]affects me too[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875/+affectsmetoo")[COLOR=#006400]'[/COLOR]** (if you think it does affect you).


'Encrypted **disk**' works. See this link for more details.
[URL="http://ubuntuforums.org/showthread.php?t=2266912"]
LVM encrypted disk & encrypted /home in Lubuntu Vivid complicated or buggy[/URL]

---

### Post by Snortley on 2015-03-18
Fixed, so far. I disabled encrypted swap, and once that was done, it was possible to activate the swap partition, without encryption. I more or less followed the instructions here:

[http://www.logilab.org/blogentry/29155](http://www.logilab.org/blogentry/29155)

It was only necessary to modify the syntax for my system, using the newly assigned UUID in fstab.

---

### Post by sudodus on 2015-03-18
Yes, that works. But the unencrypted swap can be a security hole unless you have encrypted disk.

---

### Post by Bucky Ball on 2015-03-18
> **sudodus said:**
> Yes, that works. But the unencrypted swap can be a security hole unless you have encrypted disk.

Ah, so that's why the encrypted /swap. Thanks. Makes sense. Live and learn. ;)

---

