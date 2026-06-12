---
title: "Ubuntu GNU/Linux 10.04 migration from HDD to SSD"
date: 2010-05-23
forum: Outdated Tutorials &amp; Tips
---

### Post by alpharesearch on 2010-05-23
I want to write down what I did so I don't forget - and this post may serves as a howto for other users.

[SIZE="5"]Setup[/SIZE]

First I started my PC up with the HDD and installed bootchart and rebooted my PC 3-5 times (wait 5 min in between) to get some readings how the system performs with the old HDD. When we are finished we will do that again with the SSD and than we can see if the $500 was a good investment.

[IMG]http://www.alpharesearch.de/ocz/hdd_bootchart.png[/IMG]
The little red x is when Firefox starts up...

[SIZE="5"]Hardware and BIOS[/SIZE]

I bought a 50 GB Vertex LE and a 100GB Vertex LE (thanks Newegg!). I also had to order a 2.5" to 3.5" mounting bracket for $5.99, to make this in China in large quantities should not cost more that a couple of cents so please OCZ include something with your product.
I still had two SATA II cables at hand, so I didn't need one... but in my opinion it would make sense to offer a retrial box with SSD+bracket+cable for a little more and a OEM box with just the SSD of course.

In the next step I installed everything in my PC and changed the BIOS IDE setting to AHCI.

[SIZE="5"]First Benchmark[/SIZE] 

Than I use the 10.04 install CD to boot into a independent live CD system  Please note that the Live CD must be the same as the system you are having - either 32-bit or 64-bit (if not then the chroot later will fail)... 
First I started the Gnome Disk Utility (System->Administration->Disk Utility) to check if my system can handle the SSD. You can only perform the Read/Write Test if the disk is empty so now is the best time to do this type of benchmark. Here are my results and it looks just like advertised :) 
[IMG]http://www.alpharesearch.de/ocz/Screenshot-50 GB Solid-State Disk (ATA OCZ VERTEX-LE) – Benchmark.png[/IMG]
[IMG]http://www.alpharesearch.de/ocz/Screenshot-100 GB Solid-State Disk (ATA OCZ VERTEX-LE) – Benchmark.png[/IMG]

[SIZE="5"]Partitioning[/SIZE] 

The next step is to create the partitions, the Disk Utility could do this but I wanted the correct alignment so I used the  [Linux%20-%20Tips,%20tweaks%20and%20alignment"]fdisk method from this forum]("http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment). I need one root (/) a /home and a /boot (for future RAID) directory. I will use the swap partition from on my existing HDD. 

sudo fdisk -H 32 -S 32 /dev/sda starts for first hard drive, use the Disk Utility to find your device name, then use "o" creates a new partition table and "n" creates the partitions, "t" with 83 sets the partition type to linux, and "w" writes everything to disk. [Linux%20-%20Tips,%20tweaks%20and%20alignment"]Here is a step by step instruction.]("http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)

Thanks to TortureTest for this part:
```
$ sudo fdisk -H 32 -S 32 /dev/sda

The number of cylinders for this disk is set to 15711.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): o
Building a new DOS disklabel with disk identifier 0x8cb3d286.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

The number of cylinders for this disk is set to 15711.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-15711, default 1): 2
Last cylinder, +cylinders or +size{K,M,G} (2-15711, default 15711):
Using default value 15711

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 83

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
```

Here are my result:
[IMG]http://www.alpharesearch.de/ocz/fdisk.png[/IMG]

[SIZE="5"]Copy your files[/SIZE] 

