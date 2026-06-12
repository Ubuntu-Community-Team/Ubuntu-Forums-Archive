---
title: "Access USB Flash Drive"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by jeg90 on 2012-06-30
Hi, and thanks for your help.

I'm trying to put a bootloader on a flash drive I'm using, so that I can play around with it.
I have the bootloader created, but I'm not sure how to stick it in the boot sector of the USB device.

I know to do this for a floppy disk I would need a command like:
[FONT=monospace]
[/FONT]dd if=boot.bin bs=512 of=/dev/fd0

But what is the device location to copy binary onto my flash drive.  I assume its still in /dev, but I couldn't guess which file it is (I see usbmon0 through usbmon8 if that's helpful).

I'm running Ubuntu 12.04, and have a Toshiba L305 Toshiba Satellite.

Thanks for any possible help.

---

### Post by sudodus on 2012-06-30
When your usb flash drive is connected, run the following command and post the output to a reply.

```
sudo fdisk -lu
```

---

### Post by sudodus on 2012-06-30
There are many ways to make a USB drive bootable:

1. The most common way:

Make sure your USB drive has a partition with good FAT32 file system. Set the boot and lba flags.

Then try Unetbootin (there are versions for linux as well as Windows). I have good experiences making boot USB drives with Unetbootin. There are several other programs that can do similar jobs as Unetbootin, for example the built-in USB disk creator.

2. But there are other methods too. See the following links

[[COLOR="Red"]_https://help.ubuntu.com/community/Installation/FromUSBStick/_[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick/")

[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1958073_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

[[COLOR="red"]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")

---

### Post by oldfred on 2012-06-30
I learned about grub2 and in the now everything looks like it should boot with grub2. Kinda like everything looks like a nail when you only have a hammer. But without the os-prober you have to manually maintain your own grub.cfg. I started just by copying from my other grub.cfg and others posted.  I have installed it to FAT32, NTFS, & Linux ext4 (with journal turned off) and MBR and gpt partitioning on USB flash drives.

How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

I directly boot ISO so I can have more than one ISO on a USB flash drive. I even created a Windows repairUSB, but it had lots of room so I installed grub2 and it booted (surprise) and then I added more repair type ISO to my Windows repair USB.

I also add boot stanzas for some of my installs on the hard drive just in case. 

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

---

### Post by jeg90 on 2012-06-30
I entered the command suggested.

After I typed:

```
sudo fdisk -lu
```

I get the response:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a82e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   304463871   152230912   83  Linux
/dev/sda2       304465918   312580095     4057089    5  Extended
/dev/sda5       304465920   312580095     4057088   82  Linux swap / Solaris

Disk /dev/sdc: 4009 MB, 4009754624 bytes
128 heads, 22 sectors/track, 2781 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           8     7831551     3915772    c  W95 FAT32 (LBA)
```


Thanks for your help.

---

### Post by sudodus on 2012-07-01
> **jeg90 said:**
> I entered the command suggested.

After I typed:

```
sudo fdisk -lu
```

I get the response:
...
Disk /dev/sdc: 4009 MB, 4009754624 bytes
128 heads, 22 sectors/track, 2781 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           8     7831551     3915772    c  W95 FAT32 (LBA)[/CODE]

Thanks for your help.

If you still want to make the usb flash drive such a boot drive,

1. Backup everything valuable for you from it.

2. Be aware that it is very important to type the command correctly. Otherwise you might wipe your hard drive.

Use dd according to this command

```
dd if=boot.bin bs=512 of=/dev/sdc
```

3. If you want to reuse the usb flash drive as a normal drive, use the tip from one of the links in post #3

Wipe the CD file system
 
If you want to re-use a USB drive that has been used like this, you probably need to wipe it with dd (overwrite with zeros), otherwise grub-install doesn't want to write into the mbr area, because it might recognize the 'floppy file system'.
 
 Run the following commands to identify your USB drive and find its linux drive letter.
```
sudo fdisk -lu
```
 and 
```
sudo blkid
```
Finally wipe the USB drive with the following command. 
```
sudo dd if=/dev/zero of=/dev/sdX bs=4096
```
 where it is very important that you replace X by the linux drive letter for your USB drive and nothing else. The target drive will be completely wiped, not even PhotoRec can do anything after that operation.
 
 And after that you can use gparted to make a new partition table (for example MBR) and suitable partition(s) for example FAT32 with boot and lba flags.

---

