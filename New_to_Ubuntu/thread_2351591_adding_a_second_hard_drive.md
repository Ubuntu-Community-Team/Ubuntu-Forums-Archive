---
title: "adding a second hard drive"
date: 2017-02-04
forum: New to Ubuntu
---

### Post by 194ever on 2017-02-04
I just completed the build of a new computer. I am a first-time builder.  The bootable drive is solid state and works fine. I have a larger standard drive I want to use to store photos and music but I don't know how to add it and configure it using ubuntu (16.04). Please walk me through this. Thanks

---

### Post by yancek on 2017-02-04
The first step would be to create a directory to use as a mount point for the partition.  For example:  sudo mkdir /mnt/data  (you can change data to whatever you want)
You would then need an entry in the /etc/fstab file if you want it permanently mounted.  Details on all these steps and the meaning of the various parameters are at the Ubuntu documentation site at the link below:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by ajgreeny on 2017-02-05
After doing the step above to create a new mountpoint for the new disk's partition and adding it to /etc/fstab to automount at boot you will need to make sure you can write to it as user.

What you need to do will depend on the filesystem on the disk.
If it is ntfs or fat32 it should be possible to write to as it is, but if it has an ext4 filesystem you will need to use command ```
sudo chown -R 194ever:194ever /mnt/data
``` to change ownership to you.
This assumes your username is 194ever and that you did choose to create the /mnt/data partiotion as mentioned by yancek

---

### Post by oldfred on 2017-02-05
I replace the default photos & music folders in /home with the folders in my hard drive. 
That uses links. I do that first thing with a new install so I am sure nothing is in the default folders in /home.

I actually link all folder in /home plus a few others. Primarily since I like to have multiple installs, at least one per drive, just in case. And perhaps others to test newer versions as I use LTS as main working install. But then I can link the same folders into all installs so same data is in all of them.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by 194ever on 2017-02-05
responding to yancek, when I type sudo fdisk -l, I get:

   [FONT=Ubuntu]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
 [FONT=Ubuntu]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
 
 
 
 
 [FONT=Ubuntu]Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors[/FONT]
 [FONT=Ubuntu]Units: sectors of 1 * 512 = 512 bytes[/FONT]
 [FONT=Ubuntu]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
 [FONT=Ubuntu]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
 [FONT=Ubuntu]Disklabel type: gpt[/FONT]
 [FONT=Ubuntu]Disk identifier: B77D1D8F-EA31-42AD-9E66-B65A54B499B8[/FONT]
 
 
 [FONT=Ubuntu]Device         Start       End   Sectors   Size Type[/FONT]
 [FONT=Ubuntu]/dev/sda1       2048   1050623   1048576   512M EFI System[/FONT]
 [FONT=Ubuntu]/dev/sda2    1050624 452290559 451239936 215.2G Linux filesystem[/FONT]
 [FONT=Ubuntu]/dev/sda3  452290560 468860927  16570368   7.9G Linux swap[/FONT]
 
 
 
 
 [FONT=Ubuntu]Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors[/FONT]
 [FONT=Ubuntu]Units: sectors of 1 * 512 = 512 bytes[/FONT]
 [FONT=Ubuntu]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
 [FONT=Ubuntu]I/O size (minimum/optimal): 4096 bytes / 4096 bytes

nothing that tells me about system name nor is there a disk identifier for the second hard drive.

the only OS I have is ubuntu 16.04; I did not install windows. 

what am I missing?
[/FONT]

---

### Post by ajgreeny on 2017-02-06
It would appear that the new 1TB drive does not have a formatted partition on it yet.

Either install gparted or use gparted from a live Ubuntu system and create a new partition in /dev/sdb. As you do not use Windows I recommend an ext4 partition.
After creating it you will need to use the chown command I mentioned in post #3 in order for it to be writable by you as user.

---

### Post by oldfred on 2017-02-06
Since you have UEFI system, make sure you choose gpt over the default MBR(msdos), if using gparted.
 I use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 

If thinking of every installing Ubuntu on HDD, you may want to include the ESP & bios_grub as first two partitions.
And I normally do not fully partition initially, and never make a drive one large partition.

I also leave room on SSD for another Ubuntu install. I use current LTS as main working install. My first UEFI system still has 14.04, not booted lately, and 16.04 on it. That way I can make sure my new install fully works before erasing older install. My may not erase 14.04 until 18.04 is out.

I add both of these as first two partitions on every drive. If my 32 or 64GB flash drives I may only use 100MB for ESP.
       gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI) 

I only put a small swap on HDD, as it should never be used with the amount of RAM I have. My old BIOS system with 4GB of RAM never used swap anyway. But having some is still recommended. But 17.04 is changing to use swap file, not swap partition. I put swap as last partition at end of drive so never in between other partitions that later I may want to change.

---

### Post by 194ever on 2017-02-07
I think I'm almost there. After using gparted, I added the mount point with *mkdir* per yancek, then I used the sudo chown to change ownership. I'm not clear on what was intended with /etc/fstab, which may be why I can't transfer my music. It tells me I don't have permission.

---

### Post by yancek on 2017-02-07
Moving or copying data to a place/location outside your /home/user directory almost always requires root (sudo) permissions.  So if you want to copy from your home directory to a /mnt/data location, you would need to preface the cp (copy) command with sudo.  The other option is to change the ownership of the directory/mount point so that your user rather than root owns it.

Probably the simplest thing to do to get accurate advice is to post the permissions you currently have.  For example, if the mount point is /mnt/data your would simply run:  ls - /mnt/data and the owner:group and permissions would show.  An entry in fstab is simply to mount on boot so you don't need to mount manually.

---

### Post by ajgreeny on 2017-02-08
If you ran the ```
sudo chown -R 194ever:194ever /mnt/data
``` as I showed in post #3 you will now be owner of the mountpoint folder and should therefore have full read/write permission to use it as user 194ever.

Is that what you did?

---

### Post by oldfred on 2017-02-08
I always change both ownership & permissions.
I set my data partition to similar permissions as /home.

If mounted at /mnt/data:

 sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

---

