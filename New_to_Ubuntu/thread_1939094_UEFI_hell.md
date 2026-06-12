---
title: "UEFI hell?"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by ClientAlive on 2012-03-10
Ok, my intention is not to go off on a rant but I really should explain a couple things so that people might be able to help me...

I built a new desktop over a month ago and haven't been able to use it yet. I specifically chose a uefi motherboard because I thought I would be able to take advantage of all these wonderful new efi features. I've spent the last 3 weeks trying to install 2 other distros without success. It's important to me that it be a Linux system and that it be an efi bootabel system. I also have large disks so I will require gpt to take advantage of all my disk space (I know there is add hoc software that gives you a workaround but I don't want that). As of this point I'm just hoping to find something I can 'just install' and begin using my new computer. I've been using ubuntu 10.04 LTS for a little over a year now and it's my first Linux (using it on the loaptop I'm writing to you on now). So, that being said, I'm hoping to verify whether this is true of Ubuntu or not - that it does well with uefi. If anyone has experience with this (non mac) please share...

Heres what I have so far:

3 X 3 TB disks partitioned with gpt in the followind way - 

```
root@sysresccd /root % gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.1

 

Partition table scan:

  MBR: protective

  BSD: not present

  APM: not present

  GPT: present

 

Found valid GPT with protective MBR; using GPT.

 

Command (? for help): p

Disk /dev/sda: 5860533168 sectors, 2.7 TiB

Logical sector size: 512 bytes

Disk identifier (GUID): BF5AB663-8960-406F-BCE1-1DECD658A063

Partition table holds up to 128 entries

First usable sector is 34, last usable sector is 5860533134

Partitions will be aligned on 2048-sector boundaries

Total free space is 2014 sectors (1007.0 KiB)

 

Number  Start (sector)    End (sector)  Size       Code  Name

   1            2048          104447   50.0 MiB    EF00  EFI System

   2          104448      1536104447   732.4 GiB   FD00  Linux RAID

   3      1536104448      1547290623   5.3 GiB     8200  Linux swap

   4      1547290624      5860533134   2.0 TiB     FD00  Linux RAID

 

Command (? for help): q

root@sysresccd /root % gdisk /dev/sdb

GPT fdisk (gdisk) version 0.8.1

 

Partition table scan:

  MBR: protective

  BSD: not present

  APM: not present

  GPT: present

 

Found valid GPT with protective MBR; using GPT.

 

Command (? for help): p

Disk /dev/sdb: 5860533168 sectors, 2.7 TiB

Logical sector size: 512 bytes

Disk identifier (GUID): 26EC247D-7F60-4789-8AF3-E04121501585

Partition table holds up to 128 entries

First usable sector is 34, last usable sector is 5860533134

Partitions will be aligned on 2048-sector boundaries

Total free space is 102366 sectors (50.0 MiB)

 

Number  Start (sector)    End (sector)  Size       Code  Name

   1          102400      1536102399   732.4 GiB   FD00  Linux RAID

   2      1536102400      1547288575   5.3 GiB     8200  Linux swap

   3      1547288576      5860533134   2.0 TiB     FD00  Linux RAID

 

Command (? for help): q

root@sysresccd /root % gdisk /dev/sdc

GPT fdisk (gdisk) version 0.8.1

 

Partition table scan:

  MBR: protective

  BSD: not present

  APM: not present

  GPT: present

 

Found valid GPT with protective MBR; using GPT.

 

Command (? for help): p

Disk /dev/sdc: 5860533168 sectors, 2.7 TiB

Logical sector size: 512 bytes

Disk identifier (GUID): 26EC247D-7F60-4789-8AF3-E04121501585

Partition table holds up to 128 entries

First usable sector is 34, last usable sector is 5860533134

Partitions will be aligned on 2048-sector boundaries

Total free space is 102366 sectors (50.0 MiB)

 

Number  Start (sector)    End (sector)  Size       Code  Name

   1          102400      1536102399   732.4 GiB   FD00  Linux RAID

   2      1536102400      1547288575   5.3 GiB     8200  Linux swap

   3      1547288576      5860533134   2.0 TiB     FD00  Linux RAID

 

Command (? for help): q
```

RAID in the following configuration - 

```
 root@sysresccd /root % cat /proc/mdstat
    Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]

    md126 : active raid5 sda2[0] sdc1[3] sdb1[1]

          1535996928 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]

         

    md127 : active raid5 sda4[0] sdc3[3] sdb3[1]

          4313239552 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]

  unused devices: <none>


```

And LVM in the following configuration -

