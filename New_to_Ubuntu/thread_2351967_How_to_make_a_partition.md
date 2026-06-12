---
title: "How to make a partition?"
date: 2017-02-08
forum: New to Ubuntu
---

### Post by usrandrd3 on 2017-02-08
I am new to Ubuntu and i have installed the OS with LVM option. But is not intuitive how to create a new partition, different than OS installation, to put there a virtual machine or files.

```

df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         2,9G     0  2,9G   0% /dev
tmpfs                        587M  9,0M  578M   2% /run
/dev/mapper/ubuntu--vg-root  681G   62G  585G  10% /
tmpfs                        2,9G   23M  2,9G   1% /dev/shm
tmpfs                        5,0M  4,0K  5,0M   1% /run/lock
tmpfs                        2,9G     0  2,9G   0% /sys/fs/cgroup
/dev/sda1                    472M  169M  279M  38% /boot
tmpfs                        587M  128K  587M   1% /run/user/1000

```

I installed GParted but i cannot resize this partition to 100 GB to make some free space to be used to create a new partition

[IMG]https://s27.postimg.org/qxfcmx8er/ubuntu_partitions.jpg[/IMG]

[IMG]https://s30.postimg.org/b20eaole9/ubuntu_partitions_2.jpg[/IMG]


Whic solutions i have?  LVM via command line (risky) or boot with GParted Live on USB ?

---

### Post by oldfred on 2017-02-08
If you are new LVM may not be the best choice. But if you must have full drive encryption you have to use it.

You have to use LVM tools to manage partitions, not standard partition tools like gparted, parted, fdisk or gdisk.

LVM is an advanced partitioning system. 
       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[URL="https://wiki.archlinux.org/index.php/LVM"]https://wiki.archlinux.org/index.php/LVM
[/URL]
 lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html) 

[URL="https://wiki.archlinux.org/index.php/LVM"]
[/URL]

---

### Post by usrandrd3 on 2017-02-09
I do not need encryption, i need a direction to which method is easier to create a partition.

---

### Post by Bucky Ball on 2017-02-09
> **usrandrd3 said:**
> I do not need encryption, i need a direction to which method is easier to create a partition.

You installed with LVM. You have encryption. In that case, oldfred has just given you a bunch of information. If you don't need encryption, not sure why you installed with LVM. Just makes things harder.

My advice would be start again and forget LVM.

---

### Post by oldfred on 2017-02-09
> My advice would be start again and forget LVM.                 
+1

This is for standard partitions, not LVM.
       gparted & fdisk instructions:
Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php) 

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

If not dual booting with Windows, I also prefer to use gpt partitioning over the 35 year old default MBR(msdos).

I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 
But with gpt you need either a bios_grub partition for BIOS boot or an ESP - efi system partition for UEFI boot. Even long before my first UEFI system I started adding both bios_grub for current boot, but ESP for future so I could move drive into new UEFI system.

 [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd) [URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by usrandrd3 on 2017-02-09
I want to use only Ubuntul, not dual os. I will use Windows on a virtual machine.

I have found that is better to reinstall and make partitions. I have installed as default first to format those LVM mappers, then i have reinstalled and made a few partitions. 

I do not know if good or bad, but i have made
- 1 partition /  as root for OS
- 1 partition /virma  for Virtual Machines 
- 1 partition /home  (i do not understand exactly the benefits, but i suppose i can reinstall Ubuntu without losing personal files)


```

df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            2.9G     0  2.9G   0% /dev
tmpfs           587M  8.8M  578M   2% /run
/dev/sda1        92G  5.7G   82G   7% /
tmpfs           2.9G   38M  2.9G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.9G     0  2.9G   0% /sys/fs/cgroup
/dev/sda6        74G   52M   70G   1% /virma
/dev/sda7       459G  9.6G  426G   3% /home
tmpfs           587M   72K  587M   1% /run/user/1000

```

```
[COLOR=#111111][FONT=Consolas]sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL[/FONT][/COLOR]
```
[IMG]https://s24.postimg.org/4edfs6ntx/hdd_1.png[/IMG]


```
[COLOR=#111111][FONT=Consolas]sudo fdisk -l[/FONT][/COLOR]
```
[IMG]https://s28.postimg.org/tv74r9kfx/hdd_2.png[/IMG]


Last image shows an error and i don't know how bad it is or if can be fixed.

---

### Post by oldfred on 2017-02-09
You are using the 35 year old MBR(msdos) partitioning.
That uses primary, extended and then logical partitions to get past the 4 partition limit that MBR has.

But you only write into the primary & logical partitions. The extended is only a container for all the logical. So the extended does not have to start on sector boundaries.

The requirement for sector boundaries is for SSD & new 4K drives.
 [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) 

If only running Linux you can use the newer gpt partitioning whether booting in BIOS or UEFI.
It just is gpt requires either a bios_grub partition for BIOS boot or the ESP - efi system partition for UEFI boot.

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

