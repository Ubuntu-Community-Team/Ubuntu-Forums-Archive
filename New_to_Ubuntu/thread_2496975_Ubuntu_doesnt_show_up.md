---
title: "Ubuntu doesnt show up"
date: 2024-04-18
forum: New to Ubuntu
---

### Post by niedzik32 on 2024-04-18
Hi, while starting a computer it doesnt show grub menu nor F9 doesnt work. It directs me straight up to windows. 
boot-repair-4ppa2075                                              [20240418_1727]

```
============================= Boot Repair Summary ==============================





modprobe: FATAL: Module efivars not found in directory /lib/modules/6.5.0-18-generic

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of
sda2,
using the following options:  nvme0n1p1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file


Mount /dev/nvme0n1p1 on /mnt/boot-sav/sda2/boot/efi

Unhide GRUB boot menu in sda2/etc/default/grub

=============== Reinstall the grub-efi-amd64-signed of /dev/sda2 ===============

chroot /mnt/boot-sav/sda2 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.5.0-18-generic
chroot /mnt/boot-sav/sda2 modprobe efivars

chroot /mnt/boot-sav/sda2 efibootmgr -v before grub install
EFI variables are not supported on this system.


chroot /mnt/boot-sav/sda2 uname -r
6.5.0-18-generic

chroot /mnt/boot-sav/sda2 grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/nvme0n1p1
mv /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/efi/ubuntu/shimx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/

chroot /mnt/boot-sav/sda2 grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

chroot /mnt/boot-sav/sda2 efibootmgr -v after grub install
EFI variables are not supported on this system.

Warning: NVram is locked (Ubuntu not found in efibootmgr).

chroot /mnt/boot-sav/sda2 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Found linux image: /boot/vmlinuz-6.5.0-27-generic
Found initrd image: /boot/initrd.img-6.5.0-27-generic
Found linux image: /boot/vmlinuz-6.5.0-18-generic
Found initrd image: /boot/initrd.img-6.5.0-18-generic
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi

Unhide GRUB boot menu in sda2/boot/grub/grub.cfg

Boot successfully repaired.

Locked-NVram detected. Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.4 LTS entry (nvme0n1p1/efi/ubuntu/shimx64.efi file) !
Please disable SecureBoot in the BIOS. Then try again.


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/grubx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/SecureBootRecovery.efi

nvme0n1p2: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme0n1p3: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

nvme0n1p4: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


================================ 2 OS detected =================================

OS#1:   Ubuntu 22.04.4 LTS on sda2
OS#2:   Windows 10 or 11 on nvme0n1p3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GA107M [GeForce RTX 3050 Mobile] TigerLake-H GT1 [UHD Graphics] from NVIDIA Corporation Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.4 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: E16R6IMS.10A(1.10) from American Megatrends International, LLC.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot enabled according to mokutil - Please report this message to boot.repair@gmail.com.
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0004,0003,0000,0001
Boot0000* ubuntu    HD(1,GPT,95debcb5-8402-4c80-83ee-a61471c1c4b4,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* ubuntu    HD(1,GPT,95debcb5-8402-4c80-83ee-a61471c1c4b4,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...t................
Boot0003* Windows Boot Manager    HD(1,GPT,95debcb5-8402-4c80-83ee-a61471c1c4b4,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO
Boot0004* UEFI:  USB, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(16,0)/HD(1,MBR,0xd73b9,0x800,0x7298800)..BO

64349b3622c65f495a99dbf6102496e3   nvme0n1p1/Boot/bkpbootx64.efi
64349b3622c65f495a99dbf6102496e3   nvme0n1p1/Boot/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   nvme0n1p1/Boot/fbx64.efi
a1da253696a304dce6b4668b70151c0e   nvme0n1p1/Boot/grubx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p1/Boot/mmx64.efi
a1da253696a304dce6b4668b70151c0e   nvme0n1p1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   nvme0n1p1/ubuntu/shimx64.efi
3d09cb6ae9b7dfb474846879b12bd1f9   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
b3d8489beeed8806075fc70173f0908a   nvme0n1p1/Microsoft/Boot/bootmgr.efi
23837e7f81b5b729c2cc673d3da56273   nvme0n1p1/Microsoft/Boot/SecureBootRecovery.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sda    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    34 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
nvme0n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: B007E484-575D-4264-BE69-EF46FD0BF2E7
             Start        End   Sectors   Size Type
nvme0n1p1      2048     206847    204800   100M EFI System
nvme0n1p2    206848     239615     32768    16M Microsoft reserved
nvme0n1p3    239616  999145623 998906008 476.3G Microsoft basic data
nvme0n1p4 999149568 1000212479   1062912   519M Windows recovery environment
Disk sda: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk identifier: 2BEAFCE8-74F7-4FE4-A522-5D74953F4918
     Start        End    Sectors   Size Type
sda1     34      32767      32734    16M Microsoft reserved
sda2  32768 2000408575 2000375808 953.9G Linux filesystem
Disk sdb: 57.3 GiB, 61524148224 bytes, 120164352 sectors
Disk identifier: 0x000d73b9
     Boot Start       End   Sectors  Size Id Type
sdb1  *     2048 120164351 120162304 57.3G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:1024GB:scsi:512:512:gpt:ATA SSDPR-CX400-01T-:;
1:17.4kB:16.8MB:16.8MB::Microsoft reserved partition:msftres;
2:16.8MB:1024GB:1024GB:ext4::;
sdb:61.5GB:scsi:512:512:msdos: USB  SanDisk 3.2Gen1:;
1:1049kB:61.5GB:61.5GB:fat32::boot, lba;
nvme0n1:512GB:nvme:512:512:gpt:KINGSTON OM8PCP3512F-AI1:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:512GB:511GB:ntfs:Basic data partition:msftdata;
4:512GB:512GB:544MB:ntfs::hidden, diag;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                        
&#9500;&#9472;sda1                                                    6b3c92d4-1882-4e37-a9c1-af5e0b4ef3e7             Microsoft reserved partition
&#9492;&#9472;sda2      ext4     79c90c7e-ccc8-4a28-91ba-729823ae13b9 99c441c6-074e-4db2-90e7-66818911cc7c             
sdb                                                                                                        
&#9492;&#9472;sdb1      vfat     1D1B-1720                            000d73b9-01                          UBUNTU 22_0 
nvme0n1                                                                                                    
&#9500;&#9472;nvme0n1p1 vfat     FE1D-7A09                            95debcb5-8402-4c80-83ee-a61471c1c4b4             EFI system partition
&#9500;&#9472;nvme0n1p2                                               0ab88adb-2303-4688-9fa7-01891560e97c             Microsoft reserved partition
&#9500;&#9472;nvme0n1p3 ntfs     18C21DF0C21DD2BC                     040b9ae9-42a9-4a96-bbd4-89e23822a89d             Basic data partition
&#9492;&#9472;nvme0n1p4 ntfs     C4F80EAFF80E9FB2                     e77217ae-c77c-4ffe-830e-88f1b003be55             

Mount points (filtered): _______________________________________________________

                           Avail Use% Mounted on
/dev/nvme0n1p1             61.3M  36% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3            201.7G  58% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4             88.1M  83% /mnt/boot-sav/nvme0n1p4
/dev/sda2                 881.1G   1% /mnt/boot-sav/sda2
/dev/sdb1                  52.6G   8% /cdrom
efivarfs                   71.1K  60% /sys/firmware/efi/efivars

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p1            vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme0n1p3            fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme0n1p4            fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda2                 ext4            rw,relatime
/dev/sdb1                 vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 79c90c7e-ccc8-4a28-91ba-729823ae13b9 root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Ubuntu   79c90c7e-ccc8-4a28-91ba-729823ae13b9
Windows Boot Manager (on nvme0n1p1)   osprober-efi-FE1D-7A09
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=79c90c7e-ccc8-4a28-91ba-729823ae13b9 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=FE1D-7A09  /boot/efi       vfat    umask=0077      0       1

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
  12.919506073 = 13.872214016   boot/vmlinuz                                   1
 704.060184479 = 755.978866688  boot/vmlinuz-6.5.0-18-generic                  2
  12.919506073 = 13.872214016   boot/vmlinuz-6.5.0-27-generic                  1
 704.060184479 = 755.978866688  boot/vmlinuz.old                               2
  12.346652985 = 13.257117696   boot/initrd.img                                1
 706.229438782 = 758.308085760  boot/initrd.img-6.5.0-18-generic               7
  12.346652985 = 13.257117696   boot/initrd.img-6.5.0-27-generic               1
 706.229438782 = 758.308085760  boot/initrd.img.old                            7

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sdb1: Location of files loaded by Grub
```

---

### Post by yancek on 2024-04-18
>  NVram is locked (Ubuntu not found in efibootmgr).

There are a number of threads here with that problem with no specific solution.  You might do a search on the forum or online for possible solutions and if you use any, make note of exactly what you changed.  You might take a look at the link below, specifically to the suggestion with a link in post 7.

[https://ubuntuforums.org/showthread.php?t=2482909](https://ubuntuforums.org/showthread.php?t=2482909)

---

### Post by tea for one on 2024-04-18
> **niedzik32 said:**
> Hi, while starting a computer it doesnt show grub menu nor F9 doesnt work. It directs me straight up to windows.
Is this an HP device?
Can you access the UEFI settings and see if you have TPM enabled?

---

