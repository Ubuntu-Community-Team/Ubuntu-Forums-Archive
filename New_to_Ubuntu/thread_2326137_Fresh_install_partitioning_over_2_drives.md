---
title: "Fresh install partitioning over 2 drives"
date: 2016-05-28
forum: New to Ubuntu
---

### Post by jub2 on 2016-05-28
I'm doing a fresh install of Ubuntu on a laptop with 2 drives. I'm familiar with doing an install using the following four partitions:

/boot
Swap
/
/home

Questions:
1. For dual boot setups (Windows/Linux), I used /boot so that grub2 doesn't mess with the Windows bootloader in the drive's MBR. But for a single boot ubuntu installation, is there any reason to create a /boot partition?

2. For a single boot installation, can I place the swap partition on the secondary drive? And use the entire primary drive for / and /home? Or would I be better served to keep swap partition on primary drive and /home on the secondary drive? Both drives are solid state drives.

3. If I have /home on the primary drive for data, and wanted to create a partition on the secondary drive for more data, what should I map it to?

---

### Post by oldfred on 2016-05-28
Most desktops do not need a /boot partition. Some server or server type installs or full drive encryption may need a /boot.

Having a /boot does not change with MBR partitioning that system only boots from MBR. 
But with two drives you have two MBRs, so one boot loader can be in sda, and another in sdb.

Is system UEFI or just BIOS?
But if only booting Ubuntu, I suggest gpt partitioning. It does require a bios_grub partition for BIOS boot and/or an ESP - efi system partition for UEFI. I actually have put both partitions on new drives and now larger flash drives for several years, as old system was BIOS, but knew I would eventually get a UEFI system.

It does not matter where swap is, if you have 4GB or more of RAM, you may never use swap anyway. I suggest 2GB just in case for swap.
Only if editing videos or want an entire large DB in RAM may you need larger swap.

My normal install is a 25 to 30GB / (root) partition with /home inside it on my SSD. And I then put all my data on my HDD. With two SSD, not sure it matters.
       Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413) 
    
Because I have data on HDD in /mnt/data, and I do not want it to show in Nautilus left panel I use /mnt not /media.
And I put all folders normally in /home in my data partition and link to /home. Again with two SSD, not sure it matters.

Is one SSD significantly faster than the other?

---

### Post by jub2 on 2016-05-28
> **oldfred said:**
> Most desktops do not need a /boot partition. Some server or server type installs or full drive encryption may need a /boot.

Having a /boot does not change with MBR partitioning that system only boots from MBR. 
But with two drives you have two MBRs, so one boot loader can be in sda, and another in sdb.

Is system UEFI or just BIOS?BIOS

> **oldfred said:**
> But if only booting Ubuntu, I suggest gpt partitioning. It does require a bios_grub partition for BIOS boot and/or an ESP - efi system partition for UEFI. I actually have put both partitions on new drives and now larger flash drives for several years, as old system was BIOS, but knew I would eventually get a UEFI system.I've never used GPT partitioning before. Sounds like it will work fine with BIOS machines.

Would Win 7 work on a virtual machine on a GPT partitioned ubuntu machine? Or does the virtual machine's operating system (in this case Win 7) not see the physical drive's partitioning, making it irrelevant?

> **oldfred said:**
> 
It does not matter where swap is, if you have 4GB or more of RAM, you may never use swap anyway. I suggest 2GB just in case for swap.
Only if editing videos or want an entire large DB in RAM may you need larger swap.Thanks. This machine has 8GB RAM, so I don't expect swap to get used a lot.

> **oldfred said:**
> 
My normal install is a 25 to 30GB / (root) partition with /home inside it on my SSD. Doesn't that mean your app settings are kept separate from your other data?

> **oldfred said:**
> Is one SSD significantly faster than the other?The primary SSD is slower than the secondary. I could swap them, but that would require a couple of adapters. One is microSATA and the other is mSATA.

---

