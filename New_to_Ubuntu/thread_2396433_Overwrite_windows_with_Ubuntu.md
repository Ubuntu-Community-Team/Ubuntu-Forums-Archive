---
title: "Overwrite windows with Ubuntu"
date: 2018-07-15
forum: New to Ubuntu
---

### Post by fredh3 on 2018-07-15
Hi, I have windows computer that I wanted to switch to ubuntu. I didn't want to dual boot, I wanted to wipe my computer and replace it with Ubuntu. I followed the steps in the [tutorial]("https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0") and opted for "Erase disk and install Ubuntu". However, I also (rather ignorantly) checked "Use LVM". I continued with the installation, rebooted, and ubuntu launched just fine. However, I was digging around and found that under /dev I have a number of disk partitions, namely *Computer,* *Windows8_OS, LENOVO, LRS_ESP *(see attachment)*. *I am able to navigate to these disks and open **all** the contents of my "old" computer. The Windows8_OS disk specifically is taking 459GB/957GB on my hard disk, and Computer, which holds my ubuntu files, has been allocated a measly 22GB of which 7GB remain. As stated at the beginning, I don't want this; I want to wipe my old windows machine and completely replace it with Ubuntu. 

Where did I go wrong and how can I fix this? My computer is a Lenovo Y510P with windows 10 (it came stock with Windows 8).

---

### Post by oldfred on 2018-07-15
Those are showing on sdb. Do you have two drives?
Post these:
sudo parted -l
Mount all partitions:
df -h

---

### Post by fredh3 on 2018-07-15
```
fredh3@LinuxBomber:~$ sudo parted -l
[sudo] password for fredh3: 
Model: ATA LITEONIT LSS-24L (scsi)
Disk /dev/sda: 24.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  538MB   537MB   fat32              boot, esp
 2      538MB   24.0GB  23.5GB                     lvm




Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Warning: failed to translate partition name
Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  1050MB  1049MB  ntfs         Basic data partition          hidden, diag
 2      1050MB  1322MB  273MB   fat32                                      boot, hidden, esp
 3      1322MB  2371MB  1049MB  fat32        Basic data partition          hidden
 4      2371MB  2505MB  134MB                Microsoft reserved partition  msftres
 5      2505MB  960GB   957GB   ntfs         Basic data partition          msftdata
 6      960GB   987GB   26.8GB  ntfs         Basic data partition          msftdata
 7      987GB   1000GB  13.5GB  ntfs         Basic data partition          hidden, diag




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 1028MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  1028MB  1028MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 22.4GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  22.4GB  22.4GB  ext4
```
```
fredh3@LinuxBomber:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.9G     0  3.9G   0% /dev
tmpfs                        789M  2.0M  787M   1% /run
/dev/mapper/ubuntu--vg-root   21G  5.6G   14G  29% /
tmpfs                        3.9G  4.3M  3.9G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0                   1.7M  1.7M     0 100% /snap/gnome-calculator/154
/dev/loop1                    13M   13M     0 100% /snap/gnome-characters/103
/dev/loop4                    13M   13M     0 100% /snap/gnome-characters/69
/dev/loop2                   2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop3                    87M   87M     0 100% /snap/core/4486
/dev/loop6                    15M   15M     0 100% /snap/gnome-logs/37
/dev/loop5                    21M   21M     0 100% /snap/gnome-logs/25
/dev/loop7                   3.4M  3.4M     0 100% /snap/gnome-system-monitor/36
/dev/loop8                    87M   87M     0 100% /snap/core/4917
/dev/loop9                   141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop10                  141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop11                  3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
/dev/sda1                    511M  4.7M  507M   1% /boot/efi
tmpfs                        789M   20K  789M   1% /run/user/120
tmpfs                        789M   32K  789M   1% /run/user/1000
```

---

### Post by fredh3 on 2018-07-15
I believe I only have one drive. The stock hard drive.

---

### Post by mIk3_08 on 2018-07-15
fredh3, I assume that you already installed the Ubuntu successfully in your machine. I think you can directly format those partition drives that you show us in your uploaded image above then try to merge it. 

Guide on how to merge partitions;
Merge Partitions [Click Here]("https://askubuntu.com/questions/66000/how-to-merge-partitions")
Succesfully merge the two partitions shown using GParted; [Click Here]("https://askubuntu.com/questions/143327/how-can-i-succesfully-merge-the-two-partitions-shown-using-gparted?rq=1")

---

### Post by oldfred on 2018-07-15
It looks like we see two drives.
       Model: ATA LITEONIT LSS-24L (scsi)
Disk /dev/sda: 24.0GB
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sdb: 1000GB 
    
Since first drive is only 24GB is this an SSD, used for Windows Fast start up or hibernation. Or maybe called Intel SRT?
Microsoft required vendors to use hardware to speed boot since Windows actually boots pretty slow. 
Now many systems have larger SSD, but early versions had small SSD and larger hard drive.