[For the next copy step I used this article as an inspiration.]("http://www.linuxjournal.com/content/copy-your-linux-install-different-partition-or-drive") Still in the live CD system you can use the Disk Utility to mount both your old HDD partition and the new SSD partition. To copy use this command: sudo cp -afv /path/to/source/* /path/to/destination (Don’t forget the asterisk after the source path and just copy the path from Disk Utility or Nautilus). Unmount both partitions with Disk Utility and repeat this for all your other partitions.

The only file you need to change on the new SSD root partition is the path/to/new/ssd/etc/fstab: I used "sudo gedit /media/large UUID number/etc/fstab" in command line to do this. Replace the HDD UUID with the SSD UUID for all your directories. To see all the UUIDs use this command: ls -l /dev/disk/by-uuid/ or Disk Utility will show the UUID as mount point name if you never entered a partition name. Unmount all drives.

[SIZE="5"]Make drive boot with GRUB 2[/SIZE] 

The new Ubuntu uses Grub 2 so there are some other steps necessary, but if you still use Grub 1 just [follow the link]("http://www.linuxjournal.com/content/copy-your-linux-install-different-partition-or-drive") above for the rest.


[For Grub 2 I used METHOD 3 - CHROOT from here]("https://help.ubuntu.com/community/Grub2") 

Still in Live CD Desktop in a terminal use sudo fdisk -l (the switch is a lowercase "L") again to remember the device names to use in the next step. Now you need to mount the file system to the /mnt folder. 
Mount your new SSD system root partition, substitute the correct partition: sda1, sdb5, etc. 
sudo mount /dev/sdXX /mnt # Example: sudo mount /dev/sda1 /mnt

Only if you have a separate boot partition, sdYY is the /boot partition designation (for example sdb3)
sudo mount /dev/sdYY /mnt/boot 

Mount the critical virtual filesystems:
      sudo mount --bind /dev  /mnt/dev
      sudo mount --bind /proc /mnt/proc
      sudo mount --bind /sys  /mnt/sys

Chroot into your normal system device:
      sudo chroot /mnt

To update the grub files run: 
      update-grub

Now reinstall GRUB 2:
Substitute the correct device - sda, sdb, etc. Do not specify a partition number. 

      grub-install /dev/sdX

Exit chroot: CTRL-D on keyboard

Unmount virtual filesystems:
      sudo umount /mnt/dev
      sudo umount /mnt/proc
      sudo umount /mnt/sys

If you mounted a separate /boot partition:
            sudo umount /mnt/boot 

Unmount last device:
      sudo umount /mnt

Now reboot and take the CD out and it should boot with the new SSD, you can use the Disk Utility to check for this. 

[SIZE="5"]Compare your Bootcharts[/SIZE]

As you can see the performance gain is huge!
[IMG]http://www.alpharesearch.de/ocz/ssd_bootchart.png[/IMG]
The little red x is when Firefox starts up...

I will hopefully be able to edit this post soon to add more details.

Regards,
Markus Schulz

---

### Post by alpharesearch on 2010-06-30
Here are the additional steps for the raid0 I did:

1. If you boot in Ubuntu Live CD you need to install the mdadm with:
sudo apt-get install mdadm

2. I did the similar partitioning steps except for ID (t command) is 'fd' for Linux raid autodetect.
```

$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 50.0 GB, 50020540416 bytes
32 heads, 32 sectors/track, 95406 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00084b62

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       28674    14680576   fd  Linux raid autodetect
/dev/sdb2           28675       95406    34166784   fd  Linux raid autodetect
$ sudo fdisk -l /dev/sdc

Disk /dev/sdc: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009ea19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1828    14680576   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sdc2            1828        6082    34166784   fd  Linux raid autodetect
Partition 2 does not end on cylinder boundary.
/dev/sdc3            6082        6146      519873   83  Linux
/dev/sdc4            6147       12161    48315487+   7  HPFS/NTFS
markus@markus-desktop:~$ 

```

3. create the raid array:
```
$ sudo mdadm --create /dev/md0 --chunk=512 --level=raid0 --raid-devices=2 /dev/sdb1 /dev/sdc1
mdadm: array /dev/md0 started.
$ sudo mdadm --create /dev/md1 --chunk=512 --level=raid0 --raid-devices=2 /dev/sdb2 /dev/sdc2
mdadm: array /dev/md1 started.
$ sudo su
#  sudo mdadm --examine --scan >> /etc/mdadm/mdadm.conf 

```
[IMG]http://www.alpharesearch.de/ocz/Screenshot-70 GB RAID-0 Array (70 GB RAID-0 Array) – Benchmark.png[/IMG]

4. format all the new partitions and copy all the files to md0 and md1 and boot partition:
sudo cp -afv /path/to/source/* /path/to/destination

5. I'm not sure if i have to do this, but while I was in change root I also did a:
update-initramfs -u
apt-get install mdadm
mdadm --examine --scan >> /etc/mdadm/mdadm.conf 

6.Looks like the raid is very fast but the boot is not faster...
[IMG]http://www.alpharesearch.de/ocz/raid_bootchart.png[/IMG]

7. To me it feels like raid may perform a little bit better after boot, but just one ssd alone is very good. 

Regards,
Markus Schulz

PS: I suggest to save the mdadm configuration file to a non raid file system, if you do so you can copy the file later to the live CD and use the 
mdadm --assemble --scan
command to reassemble your raid.

---