### Post by oldfred on 2016-05-28
I wanted my app settings on my faster drive. They are in /home.
It is only data like Documents, Video, Music folders that are in /mnt/data partition on HDD.

Do not know about virtual installs. That perhaps should be a separate thread in the virtual sub-forum?
When I still had XP I had it on a MBR partitioned drive and Ubuntu on a gpt partitioned drive. That system was BIOS only.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

I have multiple installs and normally have at least one install on every drive, even if just a data drive. And often a full install on a larger flash drive in a smaller partition as it does not get much added, just an emergency boot.


 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by jub2 on 2016-05-29
I went with your suggestion for GPT partitioning. Thanks for pointing out the need for a bios_grub partition for BIOS machines.

For anyone looking to use GPT and LVM on a BIOS machine, here's what worked for me:
I [used srs5694's post]("http://ubuntuforums.org/showthread.php?t=1563699&p=9786933#post9786933") to use gdisk to GPT partition the two drives. Then I flagged the partitions (except for the bios_grub partition) as 'lvm'; then set up LVM and created logical volumes. Then installed linux from a Live iso (Kubuntu, in my case) and selected installation type 'manual' - this is where I mounted the respective logical volumes to /, swap, /home, /mnt/data1, /mnt/data2. The installer seems to have found sda1 (bios_grub partition) and installed grub2 there, as I am able to boot into Kubuntu just fine.

oldfred (or anyone else reading this), what I'd like to do now is 'map' the usual data directories of Downloads, Documents, Pictures, Videos, Music to subdirectories in /mnt/data1 (so basically the only thing that gets stored in /home are settings and configurations files). I found this explanation: [https://community.linuxmint.com/tutorial/view/1609](https://community.linuxmint.com/tutorial/view/1609)

It walks through mounting /mnt/data (I don't think I need to do this since this mounting was set up during installation), and then taking ownership of the mount point via
> sudo chown -R yourusername: /mnt/data - not sure if I need to do this step. Wouldn't I have ownership of the mount point by way of mounting the logical volume during installation?

Edit: scratch that, looks like I do need to execute chown since I wasn't able to make subdirectories in /mnt/data1 until executing chown.

---

### Post by oldfred on 2016-05-29
I did not know installer let you mount data partitions.
But I have all that, and below in a script so each test install just needs script run to have everything in the right place.
Saved my commands (history) in terminal to bash file from first time & edited with more of it as time went by.

I always do a chown & chmod on my mount points. Not sure if that is required or not. If already mounted you do not mount again.
       sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data 

You can check if mounted by 
mount
or 
cat /etc/fstab

I think first one shows details.

 [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata) 


 Do not run this if you already have data in any of these folders:
rm -rf ~/{Desktop,Documents,Downloads,Music,Pictures,Videos}
mkdir -p /mnt/data/{Desktop,Documents,Downloads,Music,Pictures,Videos}
If in your home, so that is the place where you want links, finds folders in data partition & links them:
for i in `echo /mnt/data/*`;do ln -s $i; done
Another version I have seen:
for folder in Desktop Documents Downloads Music Pictures Videos; do ln -s /media/storage/${folder} /home/<username>/${folder} 

Do not know LVM, so do not know if the mounts are then different?

---

### Post by jub2 on 2016-05-29
> **oldfred said:**
> I did not know installer let you mount data partitions.At the "Installation type" selection screen, I selected 'manual' mode, and then the installer shows all the disks, partitions, AND logical volumes. At that point you can mount those partitions or logical volumes. And using gdisk earlier, I created logical volumes for data.

> **oldfred said:**
> 
Do not know LVM, so do not know if the mounts are then different?Actually I didn't have to do the mounting or fstab editing the article linked in my last post suggested. Since I performed that mounting during the install, it's already in the fstab file, so it auto-mounts on bootup. I only needed to take ownership of the mount point, create the subdirectories (Documents Downloads etc), and symlink those subdirectories to /home/username.

---