```
   root@sysresccd /root % pvdisplay
      --- Physical volume ---

      PV Name               /dev/md127

      VG Name               data

      PV Size               4.02 TiB / not usable 4.00 MiB

      Allocatable           yes (but full)

      PE Size               4.00 MiB

      Total PE              1053036

      Free PE               0

      Allocated PE          1053036

      PV UUID               ekXL2P-Hgvo-h3C2-LDTD-oUsO-EIsp-Kzo0Wo

       

      --- Physical volume ---

      PV Name               /dev/md126

      VG Name               sys

      PV Size               1.43 TiB / not usable 0  

      Allocatable           yes (but full)

      PE Size               4.00 MiB

      Total PE              374999

      Free PE               0

      Allocated PE          374999

      PV UUID               OH3VfN-Jro5-DvEK-HoFL-0wG5-30Qc-LXpBcd

       

    root@sysresccd /root % vgdisplay

      --- Volume group ---

      VG Name               data

      System ID            

      Format                lvm2

      Metadata Areas        1

      Metadata Sequence No  6

      VG Access             read/write

      VG Status             resizable

      MAX LV                0

      Cur LV                1

      Open LV               0

      Max PV                0

      Cur PV                1

      Act PV                1

      VG Size               4.02 TiB

      PE Size               4.00 MiB

      Total PE              1053036

      Alloc PE / Size       1053036 / 4.02 TiB

      Free  PE / Size       0 / 0  

      VG UUID               vLZg8a-K3qK-W7ae-ea30-ViAh-Pnri-rRjL2C

       

      --- Volume group ---

      VG Name               sys

      System ID            

      Format                lvm2

      Metadata Areas        1

      Metadata Sequence No  13

      VG Access             read/write

      VG Status             resizable

      MAX LV                0

      Cur LV                2

      Open LV               1

      Max PV                0

      Cur PV                1

      Act PV                1

      VG Size               1.43 TiB

      PE Size               4.00 MiB

      Total PE              374999

      Alloc PE / Size       374999 / 1.43 TiB

      Free  PE / Size       0 / 0  

      VG UUID               6w59f4-0AEz-hn7t-2pNF-olbT-EM8g-mkwVpD

       

    root@sysresccd /root % lvdisplay

      --- Logical volume ---

      LV Name                /dev/data/storage

      VG Name                data

      LV UUID                hWfopU-NjVi-s7Ao-dDsQ-1uik-Mv2v-tec3Pf

      LV Write Access        read/write

      LV Status              available

      # open                 0

      LV Size                4.02 TiB

      Current LE             1053036

      Segments               1

      Allocation             inherit

      Read ahead sectors     auto

      - currently set to     4096

      Block device           253:0

       

      --- Logical volume ---

      LV Name                /dev/sys/root

      VG Name                sys

      LV UUID                2MlJJA-B8N7-ReMa-Oj8q-VRAs-muU7-OvBNjk

      LV Write Access        read/write

      LV Status              available

      # open                 1

      LV Size                50.00 GiB

      Current LE             12800

      Segments               1

      Allocation             inherit

      Read ahead sectors     auto

      - currently set to     4096

      Block device           253:1

       

      --- Logical volume ---

      LV Name                /dev/sys/vm

      VG Name                sys

      LV UUID                0KpbV5-3hiS-T3PY-1lw1-VLmr-nT87-O0LegZ

      LV Write Access        read/write

      LV Status              available

      # open                 0

      LV Size                1.38 TiB

      Current LE             362199

      Segments               1

      Allocation             inherit

      Read ahead sectors     auto

      - currently set to     4096

      Block device           253:2

       
```


These are that which I intend to keep. Let me clarify, I can and am willing to step back and repartition, redo raid and redo lvm - if some different configuration is necessary or even just better. I would rather avoid that but I am willing. What I can't give up is having RAID and lvm altogether - these are things I need to have as part of my system.

I should also explain why I'm writing this post first rather than just "trying it and see..."

I have spent the last 4 solid days (I'm talking about all day from the momonet my eyes crack open until I can no longer hold them open) trying to build gentoo on that !@#^# of a machine. Suffice it to say, UEFI bites me in the but again on that one (good luck installing grub2 on a gentoo build).

So the moral of the story is I just don't want to clobber Gentoo until I'm a little more certain that what I would replace it with will work without too much greif.

I know this was a long post; and, if you made it throught to this point I sincerely appreciate you reading this. If you have any words of wisdom please do share them with me. I'm tired. I need my computer.

Thanks
Jake

---

### Post by ClientAlive on 2012-03-10
Ok, my intention is not to go off on a rant but I really should explain a couple things so that people might be able to help me...

I built a new desktop over a month ago and haven't been able to use it yet. I specifically chose a uefi motherboard because I thought I would be able to take advantage of all these wonderful new efi features. I've spent the last 3 weeks trying to install 2 other distros without success. It's important to me that it be a Linux system and that it be an efi bootabel system. I also have large disks so I will require gpt to take advantage of all my disk space (I know there is add hoc software that gives you a workaround but I don't want that). As of this point I'm just hoping to find something I can 'just install' and begin using my new computer. I've been using ubuntu 10.04 LTS for a little over a year now and it's my first Linux (using it on the loaptop I'm writing to you on now). So, that being said, I'm hoping to verify whether this is true of Ubuntu or not - that it does well with uefi. If anyone has experience with this (non mac) please share...

Heres what I have so far:

3 X 3 TB disks partitioned with gpt in the followind way - 

