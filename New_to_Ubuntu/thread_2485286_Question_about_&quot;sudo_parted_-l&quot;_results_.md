---
title: "Question about &quot;sudo parted -l&quot; results of new disk"
date: 2023-03-25
forum: New to Ubuntu
---

### Post by bhubunt on 2023-03-25
Hi,
I now have a new disk installed on my Lenovo x230. 

I have questions about the results for the "sudo parted -l" command line in the terminal 

```
 Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 31,0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  31,0GB  31,0GB  fat32        Microsoft Basic Data  msftdata


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vgubuntu-root: 478GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0,00B  478GB  478GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vgubuntu-swap_1: 1028MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0,00B  1028MB  1028MB  linux-swap(v1)


Error: /dev/mapper/sda3_crypt: unrecognised disk label
Model: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/sda3_crypt: 479GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

 
```

I am not sure why the disk label is not recognized as I put in a SanDisk SSD Plus. Also, the partition table of sda 3 is unknown.

---

### Post by bhubunt on 2023-03-25
And here is more code 


```
 ThinkPad-X230:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/' | sed 's/^[\|,`]-/\|_/g'
NAME                    SIZE FSTYPE      LABEL MOUNTPOINT                    MODEL
sda                   447,1G                                                 SanDisk_SSD_PLUS_480GB
&#9500;&#9472;sda1                  512M vfat              /boot/efi                     
&#9500;&#9472;sda2                  732M ext4              /boot                         
&#9492;&#9472;sda3                445,9G crypto_LUKS                                     
  &#9492;&#9472;sda3_crypt        445,9G LVM2_member                                     
    &#9500;&#9472;vgubuntu-root     445G ext4              /                             
    &#9492;&#9472;vgubuntu-swap_1   980M swap              [SWAP]                        
green@green-ThinkPad-X230:~$ grep . /proc/diskstats | grep -v 'loop'
   8       0 sda 27625 7764 2778815 37263 61207 58246 7036090 126371 0 77532 171666 0 0 0 0 11457 8030
   8       1 sda1 176 1018 13846 175 2 0 2 0 0 176 176 0 0 0 0 0 0
   8       2 sda2 130 31 9386 131 31 13 232 91 0 304 223 0 0 0 0 0 0
   8       3 sda3 27076 6715 2747543 36702 61172 58233 7035856 126279 0 77248 162981 0 0 0 0 0 0
 253       0 dm-0 33645 0 2744594 56936 118865 0 7035856 1068476 0 78040 1125412 0 0 0 0 0 0
 253       1 dm-1 33338 0 2730914 56540 116733 0 7035856 831440 0 77704 887980 0 0 0 0 0 0
 253       2 dm-2 241 0 11480 444 2 0 0 0 0 272 444 0 0 0 0 0 0


