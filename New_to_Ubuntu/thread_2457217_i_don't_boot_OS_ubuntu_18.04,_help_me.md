---
title: "i don't boot OS ubuntu 18.04, help me"
date: 2021-01-27
forum: New to Ubuntu
---

### Post by hieuthanhle on 2021-01-27
I crashed at the OS screen, i tried repair OS ubuntu but that doesn't fix it
It is log that repair.
Please help me !
```
boot-repair-4ppa125                                              [20210128_0306]

============================= Boot Repair Summary ==============================



/usr/share/boot-sav/bs-cmd_terminal.sh: line 177: warning: command substitution: ignored null byte in input

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of
sda2,
using the following options:        sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s  use-standard-efi-file


/boot/efi added in sda2/fstab
Mount sda1 on /mnt/boot-sav/sda2/boot/efi

Unhide GRUB boot menu in sda2/etc/default/grub

================= Reinstall the grub-efi-amd64-signed of sda2 ==================

grub-install --version
grub-install (GRUB) 2.02-2ubuntu8.17

efibootmgr -v from chroot before grub install
BootCurrent: 000F
Timeout: 1 seconds
BootOrder: 000F,0000,000A,000B,000C,000D,0003,000E,0010
Boot0000* ubuntu    HD(1,GPT,49e55379-3871-4c8a-a944-1387ce765a4c,0x800,0x100000)/File(EFIUBUNTUSHIMX64.EFI)
Boot0003* UEFI: Built-in EFI Shell    VenMedia(5023b95c-db26-429b-a648-bd47664c8012)..BO
Boot000A* (B181/D0/F0) UEFI: PXE IPv4 Intel(R) Ethernet Connection X722 for 1GbE(MAC:3cecef41e816)    PciRoot(0x3)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x3,0x0)/Pci(0x0,0x0)/MAC(3cecef41e816,1)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot000B* (B181/D0/F1) UEFI: PXE IPv4 Intel(R) Ethernet Connection X722 for 1GbE(MAC:3cecef41e817)    PciRoot(0x3)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x3,0x0)/Pci(0x0,0x1)/MAC(3cecef41e817,1)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot000C* (B181/D0/F0) UEFI: PXE IPv6 Intel(R) Ethernet Connection X722 for 1GbE(MAC:3cecef41e816)    PciRoot(0x3)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x3,0x0)/Pci(0x0,0x0)/MAC(3cecef41e816,1)/IPv6([::]:<->[::]:,0,0)..BO
Boot000D* (B181/D0/F1) UEFI: PXE IPv6 Intel(R) Ethernet Connection X722 for 1GbE(MAC:3cecef41e817)    PciRoot(0x3)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x3,0x0)/Pci(0x0,0x1)/MAC(3cecef41e817,1)/IPv6([::]:<->[::]:,0,0)..BO
Boot000E  USB KEY    BBS(HD,,0x0)/VenHw(5ce8128b-2cec-40f0-8372-80640e3dc858,0b00)..GO..NO..........S.a.n.D.i.s.k....................,.@.r.d.=.X..........A.......................>..Gd-.;.A..MQ..L.4.C.5.3.0.0.0.1.0.7.0.1.2.2.1.1.8.3.4.4........BO
Boot000F* UEFI: SanDisk, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(5,0)/HD(1,MBR,0xf6ff172,0x800,0x1d2f800)..BO
Boot0010  USB HDD    BBS(HD,,0x0)/VenHw(5ce8128b-2cec-40f0-8372-80640e3dc858,0900)..GO..NO..........W.D. .M.y. .P.a.s.s.p.o.r.t. .2.5.E.1.1.0.2.1....................,.@.r.d.=.X..........A.......................F..Gd-.;.A..MQ..L.5.7.5.8.3.5.3.1.4.4.3.4.3.9.4.C.3.5.4.5.5.2.3.4........BO
MirrorStatus: Platform does not support address range mirror
DesiredMirroredPercentageAbove4G: 0.00
DesiredMirrorMemoryBelow4GB: false

uname -r
5.4.0-42-generic

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.
df /dev/sda1
mv /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.

efibootmgr -v from chroot after grub install
BootCurrent: 000F
Timeout: 1 seconds
BootOrder: 0000,000F,000A,000B,000C,000D,0003,000E,0010
Boot0000* ubuntu    HD(1,GPT,49e55379-3871-4c8a-a944-1387ce765a4c,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot0003* UEFI: Built-in EFI Shell    VenMedia(5023b95c-db26-429b-a648-bd47664c8012)..BO
Boot000A* (B181/D0/F0) UEFI: PXE IPv4 Intel(R) Ethernet Connection X722 for 1GbE(MAC:3cecef41e816)    PciRoot(0x3)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x3,0x0)/Pci(0x0,0x0)/MAC(3cecef41e816,1)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot000B* (B181/D0/F1) UEFI: PXE IPv4 Intel(R) Ethernet Connection X722 for 1GbE(MAC:3cecef41e817)    PciRoot(0x3)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x3,0x0)/Pci(0x0,0x1)/MAC(3cecef41e817,1)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot000C* (B181/D0/F0) UEFI: PXE IPv6 Intel(R) Ethernet Connection X722 for 1GbE(MAC:3cecef41e816)    PciRoot(0x3)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x3,0x0)/Pci(0x0,0x0)/MAC(3cecef41e816,1)/IPv6([::]:<->[::]:,0,0)..BO
Boot000D* (B181/D0/F1) UEFI: PXE IPv6 Intel(R) Ethernet Connection X722 for 1GbE(MAC:3cecef41e817)    PciRoot(0x3)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x3,0x0)/Pci(0x0,0x1)/MAC(3cecef41e817,1)/IPv6([::]:<->[::]:,0,0)..BO
Boot000E  USB KEY    BBS(HD,,0x0)/VenHw(5ce8128b-2cec-40f0-8372-80640e3dc858,0b00)..GO..NO..........S.a.n.D.i.s.k....................,.@.r.d.=.X..........A.......................>..Gd-.;.A..MQ..L.4.C.5.3.0.0.0.1.0.7.0.1.2.2.1.1.8.3.4.4........BO
Boot000F* UEFI: SanDisk, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(5,0)/HD(1,MBR,0xf6ff172,0x800,0x1d2f800)..BO
Boot0010  USB HDD    BBS(HD,,0x0)/VenHw(5ce8128b-2cec-40f0-8372-80640e3dc858,0900)..GO..NO..........W.D. .M.y. .P.a.s.s.p.o.r.t. .2.5.E.1.1.0.2.1....................,.@.r.d.=.X..........A.......................F..Gd-.;.A..MQ..L.5.7.5.8.3.5.3.1.4.4.3.4.3.9.4.C.3.5.4.5.5.2.3.4........BO
MirrorStatus: Platform does not support address range mirror
DesiredMirroredPercentageAbove4G: 0.00
DesiredMirrorMemoryBelow4GB: false

chroot /mnt/boot-sav/sda2 update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-62-generic
Found initrd image: /boot/initrd.img-5.4.0-62-generic
Found linux image: /boot/vmlinuz-5.4.0-60-generic
Found initrd image: /boot/initrd.img-5.4.0-60-generic
Found linux image: /boot/vmlinuz-5.4.0-52-generic
Found initrd image: /boot/initrd.img-5.4.0-52-generic
Adding boot menu entry for EFI firmware configuration

Unhide GRUB boot menu in sda2/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.

Please do not forget to make your UEFI firmware boot on the Ubuntu 18.04.4 LTS entry (sda1/EFI/ubuntu/shimx64.efi file) !

============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/grubx64.efi 
                       /efi/ubuntu/fwupx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       3518998527 sectors, but according to the info from 
                       fdisk, it has 7813965823 sectors.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32784 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys


================================ 1 OS detected =================================

OS#1:   Ubuntu 18.04.4 LTS on sda2

============================ Architecture/Host Info ============================

CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Ubuntu 18.04.5 LTS, bionic, x86_64)


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled.

efibootmgr -v
BootCurrent: 000F
Timeout: 1 seconds
BootOrder: 000F,0000,000A,000B,000C,000D,0003,000E,0010
Boot0000* ubuntu    HD(1,GPT,49e55379-3871-4c8a-a944-1387ce765a4c,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0003* UEFI: Built-in EFI Shell    VenMedia(5023b95c-db26-429b-a648-bd47664c8012)..BO
Boot000A* (B181/D0/F0) UEFI: PXE IPv4 Intel(R) Ethernet Connection X722 for 1GbE(MAC:3cecef41e816)    PciRoot(0x3)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x3,0x0)/Pci(0x0,0x0)/MAC(3cecef41e816,1)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot000B* (B181/D0/F1) UEFI: PXE IPv4 Intel(R) Ethernet Connection X722 for 1GbE(MAC:3cecef41e817)    PciRoot(0x3)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x3,0x0)/Pci(0x0,0x1)/MAC(3cecef41e817,1)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot000C* (B181/D0/F0) UEFI: PXE IPv6 Intel(R) Ethernet Connection X722 for 1GbE(MAC:3cecef41e816)    PciRoot(0x3)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x3,0x0)/Pci(0x0,0x0)/MAC(3cecef41e816,1)/IPv6([::]:<->[::]:,0,0)..BO
Boot000D* (B181/D0/F1) UEFI: PXE IPv6 Intel(R) Ethernet Connection X722 for 1GbE(MAC:3cecef41e817)    PciRoot(0x3)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x3,0x0)/Pci(0x0,0x1)/MAC(3cecef41e817,1)/IPv6([::]:<->[::]:,0,0)..BO
Boot000E  USB KEY    BBS(HD,,0x0)/VenHw(5ce8128b-2cec-40f0-8372-80640e3dc858,0b00)..GO..NO..........S.a.n.D.i.s.k...................\.,.@.r.d.=.X..........A.......................>..Gd-.;.A..MQ..L.4.C.5.3.0.0.0.1.0.7.0.1.2.2.1.1.8.3.4.4........BO
Boot000F* UEFI: SanDisk, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(5,0)/HD(1,MBR,0xf6ff172,0x800,0x1d2f800)..BO
Boot0010  USB HDD    BBS(HD,,0x0)/VenHw(5ce8128b-2cec-40f0-8372-80640e3dc858,0900)..GO..NO..........W.D. .M.y. .P.a.s.s.p.o.r.t. .2.5.E.1.1.0.2.1...................\.,.@.r.d.=.X..........A.......................F..Gd-.;.A..MQ..L.5.7.5.8.3.5.3.1.4.4.3.4.3.9.4.C.3.5.4.5.5.2.3.4........BO
MirrorStatus: Platform does not support address range mirror
DesiredMirroredPercentageAbove4G: 0.00
DesiredMirrorMemoryBelow4GB: false

bed45d1c9554cea09924d3814cb7c446   sda1/BOOT/fbx64.efi
256fe27540b54b71cf38110338247688   sda1/ubuntu/fwupx64.efi
b6e92eeb44c28043967df78682083d85   sda1/ubuntu/grubx64.efi
4487628005555bfd4a4c0a47211e0700   sda1/ubuntu/mmx64.efi
f7a57b08bc7c1c85417ae4cea582d1d4   sda1/ubuntu/shimx64.efi
f7a57b08bc7c1c85417ae4cea582d1d4   sda1/BOOT/BOOTX64.efi


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes
sdb    : is-GPT,    no-BIOSboot,    has-noESP,     usb-disk,    not-mmc, no-os,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sdb1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda2    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sdb1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sdb

fdisk -l (filtered): ___________________________________________________________

Disk sda: 3.5 TiB, 3839633653760 bytes, 7499284480 sectors
Disk identifier: 0B1FAEF4-1D21-4E0B-A534-C99D7DACEB0C
        Start        End    Sectors  Size Type
sda1     2048    1050623    1048576  512M EFI System
sda2  1050624 7499282431 7498231808  3.5T Linux filesystem
Disk sdc: 14.6 GiB, 15669919744 bytes, 30605312 sectors
Disk identifier: 0x0f6ff172
      Boot Start      End  Sectors  Size Id Type
sdc1  *     2048 30605311 30603264 14.6G  c W95 FAT32 (LBA)
Disk sdb: 3.7 TiB, 4000752599040 bytes, 7813969920 sectors
Disk identifier: B3C03C9C-28F8-4366-96A9-B8C634717561
      Start        End    Sectors  Size Type
sdb1   2048 7813967871 7813965824  3.7T Microsoft basic data

parted -lm (filtered): _________________________________________________________

sda:3840GB:scsi:512:4096:gpt:LSI MR9240-8i:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:3840GB:3839GB:ext4::;
sdb:4001GB:scsi:512:4096:gpt:WD My Passport 25E1:;
1:1049kB:4001GB:4001GB:ntfs:My Passport:msftdata;
sdc:15.7GB:scsi:512:512:msdos:SanDisk Cruzer Glide 3.0:;
1:1049kB:15.7GB:15.7GB:fat32::boot, lba;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
â”œâ”€sda1 vfat     2522-8B85                            49e55379-3871-4c8a-a944-1387ce765a4c             EFI System Partition
â””â”€sda2 ext4     91b47b5b-3952-4c22-be74-777f9ee71ca7 1c690411-5132-4d55-8443-39c106e12cf0             
sdb                                                                                                   
â””â”€sdb1 ntfs     144AEFA64AEF833A                     51278a1c-0fdf-4d5f-ac2a-18269f3e26df SAO_LUU_2   My Passport
sdc                                                                                                   
â””â”€sdc1 vfat     BA4F-C28E                            0f6ff172-01                          UBUNTU 18_0 

df (filtered): _________________________________________________________________

       Avail Use% Mounted on
sda1   502.6M   2% /mnt/boot-sav/sda1
sda2       3T   7% /mnt/boot-sav/sda2
sdb1   387.4G  90% /media/ubuntu/SAO_LUU_2
sdc1    12.5G  14% /cdrom

Mount options: __________________________________________________________________

sda1   rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sda2   rw,relatime
sdb1   rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096
sdc1   ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 91b47b5b-3952-4c22-be74-777f9ee71ca7 root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Ubuntu   91b47b5b-3952-4c22-be74-777f9ee71ca7
Ubuntu, with Linux 5.4.0-62-generic   91b47b5b-3952-4c22-be74-777f9ee71ca7
Ubuntu, with Linux 5.4.0-60-generic   91b47b5b-3952-4c22-be74-777f9ee71ca7
Ubuntu, with Linux 5.4.0-52-generic   91b47b5b-3952-4c22-be74-777f9ee71ca7
### END /etc/grub.d/30_os-prober ###
System setup   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=91b47b5b-3952-4c22-be74-777f9ee71ca7 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
/swapfile                                 none            swap    sw              0       0
UUID=2522-8B85  /boot/efi       vfat    defaults      0       1

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   0.500984192 = 0.537927680    boot/grub/grub.cfg                             1
  29.650341034 = 31.836811264   boot/vmlinuz-5.4.0-52-generic                  1
 627.642532349 = 673.926037504  boot/vmlinuz-5.4.0-60-generic                  1
 136.306594849 = 146.358091776  boot/vmlinuz-5.4.0-62-generic                  2
 136.306594849 = 146.358091776  vmlinuz                                        2
 627.642532349 = 673.926037504  vmlinuz.old                                    1
 132.758255005 = 142.548090880  boot/initrd.img-5.4.0-52-generic               2
 628.015979767 = 674.327023616  boot/initrd.img-5.4.0-60-generic               4
 137.219104767 = 147.337891840  boot/initrd.img-5.4.0-62-generic               6
 137.219104767 = 147.337891840  initrd.img                                     6
 628.015979767 = 674.327023616  initrd.img.old                                 4

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 12693 Nov 11  2019 10_linux
-rwxr-xr-x 1 root root 11298 Nov 11  2019 20_linux_xen
-rwxr-xr-x 1 root root 12059 Nov 11  2019 30_os-prober
-rwxr-xr-x 1 root root  1418 Nov 11  2019 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Nov 11  2019 40_custom
-rwxr-xr-x 1 root root   216 Nov 11  2019 41_custom

====================== sdc1/boot/grub/grub.cfg (filtered) ======================

Try Ubuntu without installing
Install Ubuntu
OEM install (for manufacturers)
Check disc for defects

========================= sdc1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sdc1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sdc1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1


=============================== StdErr Messages ================================

File descriptor 63 (pipe:[53226]) leaked on lvs invocation. Parent PID 7327: /bin/bash[COLOR=#202124][FONT=&amp]I crashed at the OS screen[/FONT][/COLOR][COLOR=#202124][FONT=&amp]I crashed at the OS screen[/FONT][/COLOR]
```

---

### Post by oldfred on 2021-01-27
As Boot-Repair suggests, post just the link to the Boot-Repair Summary Report.

If posting terminal output always use code tags to preserve formatting.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[http://www.bbcode.org/reference.php](http://www.bbcode.org/reference.php)
If using Quick Reply then ```
 at the beginning and 
``` at the end. 
( [noparse]```
 and 
```[/noparse] )

It says it re-installed grub without error.

If you press escape right after UEFI/BIOS screen & before grub menu would appear, you should get grub menu. Sometimes you have to try more than once to catch the right spot.
Can you then boot recovery mode on either of your grub entries.

What brand/model system?
What video card/chip?

---

### Post by hieuthanhle on 2021-01-27
thanks you my bro, i can boot to grub menu, next step how do i can do it ?

---

### Post by hieuthanhle on 2021-01-27
os setup on server suppermicro and no video card/chip

---

### Post by oldfred on 2021-01-28
At grub menu, does recovery mode for one of the kernels work?

---

