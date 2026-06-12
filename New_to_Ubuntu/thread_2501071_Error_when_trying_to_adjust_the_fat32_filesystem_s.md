---
title: "Error when trying to adjust the fat32 filesystem size"
date: 2024-09-22
forum: New to Ubuntu
---

### Post by juergen-soemen on 2024-09-22
Hello!

I have expanded my partition where /boot/efi resides, because it was to small for a firmware update.
The issue I have now is, that neither disk, GParted nor fatresize can adjust the file system size.
I also tried to with Ubuntu live booted with USB.


```
juergen@juergen-lap-hp:/$ lsb_release -a 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 24.04.1 LTS
Release:    24.04
Codename:    noble

juergen@juergen-lap-hp:/$ lsblk /dev/nvme0n1p1
NAME      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
nvme0n1p1 259:1    0  **1,3G  0 part**

juergen@juergen-lap-hp:/$ df -h /boot/efi/
Dateisystem    Größe Benutzt Verf. Verw% Eingehängt auf
/dev/nvme0n1p1   **96M**     74M   23M   77% /boot/efi

juergen@juergen-lap-hp:/$ sudo fatresize /dev/nvme0n1p1 -s 1341M -p -v
fatresize 1.1.0 (20240401)
.part(start=3904282624, end=3907028991, length=2746368)
Backtrace has 6 calls on stack:
  6: /lib/x86_64-linux-gnu/libparted.so.2(ped_assert+0x5d) [0x785391aae86d]
  5: fatresize(+0x3e1b) [0x59c278bffe1b]
  4: fatresize(+0x31b8) [0x59c278bff1b8]
  3: /lib/x86_64-linux-gnu/libc.so.6(+0x2a1ca) [0x78539182a1ca]
  2: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0x8b) [0x78539182a28b]
  1: fatresize(+0x3695) [0x59c278bff695]
Bug: Assertion (ped_geometry_test_sector_inside(range, *sector)) at fatresize.c:347 in function snap() failed.
Abgebrochen
```

Please help!

Thanks,
Juergen

---

### Post by TheFu on 2024-09-22
If there's no room to the "right" of the existing partition, then it cannot be resized larger.  This is one of the few times with the image shown by gparted would clearly show if there's room or not.

I've never needed so much storage in the EFI area as you.  A few systems as example:

**One**
```
$ df -Th /boot/efi/
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/nvme0n1p2 vfat   50M  6.1M   44M  13% /boot/efi


```**Two**
```
$ df -Th /boot/efi/
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/nvme0n1p1 vfat   50M  6.1M   44M  13% /boot/efi

```
**Three**
```
$ df -Th /boot/efi/
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda2      vfat  512M   17M  496M   4% /boot/efi
```

**Four**```

$ df -Th /boot/efi/
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/nvme0n1p1 vfat  511M  6.2M  505M   2% /boot/efi
```

The first two are Ubuntu 20.04 systems that have been patched for a few years. Those both have custom partition sizes. I hate wasted space.  My first computer had a 40MB HDD, so the idea that boot code needs even 50MB makes me sick. Bloated.

_Three _is a LM 21.x system where the default installation size jumped to a huge amount and for unrelated reasons.
 I didn't bother trying to customize the partition to what I know is needed.  

_Four _is a LM 22.x system with the default installation. It has LUKS encryption.

I don't multi-boot.  None of my systems use over 20MB.  If you used code-tags, like I have, perhaps reading the columns would be easier?  Please edit your post above and use forum code tags (advanced editor).  Also, it would be helpful to see the output from **parted -l** to see where the partitions are laid out.
```
Model: KXG60ZNV512G NVMe KIOXIA 512GB (nvme)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   2330MB  1792MB  ext4
 3      2330MB  512GB   510GB

$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint   **#  <<<<< great alias to see storage info!**
NAME                TYPE  FSTYPE        SIZE FSAVAIL FSUSE% LABEL MOUNTPOIN
nvme0n1             disk              476.9G                      
&#9500;&#9472;nvme0n1p1         part  vfat          512M  504.8M     1%       /boot/efi
&#9500;&#9472;nvme0n1p2         part  ext4          1.7G    1.2G    17%       /boot
&#9492;&#9472;nvme0n1p3         part  crypto_LUKS 474.8G                      
  &#9492;&#9472;nvme0n1p3_crypt crypt LVM2_member 474.8G                      
    &#9500;&#9472;vgmint-root   lvm   ext4           35G   23.3G    25%       /
    &#9500;&#9472;vgmint-swap_1 lvm   swap          4.1G                      [SWAP]
    &#9492;&#9472;vgmint-home00 lvm   ext4           20G   17.6G     5%       /home
```