```

```
 ThinkPad-X230:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/' | sed 's/^[\|,`]-/\|_/g'
NAME                    SIZE FSTYPE      LABEL MOUNTPOINT                    MODEL
sda                   447,1G                                                 SanDisk_SSD_PLUS_480GB
&#9500;&#9472;sda1                  512M vfat              /boot/efi                     
&#9500;&#9472;sda2                  732M ext4              /boot                         
&#9492;&#9472;sda3                445,9G crypto_LUKS                                     
  &#9492;&#9472;sda3_crypt        445,9G LVM2_member                                     
    &#9500;&#9472;vgubuntu-root     445G ext4              /                             
    &#9492;&#9472;vgubuntu-swap_1   980M swap              [SWAP]  
  
```

---

### Post by TheFu on 2023-03-25
You installed with encryption enabled.  In Ubuntu systems, when that selection is made, by default, you'll get MBR partitioning with sda3 (3rd partition) as the LUKS container.  

To make running the OS easier, LVM2 is used inside the LUKS container. That way, we can resize and add LVM2 objects called PVs, VGs, and LVs.  From a very, very, high level, an LV can be considered a really flexible partition.  To see those objects, 
```
sudo pvs
sudo vgs
sudo lvs
```
will show more details, though using lsblk is also handy to see the relationships between the disk, partitions, LUKs, and LVM objects.
If you decide to keep this install, the first thing I always do is to resize the "root" LV to 35G, set the LV for swap to be 4.1G (desktops), and add home and var LVs for those locations.

A few years ago, I drew a diagram showing this setup. Hope it is helpful. See attached.
BTW, you might want some aliases to make monitoring storage cleaner, 
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'

```
Try them out. See if you like. They should remove all non-real storage, while keeping real mounts of real storage, including networked storage. If you run lxd, I have a different dft alias that removes those objects.

---

### Post by bhubunt on 2023-03-25
Thanks, as always, TheFu, for the great answer.

So to apply what you said about encryption to my question in post #1: 

is the disk label not recognized and the partition table unknown because of encryption? 

Does the encryption block the "sudo parted -l" command from generating that information, or not? 

And, second, how can I find out the partition table of this disk another way, with a different command?

---

### Post by TheFu on 2023-03-25
> **bhubunt said:**
> is the disk label not recognized and the partition table unknown because of encryption? 

Does the encryption block the "sudo parted -l" command from generating that information, or not? 

It should work.  Perhaps the BIOS, SSD firmware and Linux kernel aren't working well.  I'd be inclined to see of there were updates for the BIOS and SSD firmware.  I have a Samsung SSD.
```
$ sudo parted -l
....
Model: Samsung SSD 970 EVO 500GB (nvme)
Disk /dev/nvme0n1: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  53.5MB  52.4MB  fat32        EFI   boot, esp
 2      106MB   735MB   629MB   ext4         BOOT
 3      840MB   500GB   499GB                LVM   lvm
....
```
And my lsblkt output (for just that device):
```
NAME                                  SIZE TYPE FSTYPE      LABEL      MOUNTPOINT
nvme0n1                             465.8G disk                        
&#9500;&#9472;nvme0n1p1                            50M part vfat        EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                           600M part ext4        boot       /boot
&#9492;&#9472;nvme0n1p3                           465G part LVM2_member            
  &#9500;&#9472;vg00-swap                         4.1G lvm  swap                   [SWAP]
  &#9500;&#9472;vg00-root--00                      35G lvm  ext4        root       /
  &#9500;&#9472;vg00-var                           55G lvm  ext4        var        /var
  &#9500;&#9472;vg00-home                          26G lvm  ext4        home       /home
  &#9492;&#9472;vg00-lxd                           50G lvm  zfs_member  lxd        
```
I removed some LVs that are in the same VG to simplify things. I don't have an encrypted setup easily available. Sorry.  I have a laptop that I haven't booted in a few years with a LUKS+LVM setup. Don't know which Ubuntu release it has.  Laptops are never very important to me and never hold important data.

> **bhubunt said:**
> 
And, second, how can I find out the partition table of this disk another way, with a different command?
If parted isn't working, try **fdisk**, gdisk, sgdisk, gparted.

Here's the fdisk output from my local SSD:
```
Disk /dev/nvme0n1: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: Samsung SSD 970 EVO 500GB               
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 23C624DB-26C7-4D91-99E9-971BFB742E3D

Device           Start       End   Sectors  Size Type
/dev/nvme0n1p1    2048    104447    102400   50M EFI System
/dev/nvme0n1p2  206848   1435647   1228800  600M Linux filesystem
/dev/nvme0n1p3 1640448 976773119 975132672  465G Linux LVM

```
During the install, I manually setup the storage the way I wanted (partitions and LVM stuff), BEFORE the "do something else" option.  I was tired of the less than great defaults which weren't meeting my needs.
And just to bring it all together, my 'dft' alias output:
```
$ dft
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-root--00                   ext4   35G   11G   22G  33% /
/dev/nvme0n1p2                              ext4  574M  278M  254M  53% /boot
/dev/nvme0n1p1                              vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg00-home                       ext4   26G  9.8G   15G  41% /home
/dev/mapper/vg00-var                        ext4   54G   34G   18G  66% /var

```
Heck, while I'm sharing ... the /etc/fstab:
```
#   Main OS areas
/dev/vg00/root-00                          /         ext4 defaults 0 1
/dev/vg00/home                             /home     ext4 defaults 0 1
/dev/vg00/var                              /var      ext4 defaults 0 1
/dev/vg00/swap                             none      swap sw 0 0
# /boot was on /dev/nvme0n1p2 
UUID=8db5cac8-0450-4389-b6ec-44c3ad4c1e12  /boot     ext4 defaults 0 1
# /boot/efi was on /dev/nvme0n1p1 
UUID=2DF4-A658                             /boot/efi vfat defaults 0 1

```
Just so you know, LVM is LVM is LVM across all Linuxen.  Find a tutorial, don't worry about the OS/release/distro. They all use the same commands that work the same way for anything that starts with lv* vg* pv*. If you use tab-completion, you can see which commands are available.  

95% of the time, I use **lvextend**, since the trick with LVM storage is to allocate only the size/amount of storage to an LV as will be needed for the next 3-6 months.  Leave most of it unallocated, but still used by the VG.  As you can see above, my SSD has 500GB, but I'm using less than 200GB. This allows for LVM snapshots and some other things that are nice to have which only volume managers support (ZFS, LVM, BTRFS).  Resizing up an LV takes less than 5 seconds and I can add more storage exactly where it is needed, when it is needed, all while the system is very busy. ZERO downtime.

---

### Post by bhubunt on 2023-03-25
Here goes -- the results for the command "sudo fdisk -l"

I should specify that I just installed the Ubuntu 20.04 OS desktop from a flash drive.

Any comments?

```
 Disk /dev/loop0: 8,98 MiB, 9396224 bytes, 18352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 116,78 MiB, 122433536 bytes, 239128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 55,45 MiB, 58130432 bytes, 113536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 219 MiB, 229638144 bytes, 448512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 65,1 MiB, 68259840 bytes, 133320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 50,98 MiB, 53432320 bytes, 104360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 219 MiB, 229638144 bytes, 448512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 49,86 MiB, 52260864 bytes, 102072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 447,13 GiB, 480103981056 bytes, 937703088 sectors
Disk model: SanDisk SSD PLUS
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 2C33D6E3-DF94-4533-ACC1-371EC48492BB

[B]Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624   2549759   1499136   732M Linux filesystem
/dev/sda3  2549760 937701375 935151616 445,9G Linux filesystem[/B]


Disk /dev/mapper/sda3_crypt: 445,92 GiB, 478780850176 bytes, 935118848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/vgubuntu-root: 444,96 GiB, 477752197120 bytes, 933109760 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/vgubuntu-swap_1: 980 MiB, 1027604480 bytes, 2007040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop8: 320,45 MiB, 336003072 bytes, 656256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 55,62 MiB, 58310656 bytes, 113888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 91,7 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

 
```

---

### Post by TheFu on 2023-03-25
The only relevant parts are:
```

Disk /dev/sda: 447,13 GiB, 480103981056 bytes, 937703088 sectors
Disk model: SanDisk SSD PLUS
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 2C33D6E3-DF94-4533-ACC1-371EC48492BB

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624   2549759   1499136   732M Linux filesystem
/dev/sda3  2549760 937701375 935151616 445,9G Linux filesystem


Disk /dev/mapper/sda3_crypt: 445,92 GiB, 478780850176 bytes, 935118848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/vgubuntu-root: 444,96 GiB, 477752197120 bytes, 933109760 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/vgubuntu-swap_1: 980 MiB, 1027604480 bytes, 2007040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

I see that GPT partition table was created. Excellent. I'm crying with happiness due to that. Took much too long for that to become the default.

```
Device       Start       End   Sectors   Size Type
/dev/sda3  2549760 937701375 935151616 445,9G **Linux filesystem**

```
There isn't a "LUKS" partition type, so having a Linux label in the partition table makes perfect sense.
So, fdisk works and parted doesn't.  That seems like a bug worth reporting, assuming the BIOS shows the drive and partitions too.  Of course, anything inside sda3 will not be available until it is opened using **cryptsetup open** ... which is what the /etc/crypttab facilitates pre-boot.

Parted became preferred over fdisk mainly because fdisk didn't support GPT for a few years. That has been solved for a long time.  I don't know which is "better" any more. Basically, I use whichever works.  When I'm setting up a new disk, I actually use ... let me check a script:
**sgdisk** that that tool isn't interactive.  **cgdisk** is a curses-based version. **gdisk** is like **fdisk**.
[Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144](Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144) has more details. Seems that script looks like fst001's script - BECAUSE I STOLE IT!  ;)   Er ... standing on the shoulders of giants!

---

### Post by MAFoElffen on 2023-03-25
Yes... I remember pointing out those links to those tutorials, when helping fst001.

---

### Post by bhubunt on 2023-03-27
> **TheFu said:**
> 

Parted became preferred over fdisk mainly because fdisk didn't support GPT for a few years. That has been solved for a long time.  I don't know which is "better" any more. Basically, I use whichever works.  When I'm setting up a new disk, I actually use ... let me check a script:
**sgdisk** that that tool isn't interactive.  **cgdisk** is a curses-based version. **gdisk** is like **fdisk**.
[Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144](Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144) has more details. Seems that script looks like fst001's script - BECAUSE I STOLE IT!  ;)   Er ... standing on the shoulders of giants!

Great tip.

---

