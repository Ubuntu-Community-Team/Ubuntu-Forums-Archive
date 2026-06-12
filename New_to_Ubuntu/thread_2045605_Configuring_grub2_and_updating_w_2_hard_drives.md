---
title: "Configuring grub2 and updating w/ 2 hard drives"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by MrDongji on 2012-08-21
Hello,

I've recently attempted to update my grub through boot repair.

My current setup involves dual booting from 2 separate hard drives:

  1) 500GB for Windows NTFS
  2) 1TB (4 partitions) for Linux NTFS

As I am configuring grub, it asks me where I should install grub
```
[] /dev/sda (500107 MB)
[] /dev/sdb (1000204 MB)
[] - /dev/sdb1 (499M; /boot)
[] - /dev/sdb5 (14998 MB; /)
[] /dev/sdc (1000170 MB) External HDD

```

Here's a pastebin from boot repair:

**[http://paste.ubuntu.com/1159342/](http://paste.ubuntu.com/1159342/)**

After some research, it seems /dev/sda would be a good place to install. 

Since I have 2 hard drives, I would like to install it to the 2nd hard drive solely for Linux to keep the 2 HDDS completely separate.

Would this work or would it involve complications?

Thanks for reading.

---

### Post by grahammechanical on 2012-08-21
First, do not take me for an expert. Others may offer better advice. Some questions.

Do you have a boot option that lets you choose which hard drive to boot from?

If you do then, I think that installing Grub onto sdb (the terrabyte hard drive) would be an option.

What version of Windows do you have? It might make a big difference as to how you deal with the Windows Hard drive. This could be where you need more expert advice than I could give.

Regards.

---

### Post by MrDongji on 2012-08-21
> **grahammechanical said:**
> First, do not take me for an expert. Others may offer better advice. Some questions.

Do you have a boot option that lets you choose which hard drive to boot from?

If you do then, I think that installing Grub onto sdb (the terrabyte hard drive) would be an option.

What version of Windows do you have? It might make a big difference as to how you deal with the Windows Hard drive. This could be where you need more expert advice than I could give.

Regards.

Appreciate your reply, thanks. We're all learning so it's great.

In the BIOS, I can re-arrange boot priorities so I guess in that sense I am able to choose which hard drive I boot from.

The 1TB hard drive is currently 1st in the boot priority list.

I'm running Windows 7 Ultimate x64 on the 500GB hard drive and 

Ubuntu 12.04 LTS on the 1TB hard drive.

---

### Post by ajgreeny on 2012-08-21
I also advise you to put grub on /dev/sdb, and then change your boot priority to sdb.  That will give you the option to boot any of your OSs including windows, from the grub menu, and will leave the windows bootmanager completely untouched. 

Should you ever have a grub problem you would still be able to change boot priority and get into windows automatically.

PS:  You almost never need to put grub on a partition, eg /dev/sdb1; it should be on the first few sectors (MBR) of the disk eg /dev/sdb

I note you have a separate /boot partition, which is usually not necessary and only complicates matters, so I advise you to get rid of the boot partition and leave /boot as a folder in the root partition of Ubuntu.  Why did you choose to do things that way?

Any time you have a new kernel as an update the system will automatically run update-grub, or you can run it manually occasionally, with ```
sudo update-grub
```

---

### Post by MrDongji on 2012-08-21
> **ajgreeny said:**
> I also advise you to put grub on /dev/sdb, and then change your boot priority to sdb.  That will give you the option to boot any of your OSs including windows, from the grub menu, and will leave the windows bootmanager completely untouched. 

Should you ever have a grub problem you would still be able to change boot priority and get into windows automatically.

PS:  You almost never need to put grub on a partition, eg /dev/sdb1; it should be on the first few sectors (MBR) of the disk eg /dev/sdb

I note you have a separate /boot partition, which is usually not necessary and only complicates matters, so I advise you to get rid of the boot partition and leave /boot as a folder in the root partition of Ubuntu.  Why did you choose to do things that way?

Any time you have a new kernel as an update the system will automatically run update-grub, or you can run it manually occasionally, with ```
sudo update-grub
```

Very informative post, I appreciate it.

As for changing boot priority to sdb, this would translate into setting the 2nd hard drive (100TB) at the top of the boot list?

If so, I think I have had it listed prior to my post (Grub would appear with the list of OS).

I think what I had prior to configuring boot repair in the first place was that I had it in /dev/sda. 

Excerpt from pastebin:
```
Grub2 (v1.99) was installed in the MBR of /dev/sda and 

looks at sector 1 of the same hard drive for core.img. core.img

is at this location and looks in partition 1 for /grub.
```

To be frank, I have no idea why the boot partition is what it is. 

How would I go about removing the boot partition. Upon installing Ubuntu, I think I did leave /boot as a folder part of the root partition, but I could definitely be wrong.

I was googling and ended up with a guide in partitioning upon a clean install of Ubuntu 12.04. 

Thank you for the help.

---

### Post by ajgreeny on 2012-08-21
I assume you are able to boot to ubuntu, and if so, please open a terminal and run the command ```
mount
```  to show your currently mounted partitionsand then ```
sudo fdisk -l
```to show all the partitions you currently have on the computer.

---

### Post by MrDongji on 2012-08-21
> **ajgreeny said:**
> I assume you are able to boot to ubuntu, and if so, please open a terminal and run the command ```
mount
```  to show your currently mounted partitionsand then ```
sudo fdisk -l
```to show all the partitions you currently have on the computer.

After typing "mount" in terminal, this is what I receive:

```

/dev/sdb5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /boot type ext4 (rw)
/dev/sdb6 on /home type ext4 (rw)
/home/MrDongji/.Private on /home/Mrdongji type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=e05f0b1ffa7b6055,ecryptfs_fnek_sig=842fe681e2f8c358)
gvfs-fuse-daemon on /home/Mrdongji/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=Mrdongji)

```

After sudo fdisk -l:


```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6ee27562

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848   976769023   488281088    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfca2c3c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      976895      487424   83  Linux
/dev/sdb2          978942   428711935   213866497    5  Extended
/dev/sdb5          978944    30273535    14647296   83  Linux
/dev/sdb6        30275584   420898815   195311616   83  Linux
/dev/sdb7       420900864   428711935     3905536   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 3999 MB, 3999268864 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7811072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x450a707f

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

---

### Post by YannBuntu on 2012-08-22
Hello
> **MrDongji said:**
> 
Here's a pastebin from boot repair:

**[http://paste.ubuntu.com/1159342/](http://paste.ubuntu.com/1159342/)**

After some research, it seems /dev/sda would be a good place to install. 

Since I have 2 hard drives, I would like to install it to the 2nd hard drive solely for Linux to keep the 2 HDDS completely separate.

Would this work or would it involve complications?

Indeed Boot-Repair has done what you wanted: it has installed GRUB on sdb only, so that you can remove any HDD without any problem. (if you disconnect sdb, your PC will boot directly on Windows)
Now you just need to place sdb as 1st in your BIOS boot order.

---