That's from "Four". We can see that partitions 1, 2, 3 are actually in order on the disk.  That isn't required.  Note, there's no room between 1 and 2, so 1 cannot be made larger.  There's no room between 2 and 3, so 2 cannot be made larger either.  3 is a LUKS container. Everything inside partition 3 is encrypted (474G).  Inside the LUKS encrypted container is LVM and some logical volumes. Normal stuff, but extremely flexible.  Immediately after install, I did resize the LVM objects for my needs.  Lots of free storage (400+GB!) , so when I need more, it can be added to existing or new LVs.  I've never guessed correctly where I'll need storage, so best to have the flexibility of LVM.

And please, please, use code tags, as I've shown.  Columns that line up really help make reading this stuff easier.

---

### Post by juergen-soemen on 2024-09-22
Thank you for your fast answer, TheFu!

The reason why I used so much space is because this is 2 TB drive and there is plenty of space - also important files are stored in the Cloud. So that leaves plenty of space on the local drive.
Furthermore I wanted to avoid future headache about the size of this special and not easy to handle space.

There is one reason why I need Windows on this computer - PearsonVUE online Exams. They don't support Linux - else I would have reinstalled this computer in the very beginning to be Ubuntu only.

Here is the output of the parted-l command:

```
 
$ parted -l
Modell: Seagate ZP2000GV30012 (nvme)
Festplatte  /dev/nvme0n1:  2000GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: gpt
Disk-Flags: 

Nummer  Anfang  Ende    Größe   Dateisystem  Name                          Flags
 2      106MB   123MB   16,8MB               Microsoft reserved partition  msftres
 3      123MB   858GB   858GB   ntfs         Basic data partition          msftdata
 4      858GB   859GB   821MB   ntfs                                       versteckt, diag
 5      859GB   1999GB  1140GB  ext4
 1      1999GB  2000GB  1406MB  fat32        Boot EFI                      boot, esp


$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME        TYPE FSTYPE   SIZE FSAVAIL FSUSE% LABEL MOUNTPOIN
nvme0n1     disk          1,8T                      
&#9500;&#9472;nvme0n1p1 part vfat     1,3G   22,9M    76%       /boot/efi
&#9500;&#9472;nvme0n1p2 part           16M                      
&#9500;&#9472;nvme0n1p3 part ntfs   799,1G

```

---

### Post by TheFu on 2024-09-22
> **juergen-soemen said:**
>  
```

Nummer  Anfang  Ende    Größe   Dateisystem  Name                          Flags
 2      106MB   123MB   16,8MB               Microsoft reserved partition  msftres
 3      123MB   858GB   858GB   ntfs         Basic data partition          msftdata
 4      858GB   859GB   821MB   ntfs                                       versteckt, diag
 5      859GB   [COLOR="#FF0000"]1999GB[/COLOR]  1140GB  ext4
 1      [COLOR="#FF0000"]1999GB[/COLOR]  2000GB  [COLOR="#008000"]1406MB[/COLOR]  fat32        Boot EFI                      boot, esp

```

Note the start/end sectors for each partition. Looks like there's no room to the "right" of partition 1 or to the left.  You'll need to reduce partition 5 first.  BTW, the OS size for most Linux systems doesn't need to be much over 35G, then create other partitions for other needs. This keeps the OS separate from data.

But having the EFI partition as 1.4GB is huge!  Can't imagine needing anything so large.  100MB should be more than sufficient.
If you touch anything related to booting, you'll want to run an **upgrade-grub** and perhaps **update-initramfs**  (I don't remember the order) or the exact commands and options to those commands. Sorry.

---

### Post by juergen-soemen on 2024-09-22
Thanks again for your help TheFu.

> But having the EFI partition as 1.4GB is huge!  Can't imagine needing anything so large.  100MB should be more than sufficient.