```
root@sysresccd /root % gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.1

 

Partition table scan:

  MBR: protective

  BSD: not present

  APM: not present

  GPT: present

 

Found valid GPT with protective MBR; using GPT.

 

Command (? for help): p

Disk /dev/**sda**: 5860533168 sectors, 2.7 TiB

Logical sector size: 512 bytes

Disk identifier (GUID): BF5AB663-8960-406F-BCE1-1DECD658A063

Partition table holds up to 128 entries

First usable sector is 34, last usable sector is 5860533134

Partitions will be aligned on 2048-sector boundaries

Total free space is 2014 sectors (1007.0 KiB)

 

Number  Start (sector)    End (sector)  Size       Code  Name

   1            2048          104447   50.0 MiB    EF00  EFI System

   2          104448      1536104447   732.4 GiB   FD00  Linux RAID

   3      1536104448      1547290623   5.3 GiB     8200  Linux swap

   4      1547290624      5860533134   2.0 TiB     FD00  Linux RAID

 

Command (? for help): q

root@sysresccd /root % gdisk /dev/sdb

GPT fdisk (gdisk) version 0.8.1

 

Partition table scan:

  MBR: protective

  BSD: not present

  APM: not present

  GPT: present

 

Found valid GPT with protective MBR; using GPT.

 

Command (? for help): p

Disk /dev/**sdb**: 5860533168 sectors, 2.7 TiB

Logical sector size: 512 bytes

Disk identifier (GUID): 26EC247D-7F60-4789-8AF3-E04121501585

Partition table holds up to 128 entries

First usable sector is 34, last usable sector is 5860533134

Partitions will be aligned on 2048-sector boundaries

Total free space is 102366 sectors (50.0 MiB)

 

Number  Start (sector)    End (sector)  Size       Code  Name

   1          102400      1536102399   732.4 GiB   FD00  Linux RAID

   2      1536102400      1547288575   5.3 GiB     8200  Linux swap

   3      1547288576      5860533134   2.0 TiB     FD00  Linux RAID

 

Command (? for help): q

root@sysresccd /root % gdisk /dev/sdc

GPT fdisk (gdisk) version 0.8.1

 

Partition table scan:

  MBR: protective

  BSD: not present

  APM: not present

  GPT: present

 

Found valid GPT with protective MBR; using GPT.

 

Command (? for help): p

Disk /dev/**sdc**: 5860533168 sectors, 2.7 TiB

Logical sector size: 512 bytes

Disk identifier (GUID): 26EC247D-7F60-4789-8AF3-E04121501585

Partition table holds up to 128 entries

First usable sector is 34, last usable sector is 5860533134

Partitions will be aligned on 2048-sector boundaries

Total free space is 102366 sectors (50.0 MiB)

 

Number  Start (sector)    End (sector)  Size       Code  Name

   1          102400      1536102399   732.4 GiB   FD00  Linux RAID

   2      1536102400      1547288575   5.3 GiB     8200  Linux swap

   3      1547288576      5860533134   2.0 TiB     FD00  Linux RAID

 

Command (? for help): q
```

RAID in the following configuration - 

```
 root@sysresccd /root % cat /proc/mdstat
    Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]

    md126 : active raid5 sda2[0] sdc1[3] sdb1[1]

          1535996928 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]

         

    md127 : active raid5 sda4[0] sdc3[3] sdb3[1]

          4313239552 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]

  unused devices: <none>


```

And LVM in the following configuration -

```
   root@sysresccd /root % pvdisplay
      --- Physical volume ---

      PV Name               **/dev/md127**

      VG Name               data

      PV Size               4.02 TiB / not usable 4.00 MiB

      Allocatable           yes (but full)

      PE Size               4.00 MiB

      Total PE              1053036

      Free PE               0

      Allocated PE          1053036

      PV UUID               ekXL2P-Hgvo-h3C2-LDTD-oUsO-EIsp-Kzo0Wo

       

      --- Physical volume ---

      PV Name               **/dev/md126**

      VG Name               sys

      PV Size               1.43 TiB / not usable 0  

      Allocatable           yes (but full)

      PE Size               4.00 MiB

      Total PE              374999

      Free PE               0

      Allocated PE          374999

      PV UUID               OH3VfN-Jro5-DvEK-HoFL-0wG5-30Qc-LXpBcd

       

    root@sysresccd /root % vgdisplay

      --- Volume group ---

      **VG Name               data**

      System ID            

      Format                lvm2

      Metadata Areas        1

      Metadata Sequence No  6

      VG Access             read/write

      VG Status             resizable

      MAX LV                0

      Cur LV                1

      Open LV               0

      Max PV                0

      Cur PV                1

      Act PV                1

      VG Size               4.02 TiB

      PE Size               4.00 MiB

      Total PE              1053036

      Alloc PE / Size       1053036 / 4.02 TiB

      Free  PE / Size       0 / 0  

      VG UUID               vLZg8a-K3qK-W7ae-ea30-ViAh-Pnri-rRjL2C

       

      --- Volume group ---

      **VG Name               sys**

      System ID            

      Format                lvm2

      Metadata Areas        1

      Metadata Sequence No  13

      VG Access             read/write

      VG Status             resizable

      MAX LV                0

      Cur LV                2

      Open LV               1

      Max PV                0

      Cur PV                1

      Act PV                1

      VG Size               1.43 TiB

      PE Size               4.00 MiB

      Total PE              374999

      Alloc PE / Size       374999 / 1.43 TiB

      Free  PE / Size       0 / 0  

      VG UUID               6w59f4-0AEz-hn7t-2pNF-olbT-EM8g-mkwVpD

       

    root@sysresccd /root % lvdisplay

      --- Logical volume ---

      LV Name                **/dev/data/storage**

      VG Name                data

      LV UUID                hWfopU-NjVi-s7Ao-dDsQ-1uik-Mv2v-tec3Pf

      LV Write Access        read/write

      LV Status              available

      # open                 0

      LV Size                4.02 TiB

      Current LE             1053036

      Segments               1

      Allocation             inherit

      Read ahead sectors     auto

      - currently set to     4096

      Block device           253:0

       

      --- Logical volume ---

      LV Name                **/dev/sys/root**

      VG Name                sys

      LV UUID                2MlJJA-B8N7-ReMa-Oj8q-VRAs-muU7-OvBNjk

      LV Write Access        read/write

      LV Status              available

      # open                 1

      LV Size                50.00 GiB

      Current LE             12800

      Segments               1

      Allocation             inherit

      Read ahead sectors     auto

      - currently set to     4096

      Block device           253:1

       

      --- Logical volume ---

      LV Name                **/dev/sys/vm**

      VG Name                sys

      LV UUID                0KpbV5-3hiS-T3PY-1lw1-VLmr-nT87-O0LegZ

      LV Write Access        read/write

      LV Status              available

      # open                 0

      LV Size                1.38 TiB

      Current LE             362199

      Segments               1

      Allocation             inherit

      Read ahead sectors     auto

      - currently set to     4096

      Block device           253:2

       
```


