---
title: "Problems with resizing/allocating space for partitions."
date: 2019-07-03
forum: New to Ubuntu
---

### Post by vysero on 2019-07-03
Today I ran out of space on this partition. I am using Ubuntu 18.04 and I opened up the disks utility. Luckily one of my partitions had an excess of space so I used the resize feature and now I have about 200G's of free space just waiting to be used. There is only one problem I can't add the space to this currently mounted partition... how the heck am I going to go about getting all the juicy memory onto this partition? I tried logging into my Ubuntu 16.04 system but it doesn't have the same resize feature that 18.04 does, any suggestions?

---

### Post by deadflowr on 2019-07-03
Use a Ubuntu live cd/dvd/usb to resize it as that has gparted on it and will allow resizing since the file system won't be mounted.
Normal partitions need to be unmounted in order to manipulate them.

---

### Post by vysero on 2019-07-03
I stuck in the disk I used to install Ubuntu 18.04 selected Install Ubuntu option but it doesn't work. All it does is try to run the temp free version of Ubuntu it wont actually let me install Ubuntu... can I run gparted as a stand alone application?

---

### Post by TheFu on 2019-07-03
> **vysero said:**
> I stuck in the disk I used to install Ubuntu 18.04 selected Install Ubuntu option but it doesn't work. All it does is try to run the temp free version of Ubuntu it wont actually let me install Ubuntu... can I run gparted as a stand alone application?

NO!!!!!!!!   Don't "install Ubuntu"!!!!!!!!   That could wipe everything!

You want to use an ubuntu/xubuntu/lubuntu 18.04 boot disk/flash drive and **TRY UBUNTU** to do this stuff.

Also, if you installed using LVM, adding more storage while running is just a few commands. If you didn't choose LVM at the install time, then the storage must be contiguous with the other storage to be extended.

The **lsblk** command will show if you are using LVM or not.

---

### Post by SeijiSensei on 2019-07-03
You don't need to add the space to the existing root partition. You need only mount it into the filesystem at a separate "mount point."  The simplest solution is just to create a new location like /data and mount the new filesystem there.  Here's how I would do it from the command prompt, if the new partition is /dev/sda2.

```

sudo mkdir /data
sudo mkfs -t ext4 /dev/sda2
sudo mount /dev/sda2 /data

```

If you want to allow all users read/write access to this partition, you can use (after mounting):

```
sudo chmod -R 777 /data
```