Before I started to resize the EFI partition, it was 100MB (the laptop was pre-installed with Windows, which by default creates a 100MB EFI partition). I can Image that there is no space issue without multi boot.

In the first attempt to solve the temporary space problem I moved the content of the Microsoft folder to /home and then tried to apply the BIOS upgrade with the Ubuntu firmware updater program. 
But it told me insufficient space. Maybe the program creates a backup and needs therefore appx. the double space to apply the upgrade, I don't know.

Here is the space consumption of /boot/efi as it is now:

```
$ du -h /boot/efi/ --max-depth=2
27M    /boot/efi/EFI/Microsoft
1,9M    /boot/efi/EFI/Boot
45M    /boot/efi/EFI/ubuntu
74M    /boot/efi/EFI
1,0K    /boot/efi/System Volume Information
74M    /boot/efi/
```

And here is the BIOS from the previous BIOS upgrade:

```
boot/efi/EFI/ubuntu/fw# ls -lacth
insgesamt 41M
drwx------ 2 root root 1,0K ago 19 10:04 .
-rwx------ 1 root root  41M ago 19 10:04 fwupd-8cf4e0ec-a249-4c1f-9cdf-bbe85a9096e4.cap
drwx------ 3 root root 1,0K mar  4  2024 ..
```

But I am not sure if I may move this file with together with the /boot/efi/EFI/Microsoft to /home (I don't want to risk an unusable system).
If it is ok, the space should be sufficient.


> Note the start/end sectors for each partition. Looks like there's no  room to the "right" of partition 1 or to the left.  You'll need to  reduce partition 5 first. 
Will do. Is 200MB ok?
Please tell me what we aiming for with this action - create space for a new EFI partition?

> BTW, the OS size for most Linux systems doesn't need to be much over  35G, then create other partitions for other needs. This keeps the OS  separate from data.
This is a good hint.

Maybe it is necessary to describe which steps I performed trying to resize the EFI partition:
[LIST]
[*]created a dump with Ubuntu disk utility to /home
[*]Reduced the Ubuntu partition
[*]deleted the EFI partition
[*]created a new EFI partition using the free space
[*]formatted it with FAT32
[*]flagged the new partition
[*]restored the dump file with disk utility (in this step the wrong file system disk size happened)
[*]created a mount point
[*]**upgrade-grub**
[/LIST]

---

### Post by juergen-soemen on 2024-09-23
Here is the new paritioning:

$ parted /dev/nvme0n1 print free
Modell: Seagate ZP2000GV30012 (nvme)
Festplatte  /dev/nvme0n1:  2000GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: gpt
Disk-Flags: 

```
Nummer  Anfang  Ende    Größe   Dateisystem   Name                          Flags
        17,4kB  106MB   106MB   Freier Platz
 2      106MB   123MB   16,8MB                Microsoft reserved partition  msftres
 3      123MB   858GB   858GB   ntfs          Basic data partition          msftdata
 4      858GB   859GB   821MB   ntfs                                        versteckt, diag
 5      859GB   1999GB  1140GB  ext4
        1999GB  1999GB  199MB   Freier Platz
 1      1999GB  2000GB  1406MB  fat32         Boot EFI                      boot, esp
        2000GB  2000GB  73,2kB  Freier Platz
```

Please advise what to do next.

---

### Post by yancek on 2024-09-23
Moving your EFI partition to the extreme end of a 2TB drive seems like asking for problems.  I see boot repair output here often stating the boot files are far from the beginning of the device and this is on MUCH SMALLER drives than yours.  So what is the situation now?  Is the computer usable?  Can you boot either windows or Ubuntu in any way, from the UEFI menu in the BIOS?  What output did you get when you ran update-grub?  I would expect that since you moved all the boot files you would need to reinstall grub first.

---

### Post by juergen-soemen on 2024-09-23
Both OS are booting ok (from grub).
The only issue is the difference between partitioned size and size shown at file system level, which makes the newly allocated space in partition 1 unavailable.

The formerly output of update-grub is not available anymore, I closed the terminal in between.

I ran that command once again, here is the output:

```
$ update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.8.0-45-generic
Found initrd image: /boot/initrd.img-6.8.0-45-generic
Found linux image: /boot/vmlinuz-6.8.0-44-generic
Found initrd image: /boot/initrd.img-6.8.0-44-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
```

---