These are that which I intend to keep. Let me clarify, I can and am willing to step back and repartition, redo raid and redo lvm - if some different configuration is necessary or even just better. I would rather avoid that but I am willing. What I can't give up is having RAID and lvm altogether - these are things I need to have as part of my system.

I should breifly mention the operating systems purpose:

I'm looking to install something for really a single purpose - to be the host to quemu/ kvm. It would be nice if it were lightweight, need not even have a gui - just fire up kvm from which I will run a guest o/s to do whatever I really need to be doing.

I should also explain why I'm writing this post first rather than just "trying it and see..."

I have spent the last 4 solid days (I'm talking about all day from the momonet my eyes crack open until I can no longer hold them open) trying to build gentoo on that !@#^# of a machine. Suffice it to say, UEFI bites me in the butt again on that one (good luck installing grub2 on a gentoo build).

So the moral of the story is I just don't want to clobber Gentoo until I'm a little more certain that what I would replace it with will work without too much greif.

I know this was a long post; and, if you made it throught to this point I sincerely appreciate you reading this. If you have any words of wisdom please do share them with me. I'm tired. I need my computer.

Thanks
Jake

---

### Post by acimi66 on 2012-03-11
Sorry I can't really help but heres some link that might help

[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

or this video be informative
[http://www.youtube.com/watch?feature=endscreen&NR=1&v=-zYFeUlInpo](http://www.youtube.com/watch?feature=endscreen&NR=1&v=-zYFeUlInpo)

the uefi bios looks great.
Good Luck

---

### Post by nothingspecial on 2012-03-11
Merged.

---

### Post by Cheesemill on 2012-03-11
My setup doesn't use LVM but I have successfully installed Arch on a system that uses UEFI, GPT and GRUB2.

I'm not sure if using RAID as a boot device is possible though, I just have an SSD as my OS drive and a software RAID using mdadm for my storage.

Some links that may be useful:

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

I know that you were asking about Ubuntu, but I figure that if you're OK with Gentoo then Arch should be no problem :)

Also I used this installation media:
[https://wiki.archlinux.org/index.php/Archboot](https://wiki.archlinux.org/index.php/Archboot)

Which has support for GPT / GRUB2 / UEFI built in unlike the official install image.

---

### Post by Gone fishing on 2012-03-11
You can have the raid on the boot device (I've done it).
I found this which looks useful with Ubuntu [http://askubuntu.com/questions/91484/how-to-boot-ubuntu-from-efi-uefi](http://askubuntu.com/questions/91484/how-to-boot-ubuntu-from-efi-uefi)

---

### Post by oldfred on 2012-03-11
I think Cheesemill gave you some good links. I have not installed with UEFI and do not know RAID nor LVM.

Grub2 has many updates to work with UEFI and you need the newest version. There were(are) many bugs also, some that require major workaround.

If just Ubuntu and you have partitioned in advance and are installing the newest version it should work. But only those who partitioned in advance seemed to make it work.

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)

---

### Post by ClientAlive on 2012-03-11
Thank you, those are some good links.

I found a couple links myself which may be useful if anyone ever reads this thread in the future:

I found this one which contains information, in the response, that indicates the ubuntu installer has been designed to boot on either BIOS or UEFI since 10.10. I don't know who Colin Watson is but he speaks in the first person singular in his response. Perhaps he is the person responsible for creating the ubuntu installers. Do you see the inforamation in that response? It's only half a sentance but it's there:

> In 10.10, I changed the standard amd64 images to dual-boot on either BIOS or UEFI systems

[https://answers.launchpad.net/mactel-support/+question/162838](https://answers.launchpad.net/mactel-support/+question/162838)

In that sentance he is talking about the "standard" image, not the MAC image - even though the question was about the MAC image.

Reading that response told me the standard image should work.

I don't have the links up any longer but I had also found a couple web pages that indicate you need to use the alternate install cd if you want to deal with raid and lvm. Perhaps it was dated and these things can be done with the other install images these days - idk. I also want a cli only install and build from there myself - so this seemed like the right option.

So I'm booted with the ubuntu-11.10-alternate-amd64.iso and all seems to be going fine except I have no way to verify that it's efi booted or not. I had discoverd before this that the way to verify it is to check for the existence of a certain directory, after the installer is booted. For fedora it is: /sys/firmware/efi. For anything standard grub2 it may, concievably be something like: /boot/efi/EFI or /boot/efi/efi (sometheing like that but I'm not certain). The problem is that ctrl+F1 and ctrl+F2 do not give me a terminal while in this ubuntu installer. I have no way to check for it. I guess I'm just pushing forward and hope for a clean install. If I have to do some hacking after the install that's fine.

The installer allows me to set /dev/mapper/sys-root (a logical volume) with the / mount point so hopefully all will proceed well to the finish.

* If anyone knows how I can veryify whether this installer is efi booted or not it would be appreciated.

---------------------------
Link to the 64-bit Mac (AMD64) alternate install CD (if you do happen to have a MAC):

[http://cdimages.ubuntu.com/releases/natty/release/](http://cdimages.ubuntu.com/releases/natty/release/)
---------------------------

Edit:

As for the efi system partition:

I can't find anywhere in the "Use as" menu that corresponds with an efi system partition or in the "Mount point" menu that corresponds wtih mounting it as the efi system partition. This is disturbing, as I'm rather certain I need something like this for a uefi install.

Until I can sort this out I'm kind of at a stand still...

Should I set it manually as /dev/mapper/sys-root/boot  ??

Any ideas?

Pictures attached.

---

### Post by Cheesemill on 2012-03-11
> I don't have the links up any longer but I had also found a couple web pages that indicate you need to use the alternate install cd if you want to deal with raid and lvm.Yep.

> For fedora it is: /sys/firmware/efi. For anything standard grub2 it may, concievably be something like: /boot/efi/EFI or /boot/efi/efi (sometheing like that but I'm not certain).I'm pretty sure it's /boot/efi

> The problem is that ctrl+F1 and ctrl+F2 do not give me a terminal while in this ubuntu installer.Isn't it CTRL+ALT+F1 etc...

> As for the efi system partition:

I can't find anywhere in the "Use as" menu that corresponds with an efi system partition or in the "Mount point" menu that corresponds wtih mounting it as the efi system partition. This is disturbing, as I'm rather certain I need something like this for a uefi install.

Until I can sort this out I'm kind of at a stand still...

Should I set it manually as /dev/mapper/sys-root/boot  ??

Any ideas?
From the Arch wiki pages:

To create a UEFI system partition:

**For MBR partitioned disks:**
Using GNU Parted/GParted: Create a >=400 MiB FAT32 partition. Change the type code of that partition to 0xEF using fdisk, cfdisk or sfdisk.
*or*
Using fdisk: Create a >=400 MiB partition with partition type 0xEF and format it as FAT32 using mkfs.vfat -F32 /dev/<THAT_PARTITION>

**For GPT partitioned disks:**
Using GNU Parted/GParted: Create a >=400 MiB FAT32 partition. Set "boot" flag on for that partition.
*or*
Using GPT fdisk (aka gdisk): Create a >=400 MiB partition with gdisk type code "EF00". Then format that partition as FAT32 using mkfs.vfat -F32 /dev/<THAT_PARTITION> 

** Then mount the UEFI system partition at /boot/efi**

(Disclaimer - Again this is all from my experiences with Arch so YMMV. As far as possible Arch uses unpatched sources for everything so unless the Ubuntu devs have done anything weird then you should be OK)

---

### Post by oldfred on 2012-03-11
You can run boot info script and see if it shows grub2's boot loader in the MBR or a efi partition.

Only the git/test version parses efi partitions.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Not sure if Boot-Repair works with your system but it also runs the git version.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

If from liveCD you may have to install the extra drivers:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install xz-utils
unlzma is equivalent to xz --format=lzma --decompress.

---

### Post by ClientAlive on 2012-03-11
> **Cheesemill said:**
> 

Isn't it CTRL+ALT+F1 etc...


That's what I was pressing. It was a typo on my part when I posted. Still doesn't get me a terminal though so I'm kind out of ideas on getting one open from within this installer.

This is a really big deal! If I can't get a terminal I'm very very limited here. And I really need to find out whether this thing is efi booted or not before I know what choices I face. Critical to find that out.

> **oldfred said:**
> You can run boot info script and see if it shows grub2's boot loader in the MBR or a efi partition.

Only the git/test version parses efi partitions.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Not sure if Boot-Repair works with your system but it also runs the git version.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

If from liveCD you may have to install the extra drivers:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install xz-utils
unlzma is equivalent to xz --format=lzma --decompress.

I'm not sure I understand how this might help. There is no operating system on that machine. I'm booted via cd into the ubuntu alternate install cd. If I restart the machine with a different cd in there, then it's exactly that - the ubuntu installer will no longer be fired up on the machine. There's nothing to check as being booted efi or not except the installer itself. This also seems to require a command line which I've been unable to get up in the installer.
-----------------------------

Basically I'm stuck with a few little questions. Some have more to do with how this installer treats UEFI and other how it treats other things:

> **Cheesemill said:**
> 
From the Arch wiki pages:

To create a UEFI system partition:

Using GPT fdisk (aka gdisk): Create a >=400 MiB partition with gdisk type code "EF00". Then format that partition as FAT32 using mkfs.vfat -F32 /dev/<THAT_PARTITION> 


I've noticed that the size you're told to make the system partition is all over the board depending on what source you look at. I've seen one source use only 8 MiB (or was it MB - either way... ). I've seen others tell you between 200 and 500. I've seen another one tell you >= 100, and the list goes on. Mine happens to be 50 MiB.

> **Cheesemill said:**
> 
** Then mount the UEFI system partition at /boot/efi**


/boot (for me) would be instide a logical volume. Specifically, I have /dev/mapper/sys-boot (a logical volume) set to be mounted to /. I'm assuming this means that /boot (among other things) will be created inside there as part of the install process.

If I were to need to "...mount the UEFI System partion at /boot/efi" the only path I can think of for it's mount point would be: /dev/mapper/sys-root/boot/efi  (or would it just be /boot/efi because of some technicality in regard to how the installer treats thing? I'm not sure... )

In either of the cases (regarding what path is technically correct for the mount point) this raises some questions:

(1) Is the installation going to create the directory "efi" as part of the install process?

(2) To mount /dev/sda1 (my system partition) to /dev/mapper/sys-root/boot...  (to take the first notion of what the path should be) would be to mount it to a directory (/boot) which doesn't even exist yet. IE: "/boot (for me) would be instide a logical volume ... I'm assuming this means that /boot (among other things) will be created inside there as part of the install process."

The crossroad I feel I'm standing at right now is this:

Either the installer is efi booted and I can work on how to proceed that way; or the installer is not booted efi and I need to consider whether I can get a clean BIOS boot install out of it and then try to convert to efi after the install is complete.

---

### Post by oldfred on 2012-03-11
I thought you had something installed and could not tell how it was working.

I think the installer finds the efi partition and then knows it should be efi install. Although some posts seemed to just do an install then install the grub-efi as part of a grub repair.

---

### Post by ClientAlive on 2012-03-11
> **oldfred said:**
> I thought you had something installed and could not tell how it was working.

I think the installer finds the efi partition and then knows it should be efi install. Although some posts seemed to just do an install then install the grub-efi as part of a grub repair.


Yes. I think we're starting to narrow this down to specifics now.

To put it succincly, I think the biggest issue I face atm is whether to proceed with an efi install or a BIOS install. But I need more information, and more definite information at that, before I can make a prodent decision about that.

I'm googling for it right now but if anyone knows how I can make a definite ascertation on how this installer is booted...

Also - what should be selected in the "Use as" menu for the system partition? Which selection would correspond to an efi installation and which would correspond to a BIOS installation?

I see one selection in there called, "Reserved BIOS boot area" which may be the one that correspond to a BIOS install. Thought this may take care of that half of the question, I'd still like verification on it.

Also, either route I go (whether an efi install or a BIOS install) I'm wondering if I shouldn't set the mount piont as "/boot/efi" (exactly as that) ??
-----------------------

Edit:

It's concievable that if I can find out the precise name of the selection for an efi install (in the "Use as" part) that I could use it as a way of telling whether the installer is efi booted or not.

---

### Post by oldfred on 2012-03-11
I boot with BIOS and gpt. So I have a bios_grub partition. My new SSD I also created a 250MB efi partition as the first partition as I hope to get an UEFI system soon. But I did not give it the ef00 (yet) setting as I knew I was BIOS and did not want grub to get confused. So my efi is not really an efi just a label so far.

If using gpt with BIOS create a 1MB bios_grub partition. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. 

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

One suggestion was to create both from notes from several posts:

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

If you're using EFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-2TB disks, so you may need to use another utility to do the partitioning.

---

### Post by ClientAlive on 2012-03-11
oldfred,

I'm sorry I didn't get here more quickly to disclose this:

For about the millionth time, I was reading some document online; and, yet again, I read something to the effect of - 'you have to be sure the installer is efi booted.' I know this. Of course I know this - I've been talking on and on about it. But for some reason it occured to me to try going into my uefi settings, once again...  and see if I could find some distinction in there.

When I read that, I recalled that with a previous install attempt (with a different distro) that the install media would show up in my uefi interface with a "uefi" prefix on the entry. I went right to it; and, sure enough, there were two separate entries for my dvd drive. One had the "uefi" prefix to it and the other didn't. I hadn't noticed it when I booted the installer the first time but this time I chose the entry with the prefix.

I now am able to see an entry in the "Use as" section of the installer  called: "EFI boot partition." This was not there before I rebooted and booted into the installer correctly. Now everything in the installer (fingers crossed) seems to be very straightforward for this. I'm moving forward with this and am hoping it all pans out w/o any further trouble.

Thank you so much oldfred (and everyone who posted here) for the time you've taken to help me. It is greatly appreciated. I will not mark the thread "solved" yet until the install is complete. I may run into some problem yet so please don't stop checking on me. If all goes well, I'll be sure to let everyone know.

Thank you
Jake

PS: Just a reminder in case anyone stumbles on this in the future: The motherboard I have is an **Asus M5A99X Evo** purchaesed around mid Feb of 2012. I say this because getting any information on this board's settings has been absolute hell. Calling the manufacturer's tech support and looking all - over - the - internet for this specific board's setting has yeilded nothing. I found information for similar Asus boards but not this one. Learning where that setting is was just a fluke for me.

Caveot: there may yet be another setting on the board where you set the boot mode. This may be a separate setting or it may not exist at all. If that exists I'm unaware of it.

---

### Post by ClientAlive on 2012-03-11
Well I got an install. I'm typing this to you from that new install. There are a few minor issues/ bugs to work out but I think it best to start a new thread about it. Basically, my real issue was identifying the correct item in my uefi boot options to use. Thanks again fellas.

Jake

---

### Post by oldfred on 2012-03-12
Glad you got it resolved.

We have tested the new git version of Boot info script with one or two efi installs to make sure it parses the efi partitions correctly. 

But could you post your boot info script?

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Current verison does not see efi partition, but has instruction:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install xz-utils
unlzma is equivalent to xz --format=lzma --decompress.

Often good to have some repair tools. Boot-repair also runs the git version of bootinfoscript.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by ClientAlive on 2012-03-12
> **oldfred said:**
> Glad you got it resolved.

We have tested the new git version of Boot info script with one or two efi installs to make sure it parses the efi partitions correctly. 

But could you post your boot info script?

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```


I can if I can get another stinkin install working on here. What I got was a full install (full on unity and the works - in all it's bloated glory). What I thought I would have is the option for a minimal, cli only system. I posted another thread here on the forums talking about "how do I strip it down to cli" and I let this guy talk me into reinstalling with the alternate cd. (Actually, he wanted me to use the minimal install cd but that installer won't even boot - gives me a grub command line). So ever since then this thing has been trashed - again. There's just so many stupid details I don't know how to do with this efi thing but they end up being thigs I MUST do or I'm not gonna have a working o/s on here. Asus tech support is useless - I think they aspire to be useless, in fact.

I'm about to attempt another full install. If I can get that working at all it will probably print "error: efi disk read error" to the screen about a donzen times before it starts to boot the o/s. That's what it did before. But hey, if I can get an o/s to boot at all I guess that's progress. Maybe then I can do what I knew I should have done in the first place - go in and remove the packages one by one until I'm down to cli. I also think replacing grub with elilo is a good idea as well.

Maybe I should try the server install, idk.

Wish me luck. Here I go...

If I can get a system working on here again I'll run the boot info script and share it with you.


Jake

---

### Post by oldfred on 2012-03-13
There have been several threads with users asking how to boot to command line. I have not followed but found this one.

[http://ubuntuforums.org/showthread.php?p=9227346](http://ubuntuforums.org/showthread.php?p=9227346)
Which is edit grub
gksudo gedit /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash text”
I often search the forum with this from google as its search is better than the forum search. Just append this to any search to restrict it to the forum.
site:ubuntuforums.org
or for all linux sites:
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

Minimal install is just that. Only a kernal and enough drivers to connect to the Internet to download just what you want.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Not sure how all the somewhat different versions are updated to include efi. Servers have had UEFI a lot longer than desktops, so I am surprised that efi does not work better.

---

### Post by ClientAlive on 2012-03-13
> **oldfred said:**
> There have been several threads with users asking how to boot to command line. I have not followed but found this one.

[http://ubuntuforums.org/showthread.php?p=9227346](http://ubuntuforums.org/showthread.php?p=9227346)
Which is edit grub
gksudo gedit /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash text”
I often search the forum with this from google as its search is better than the forum search. Just append this to any search to restrict it to the forum.
site:ubuntuforums.org
or for all linux sites:
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

Minimal install is just that. Only a kernal and enough drivers to connect to the Internet to download just what you want.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Not sure how all the somewhat different versions are updated to include efi. Servers have had UEFI a lot longer than desktops, so I am surprised that efi does not work better.


Thanks oldfred.

Well, I did another full install last night figuring I would then just go in and strip it down. The install went fine and was able to boot up (with some errors from my firmware). Installed synaptic and proceeded to spend the next 4 hrs finding an marking packages for removal. What I removed is extreme! I think there were something like 716 packages removed or something like that - and only like 89 packages left behind. Stripped everything gnome, unity, all the little packages like media players and browsers, mozilla, openoffice and libre, etc. Now I can't boot. I have a good idea how to go about fixing the situation though (whether I stick with grub or not). I'm going to look into using elilo to boot. I hear it does better with efi but I'm not sure how well it handles / in a logical volume. Anyhow, I think I should start a separate thread about it since this one was really not about that.

---

### Post by Cheesemill on 2012-03-13
If you are still using the Alternate CD to install then you can just hit F4 on the CD boot screen and select 'Install a CLI system'

---

### Post by oldfred on 2012-03-13
Sometimes uninstalling one package removes a bunch of others and something is essential.

I might just document your installed packages when you get it the way you want, then a reinstall would be easier:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by sudodus on 2012-03-13
[I hope you are not too angry with me for this little detour, but I think the question is too small for an own thread.]

Let's say I want to boot to a text screen, but have the possibility to start a graphics DE. Now I know the first step, and I have installed LXDE.

What command should I use to start the graphics DE?

[I]Edit: In the (good?) old days I was running Unix in Sun workstations like that:
- login to a text screen
- run x to get graphics[/I]

---

### Post by oldfred on 2012-03-13
@sudodus
It may be worthy of its own thread to get the latest info from someone who knows.
The old way always was 
startx

But then (with gnome2) they said this was better:
#or now preferred to restart gdm, I have seen all of these as preferred but do not know if one is better or not.
sudo service gdm start
sudo /etc/init.d/gdm restart
sudo start gdm

But you do not have gdm and I do not know now with Unity and gnome3 what is correct.
You could look in /etc/init.d and see if you have something??

My gdm is just a link to a script that has this in it:
> $ECHO "Rather than invoking init scripts through /etc/init.d, use the service(8)"
$ECHO "utility, e.g. service $INITSCRIPT $COMMAND"


---

### Post by sudodus on 2012-03-13
Thanks oldfred,
Actually (on another system) I have Ubuntu 10.04, so I can test your tips with gnome2. And since you think so, I'll try with an own thread.

---

### Post by ClientAlive on 2012-03-13
> **Cheesemill said:**
> If you are still using the Alternate CD to install then you can just hit F4 on the CD boot screen and select 'Install a CLI system'

Cheesemill,

I would like to try this but I'm not certain which screen you're referring to. I know, seems really stupid, and I'm not trying to be lame here. There is the very first screen you see when you boot the cd. It's first two entries in the list are "Install Ubuntu" and something like 'Install in expert mode' the other remaining two have to do with memtest and/ or system recovery. Pressing F4 at this point yeilds no response. If I select "Install Ubuntu" and press enter the next screen I'm presented with is to "Select a language" - which looks like the beginning of the standard install process. If the screen to press F4 at is somewhere after that one (the "Select a language" one) I'm not really certain which one it would be. From memory it's going to proceed from there with a series of configuring the keyboard, timezone, etc, etc. Can you please clarify at which screen F4 is to be pressed?

Thank you
---------------------

> **oldfred said:**
> Sometimes uninstalling one package removes a bunch of others and something is essential.

I might just document your installed packages when you get it the way you want, then a reinstall would be easier:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade


Yes. Great idea oldfred. Thx. I have never used dpkg except one time a long time ago and was only following some instruction to carry out a specific thing. Thanks for giving me the code to run for this.

---

### Post by Cheesemill on 2012-03-13
Give me a minute, I'll try and dig out an ISO and fire it up in a VM....

---

### Post by Cheesemill on 2012-03-13
Here you go.

This is todays precise-alternate-i386.iso but I can't ever remember it being anything different.

It's the screen after the language select screen.

---

### Post by ClientAlive on 2012-03-13
> **Cheesemill said:**
> Give me a minute, I'll try and dig out an ISO and fire it up in a VM....

Thank you. I sure am glad you checked back so soon. I'm ready to go...
-------------

Edit:

My first menu does not look like what is in your screenshot. In fact, that menu strikes me as the full install cd rather than the "alternate" install cd.

We're talking about Ubuntu 11.10 right? It's conceivable they may have changed the installer starting around 11.04 - I know a lot of radical changes began around that time.

Thx

---

### Post by ClientAlive on 2012-03-13
This what the first screen looks like with the 11.10 alternate install cd:

See attachment

---

### Post by Cheesemill on 2012-03-13
My screenshot is of todays 12.04 alternate image (it was the first one I could find) although I remember 8.04 and 10.04 being exactly the same.

Find attached screenshots of - 

The first screen I get.
The same screen after selecting a language.
The same screen after hitting F4.

---

### Post by ClientAlive on 2012-03-13
> **Cheesemill said:**
> My screenshot is of todays 12.04 alternate image (it was the first one I could find) although I remember 8.04 and 10.04 being exactly the same.

Find attached screenshots of - 

The first screen I get.
The same screen after selecting a language.
The same screen after hitting F4.

I don't know why my screen looks different. It seem like mine is a grub boot menu for some reason and I'm not sure if that's what it should be. After booting the cd but just before seeing that first menu (in the screenshot of previous post) I see the following flash across the screnn:

```

error: "prefix" is not set

```

When I had a working install before I would get another error before it finally booted up the system:

```

error: efidisk read error

```

It would print to the screen about 8 times then begin to boot the o/s (back when I had a working install).

Could these be clues or do I just not have the right install media?

---

### Post by Cheesemill on 2012-03-13
Which install media do you have?

If it's ubuntu-11.10-alternate-amd64.iso then you should be getting the same screens as me.

Just a thought, perhaps booting the CD in UEFI mode is somehow altering the behaviour of the installer?
I can't test this as I don't have access to a UEFI machine at the moment.

---

### Post by ClientAlive on 2012-03-13
> **Cheesemill said:**
> Which install media do you have?

If it's ubuntu-11.10-alternate-amd64.iso then you should be getting the same screens as me.

Just a thought, perhaps booting the CD in UEFI mode is somehow altering the behaviour of the installer?
I can't test this as I don't have access to a UEFI machine at the moment.


It took me a long time to discover this but the way my uefi implementation works (Asus UEFI) is that, in the firmware boot menu, two entries for the dvd drive appear when you have a disk inserted that has anything uefi on it. One has a prefix "UEFI" and the other doesn't. I can click the one with the prefix to get it to efi boot the disc.

To the best of my understanding, the only way to end up with an installation that boots with efi is you have to boot the installer with efi. This is the case with fedora as well (and possibly many or even all linux distros that support it). I know there may be a way to get a non efi boot installation but I don't want that.

I'm dl the 12.04 alternate cd image right now to see if that makes a difference. If I still get that initial error printed to the screen then I fear the issue may be with my firmware or even the board itself.

---

### Post by ClientAlive on 2012-03-13
I burned, md5summed, and booted the 12.04 alternate install dvd and I get the same grub menu as with the 11.10 cd. I'm stumped. I just don't know how to procede with fixing this situation. My firmware is up to date as recent as 2 wks ago (version 0901 of the asus uefi firmware for my board).

I do still get the error message from my firmware with this install media as well:

```

error: "prefix" not found

```

---

### Post by oldfred on 2012-03-13
If it is trying to install in MBR mode and you do not have a 1MB bios_grub partition, I think you get that error.

I have seen one or two installs in MBR mode then reboot  and convert to efi. Not exactly sure how they did that either.

---

### Post by ClientAlive on 2012-03-13
That's probably what I'm going to have to do - convert later. I just hope I can find my way to a minimal system as well.

I tell ya, provided the feature is stable, the minute that 3.3 kernel hits stable I'm jumping on it! It has efi_stub in it.


Thx

---