For a more nuanced solution, read [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

To make this permanent, you'll need to edit the file /etc/fstab as root (sudo nano /etc/fstab) and add the line

```
/dev/sda2     /data     ext4     defaults     0 0
```

---

### Post by Dennis N on 2019-07-03
> how the heck am I going to go about getting all the juicy memory onto this partition?
You could use the free space you made to create a new partition, and then mount it from Ubuntu as a data partition for storage.

---

### Post by vysero on 2019-07-03
Alright I manged to figure it out using the Ubuntu startup disk and gparted. Now I think I want to go a few steps further. I have attached a screenshot of the situation of my 1Tb Hard Disk. Partition 7 is the partition I recently increased the size of and (as is evident by the star and triangle in the bottom right) I believe has this versions of Ubuntu 18.04 on it. As far as I am concerned everything else on this drive can be deleted and reallocated into this partition. That being said, I am not sure what all on this drive can actually be deleted and reallocated and what has to stay for Ubuntu 18.04 to continue to work properly. For instance, I am assuming SWAP is important? I really dont know what's important here. My Ubuntu 16.04 is actually on the 256 disk shown ubove this 1TB disk on the top left.

Does anyone know exactly what Ubuntu creates when you install a fresh copy of Ubuntu onto a partition? I know Data can go away for instance but there is that EFI System in the way of Partition 7 and what would be the new un-allocated space and for some reason I can't actually move the EFI system partition.

Based on the contents of my 256 GB Disk with Ubuntu 16.04 Ubuntu makes a partition called EFI System, another Called Basic Data and yet another called Linux Swap. Which seems to sugjest (in theory) that I could get rid of Data, partition 4 and the first one is called Windows Reserved... not sure what that's for I have no windows OS on this machine.

---

### Post by oldfred on 2019-07-05
My eyes are not good & screenshot too light to read.
From terminal run this & post in code tags:
sudo parted -l
lsblk -f

The ESP - efi system partition is required for UEFI boot. One ext4 partition is required for / (root), but many like to have system separate from data and either have /home or /data partition(s) as ext4. New versions of Ubuntu now use swap file, so swap partition is not required, but if found it will use it. Bit complicated to undo entry for swap partition and create swap file from scratch, but doable if desired.
Micosoft has a System Reserved partition which is unformatted. Gparted shows it as an error as it is not formatted.  If no Windows you can delete it also. It is used by Windows for serial numbers or hidden info for DRM in Windows.

---

### Post by TheFu on 2019-07-05
> **oldfred said:**
> My eyes are not good & screenshot too light to read.


+1.  I can't read it either.  Text is always preferred.  Please and thank you.

> 
Does anyone know exactly what Ubuntu creates when you install a fresh copy of Ubuntu onto a partition? 

The answer is, "it depends."  During an install you can choose
* wipe the disk.
* wipe the disk and use LVM.
* wipe the disk and encrypt the entire drive (which also uses LVM).
* install next to some other OS
* "Do something else."
What each of those choices does depends on the disk already in the machine, how it is formatted (MBR or GPT) and if your system supports UEFI booting or legacy booting.

**Which is why we've been asking you to run commands!!!! **  We don't know what you have and need those commands to provide good advice.  If you want crap advice, we can guess, be wrong, and have you mad because something important was wiped.

Everyone here is trying to help you.  We all have thousands of posts and recognize each other's handles. These are good people trying to help.  Can you please help us to do that?  Please?

---

### Post by SeijiSensei on 2019-07-05
If you really don't care about preserving what's on the drive already, just choose the default option of wiping the disk clean during installation and using all of it for Ubuntu.

---

### Post by vysero on 2019-07-08
Sure thing:

```
rob@linux:~$ sudo parted -l

Model: ATA ST1000DM010-2EP1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  135MB   134MB                   Microsoft reserved partition  msftres
 2      135MB   250GB   250GB   ntfs            Basic data partition          msftdata
 6      250GB   251GB   538MB   fat32           EFI System Partition          boot, esp
 7      251GB   729GB   478GB   ext4
 4      729GB   983GB   254GB   ext3
 5      983GB   1000GB  17.1GB  linux-swap(v1)


Model: KXG50ZNV256G NVMe TOSHIBA 256GB (nvme)
Disk /dev/nvme0n1: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name                  Flags
 1      1049kB  538MB  537MB   fat32           EFI System Partition  boot, esp
 2      538MB   239GB  238GB   ext4                                  msftdata
 3      239GB   256GB  17.1GB  linux-swap(v1)

rob@linux:~$ lsblk -f
NAME        FSTYPE   LABEL UUID                                 MOUNTPOINT
loop0       squashfs                                            /snap/gnome-logs/61
loop1       squashfs                                            /snap/gnome-logs/57
loop3       squashfs                                            /snap/gnome-3-28-1804/63
loop4       squashfs                                            /snap/core18/1013
loop5       squashfs                                            /snap/gnome-logs/45
loop6       squashfs                                            /snap/gnome-calculator/260
loop7       squashfs                                            /snap/pycharm-community/132
loop8       squashfs                                            /snap/gnome-calculator/352
loop9       squashfs                                            /snap/gnome-calculator/406
loop10      squashfs                                            /snap/gtk-common-themes/1198
loop11      squashfs                                            /snap/core18/1049
loop12      squashfs                                            /snap/gnome-system-monitor/91
loop13      squashfs                                            /snap/pycharm-community/128
loop14      squashfs                                            /snap/core/7270
loop15      squashfs                                            /snap/core/7169
loop16      squashfs                                            /snap/gnome-3-28-1804/59
loop18      squashfs                                            /snap/gnome-3-26-1604/88
loop20      squashfs                                            /snap/gnome-characters/288
loop21      squashfs                                            /snap/gnome-system-monitor/95
loop22      squashfs                                            /snap/gnome-characters/292
loop23      squashfs                                            /snap/gnome-3-26-1604/90
sda                                                             
&#9500;&#9472;sda1                                                          
&#9500;&#9472;sda2      ntfs     DATA  FE2204452204057D                     
&#9500;&#9472;sda4      ext3           82c84240-0d3a-43d6-b525-b7f541499dd3 /media/murchrob/82c84240-0d3a-43d6-b525-b7f541499dd3
&#9500;&#9472;sda5      swap           1c7a8aa0-0f1a-467e-9fce-353494b89ddc 
&#9500;&#9472;sda6      vfat           62D7-A337                            
&#9492;&#9472;sda7      ext4           8a2061b7-f65a-4788-9e8d-aa532b2c0f45 /
sr0                                                             
nvme0n1                                                         
&#9500;&#9472;nvme0n1p1 vfat           30EE-9A72                            /boot/efi
&#9500;&#9472;nvme0n1p2 ext4           5646bf56-bafb-45f0-88c8-b51dd33a7941 
&#9492;&#9472;nvme0n1p3 swap           5e2aa36f-76d8-4273-9fed-5289c6875cb4 
```

---

### Post by TheFu on 2019-07-08
You aren't using LVM on those 2 disks.
Boot from a flash drive with Ubuntu and "Try Ubuntu", then use/install **gparted** and resize the partitions as you like.  It doesn't have to be Ubuntu. It can be xubuntu/lubuntu/ubuntu-mate ... doesn't matter, except it should be the same version installed on the disks.

When doing stuff like this there are a few things necessary for safety.
a) backup anything you don't want to lose onto external storage and disconnect it from the computer.
b) ensure power will not be interrupted as the data is moved around. Don't just use battery power on a laptop.

---

### Post by oldfred on 2019-07-08
Bit surprised to see an ext3 partition, ext4 has been standard since 2009.

And / is on sda, not on NVMe?
NVMe drive is a lot faster than your sda drive.

---

### Post by vysero on 2019-07-08
@oldfred Tbh, I am not even sure how the ext3 partition was created or what for; here are the contents: var->log->os-uninstaller(empty directory) and lost+found which requires sudo to access and is also empty.

---

### Post by oldfred on 2019-07-08
Lost+found is a default.

Perhaps you used Boot-Repair's uninstaller and had that partition, so it saved its logs to that partition. But then it was housecleaned.

If empty, I would reformat or delete & combine with another partition. 

I like to have several partitions. I do multiple installs and have a partition on every drive for ISO which I directly boot with grub & loopmount. And then multiple 25GB / (root) partitions to test new version or different gui or just to experiment.

---

### Post by vysero on 2019-07-08
Alright I got it figure out thanks a lot guys, just like I wanted it!

---