Many with your type of hardware put / (root) on SSD to make Ubuntu fast, but then have /home or data on HDD.  Do not know LVM installs, but a bit more difficult to configure if that is what you want.

---

### Post by fredh3 on 2018-07-16
Yes, [COLOR=#666666][FONT=arial]1TB HDD + 24GB SSD. Would it be easier for me to reinstall ubuntu? Why didn't it completely wipe my HDD and all it's partitions?[/FONT][/COLOR]

---

### Post by mIk3_08 on 2018-07-16
I agree with oldfred. you have two drive installed on your machine.

Model: ATA ST1000LM024 HN-M (scsi) 
Disk /dev/sdb: 1000GB

Model: ATA LITEONIT LSS-24L (scsi) 
Disk /dev/sda: 24.0GB

---

### Post by mIk3_08 on 2018-07-16
> **fredh3 said:**
> Yes, [COLOR=#666666][FONT=arial]1TB HDD + 24GB SSD. Would it be easier for me to reinstall ubuntu? Why didn't it completely wipe my HDD and all it's partitions?[/FONT][/COLOR]


you can wipe the data on your HDD in this section;
see image below;

[ATTACH=CONFIG]280426[/ATTACH]

---

### Post by HermanAB on 2018-07-16
While playing with the partition table can be a learning experience, it is probably less hassle and much quicker, to just re-install from scratch.

---

### Post by oldfred on 2018-07-16
Do you need LVM with full drive encryption?
If not reinstall with / on SSD & /home on HDD.

I normally partition in advance and include an ESP on every drive. And I typically have a full install or two on every drive.

You have an ESP - efi system partition on your sda, you you installed in UEFI boot mode. Even if you install to HDD, it will want to use the ESP on sda.

---

### Post by mIk3_08 on 2018-07-16
How was your machine fredh3?

---

### Post by fredh3 on 2018-07-17
> **oldfred said:**
> Do you need LVM with full drive encryption?
If not reinstall with / on SSD & /home on HDD.

I normally partition in advance and include an ESP on every drive. And I typically have a full install or two on every drive.

You have an ESP - efi system partition on your sda, you you installed in UEFI boot mode. Even if you install to HDD, it will want to use the ESP on sda.


So I tried doing that. Basically I got fed up with it all and went about reinstalling. However, when you install ubuntu it only wipes whatever drive you put ubuntu on. So for me everything was put on my SDD and all the windows garbage remained on my HDD. I tried to wipe my HDD using DBAN, but I couldn't get that to work. Basically what I did was reinstall ubuntu on my HDD ( to wipe it clean) and then reinstall again on my SDD. That worked out great as far as wiping the HDD was concerned, I was able to free up the space with gparted, but I still don't know how to keep /root on SDD and put /home on HDD. I'd like to reinstall with /root on SDD and /home on HDD, but I tried that before and there were either some partitions I couldn't remove or I couldn't mount /home to the HDD. I'm a stark-raving beginner with all of this, so it's taking much longer than I'm sure it should. Any help on how to procede from here would be much appreciated. Sorry if i'm not clear with anything.

> **oldfred said:**
> You have an ESP - efi system partition on your sda, you you installed in UEFI boot mode. Even if you install to HDD, it will want to use the ESP on sda.

How do I change that? I don't really know which partition types are appropriate where, other than that my HDD should be ext4.

---

### Post by fredh3 on 2018-07-17
And no, I don't need LVM with full drive encryption.

---

### Post by fredh3 on 2018-07-17
This is what I'm looking at in the installation wizard when I select "Something Else"

---

### Post by oldfred on 2018-07-17
If a beginner, avoid LVM until more knowledgeable. Often used for servers, but required if you want full drive encryption.

With two drives you have to use the Something Else install option. And best to then first create both drives as gpt partitioned and add the ESP - efi system partition as first partition on all drives. 

I use gparted, change partitioning to gpt, and then create the partitions I want. I typically do not want entire larger drive as my data partition or /home.

And then in Something Else choose (change button) ext4 partition on SSD as / (root) and ext4 partition on HDD as /home. 

       I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. You want to do this for both drives.

            Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
[URL="https://gparted.org/news.php"]https://gparted.org/news.php
[/URL]
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 (you can put this on your HDD) 
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found) 
[*]You do not need to create swap, as it either finds existing swap partition, or creates in fstab swapfile entry. 
[/LIST]
 
      
 [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
      [/URL]Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do.
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
    [URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by fredh3 on 2018-07-17
Alright, well thanks a lot for that. It took me some time to work through, but I successfully made a new partition table as gpt and reinstalled with ESP as the first partition on both drives. I then made ext4 partition on SSD as / (root) and ext4 partition on HDD as /home, per oldfred's suggestion. That essentially did everything I wanted. Thank you all so much for your help with this process!

---

### Post by oldfred on 2018-07-17
Glad that worked. 

You can change to [Solved].

---

