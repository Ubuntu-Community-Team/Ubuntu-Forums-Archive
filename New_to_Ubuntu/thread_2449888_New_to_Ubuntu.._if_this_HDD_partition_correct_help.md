---
title: "New to Ubuntu.. if this HDD partition correct? help"
date: 2020-09-03
forum: New to Ubuntu
---

### Post by Darkhaund on 2020-09-03
Hello guys.. new to Ubuntu (sortta) and this time I am decided tos stick around.
This is my current SSD HDD wehre my ubuntu is installed.

There is no dual boot or anything.. just ubuntu.
I am curious of this partition is correct and what does it mean. I really wish to understand.

Here is the screenshot
[COLOR=unset]https://imgur.com/LOUlKkb[IMG]https://imgur.com/LOUlKkb[/IMG][/COLOR]
[IMG]https://i.imgur.com/LOUlKkb.png[/IMG]

Why are there 3 partitions? Is this how it should be?
[COLOR=unset]https://imgur.com/LOUlKkb[/COLOR]

---

### Post by Dennis N on 2020-09-03
This is the default when you install in BIOS mode in 20.04 and use the "Erase Disk and Install" option. Its an MS-DOS partition table, but the installer creates an unnecessary FAT partition (partition 1) that is only needed for a UEFI system. You didn't do anything wrong. It's a bug of sorts in the installer, but won't affect how the system runs.  I have the same thing here in this virtual machine:

```
Model: Virtio Block Device (virtblk)
Disk /dev/vda: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  538MB   537MB   primary   fat32        boot
 2      539MB   21.5GB  20.9GB  extended
 5      539MB   21.5GB  20.9GB  logical   ext4

```

---

### Post by Darkhaund on 2020-09-03
Thanks... so all is good and I have nothing to worry about. No disk space lost or anything right?

---

### Post by Dennis N on 2020-09-03
We have all the disk space, but the small partition 1 isn't of much use in a BIOS install. The installer also made a choice of using a logical partition, which is not what most people would do if doing their own partitioning on a system intended for one OS. Bit it will work fine.

---

### Post by oldfred on 2020-09-03
If mounted at /EFI/ubuntu then did you install in UEFI boot mode, but have the old MBR partitioning as you have an extended & logical partition(s).

With UEFI better to use gpt as gpt has some advantages, even if you want to boot in BIOS mode with Ubuntu. I have used gpt with Ubuntu since 2010 and my BIOS only system, and since 2014 with UEFI systems.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

Windows requires gpt for UEFI boot, but Ubuntu does not.

---

### Post by Dennis N on 2020-09-03
> If mounted at /EFI/ubuntu then did you install in UEFI boot mode, but have the old MBR partitioning as you have an extended & logical partition(s).

You can't determine the type of install by looking to see if /boot/efi is mounted. In the default BIOS-mode install (using "Erase disk") in Ubuntu 20.04, the OS creates the FAT32 partition, and creates an entry in fstab to mount it at /boot/efi, but the partition is empty. 

Details from the same system as displayed in post #2. (space command is an alias I use)
```
dmn@Tyana-vm:~$ space
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
/dev/vda5        20G   14G  4.3G  77% /
/dev/vdb1       9.8G  1.6G  7.7G  18% /mnt/Common-Files
/dev/vda1       511M  4.0K  511M   1% /boot/efi

```
But this isn't a UEFI installation:

---

### Post by Darkhaund on 2020-09-11
Thanks for the input guys.. but alot of the things you guys explian make no sense to me.. since i am new to this

---

### Post by mastablasta on 2020-09-14
BIOS - the old software on motherboard. it loads before the OS loads. it then boots the OS using MBR (master boot record). that one allowed 4 primary partitions and then logical or extended partitions. OS should be installed to primary partition. it didn't need a special partition for boot so everything was just on one partition. or in windows talk everything was on drive C:\

UEFI appeared in 2003, and is a newer, more advanced version of BIOS. it then moved to consumer market in about 2008, 2009, but wasn't used massively until windows 8 came out when microsoft decided to add secure boot to it. secure boot means the OS needs a signed kernel (sore of the OS) before the system would even boot. it's a security layer and DRM system as well. it means for example that the windows you boot came from microsoft and is not a cracked version, because UEFI check if it was digitally signed. anyway in order to boot the OS in UEFI, the signature has to be read by any OS (windows doesn't read EXT4 fielsystem that linux uses). so a small FAT partition (boot) is there for that.

the bug described here is that with BIOS PC (old method) this small partition is not needed, but is still created by installer. on new UEFI system partition is needed, so there is no major issue there.

luckily the created partition is small - only 0,5 GB.

also there are actually only 2 partitions on your system. the /boot and the / (which is **root **partition or C:\ in windows talk). what is strange (and probably also part of same bug) is that root is on logical (secondary or extended partition). which is unusual. the usual way is same as it was in old BIOS - that OS install is made on primary partition. however, as others mentioned, don't worry much about it, as it will all work just as well.

---

### Post by Yellow Pasque on 2020-09-14
> **Darkhaund said:**
> Thanks for the input guys.. but alot of the things you guys explian make no sense to me.. since i am new to this

The partition scheme is fine.

---

