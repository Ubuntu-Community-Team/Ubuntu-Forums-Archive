---
title: "Ubuntu 14.04.1 does not detect Windows 7."
date: 2014-11-01
forum: New to Ubuntu
---

### Post by lucian.andercou on 2014-11-01
Ubuntu 14.04.1 does not detect my Windows 7 installation. This is the output of fdisk-l and paubuntu@ubuntu:~$ sudo fdisk -l 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted. 




Disk /dev/sda: 320.1 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 4096 bytes 
I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
Disk identifier: 0x27375a4d 


   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT 
/dev/sda2          206848   317939711   158866432    7  HPFS/NTFS/exFAT 
/dev/sda3       317939712   420341759    51201024    f  W95 Ext'd (LBA) 
/dev/sda4       420341760   625139711   102398976    7  HPFS/NTFS/exFAT 
/dev/sda5       317941760   420341759    51200000    7  HPFS/NTFS/exFAT 


Disk /dev/sdb: 3999 MB, 3999793152 bytes 
98 heads, 33 sectors/track, 2415 cylinders, total 7812096 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x00000000 


   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1            8192     7812095     3901952    b  W95 FAT32 
ubuntu@ubuntu:~$ ^C 
ubuntu@ubuntu:~$ sudo parted -l 
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table. 
However, it does not have a valid fake msdos partition table, as it should. 
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT 
partition tables.  Or perhaps you deleted the GPT table, and are now using an 
msdos partition table.  Is this a GPT partition table? 
Yes/No?              rted-l:
I also cannot connect to the internet through wifi, although I can connect to my wifi.My laptop is running on BIOS.

---

### Post by Bucky Ball on 2014-11-01
I have changed the title of you thread to give you a better chance of getting support. Generic ones don't get you far generally. ;)

[Boot Repair ]("http://ubuntuforums.org/showthread.php?t=1769482")is your friend. Give that a go. Use the recommended repair option. You can download the ISO and make a disk or USB or, in a terminal running a live boot, paste:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)
```

---

### Post by lucian.andercou on 2014-11-01
I've already burned a CD with a boot-repair-disk-64bit. It said it repaired the boot section, but Ubuntu still doesn't recognize windows 7. With the code you provided I get an error from the first command : Cannot add PPA: '[COLOR=#000000][FONT=Ubuntu Mono]ppa:yannubuntu/boot-repair'. Please check if the PPA name or format is correct.[/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-11-01
Crazy but might work. Try opening a terminal and:

```
sudo update-grub
```

---

### Post by yancek on 2014-11-01
Are you not seeing your windows partitions from the Ubuntu installer?  There is no room on the disk on which to install Ubuntu which you can see if you look at the sector output.  It's probably easier to read if you use GParted which is on the Ubuntu disk.  Also there is a message that you have GPT plus you have an Extended partition and my understanding with GPT is that all the partitions are primary.  I don't use it myself but you might post an image from GParted.

---

### Post by Bucky Ball on 2014-11-01
Actually, just thought of something. Open Software Centre and install ntfs-config and ntfs-3g. The NTFS config tool should now be in your menus somewhere. Launch in and enable the Windows partitions. Reboot.

---

### Post by lucian.andercou on 2014-11-01
I've attached a screenshot with gparted, I do have an extended partition of about 105 GB left for Ubuntu. I've had a previous version of Ubuntu installed inside Windows as an application. I tried to download ntfs config, but it won't work since the wifi doesn't work. The update grub also doesn't work, it says something like: can't fin path of 'cow'.

---

### Post by yancek on 2014-11-01
The image in your last post shows nothing on sda, not even the four windows partitions shown in the fdisk output in the initial post.  Also, the image background appears to be from an installation medium.  Do you actually have Ubuntu installed to your computer or are you having these problems while trying to install?  It shows the entire drive as unallocated whereas earlier you had four ntfs partitions.  Strange.

---

### Post by LostFarmer on 2014-11-01
Your sda hdd has both msdos and EFI partition information on it, that is a no no and must be fixed first.  I do not know how.  That is the reason for gparted not printing out any partition information and why the installer is not seeing the partitions.

---

