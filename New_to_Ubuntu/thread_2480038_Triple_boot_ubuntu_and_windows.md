---
title: "Triple boot ubuntu and windows"
date: 2022-10-17
forum: New to Ubuntu
---

### Post by krishnan t s on 2022-10-17
I have a desktop with 3 drives- 2 SSD's and a hard disk. I have kept each drive dedicated for an operating system. The hard disk for Windows 10, one SSD for Ubuntu Unity 20.04 and one for beta testing Ubuntu 22.10.
The install went without errors for all 3 OSes but I'm getting only one Ubuntu entry in my grub. I would like to add another entry to grub to detect my Ubuntu 22.10 install but I don't know how to(i have already tried grub-install /dev/sda and update grub with no luck). I can boot into all three installs through the default uefi boot manager that i access when i want to boot into a live USB version of Ubuntu.Edit: After reboot, I'm unable to boot into Ubuntu 22.10 through the default uefi boot manager.
Can anyone help me? Thanks in advance

---

### Post by yancek on 2022-10-17
I have a number of questions on your setup and how you installed and I expect it would be simpler if you downloaded and ran boot repair as I expect most questions would be answered.  Go to the link below and download and run boot repair.  Use the 2nd option described on the page using the ppa using installed Ubuntu and select the Create BootInfo Summary option and post the link you are given here when boot repair finishes.  Do NOT try to make any repairs.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by krishnan t s on 2022-10-17
> **yancek said:**
> I have a number of questions on your setup and how you installed and I expect it would be simpler if you downloaded and ran boot repair as I expect most questions would be answered.  Go to the link below and download and run boot repair.  Use the 2nd option described on the page using the ppa using installed Ubuntu and select the Create BootInfo Summary option and post the link you are given here when boot repair finishes.  Do NOT try to make any repairs.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)



```
boot-repair-4ppa200                                              [20221017_1614]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda3: __________________________________________________________________________

    File system:       btrfs
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       btrfs
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu Kinetic Kudu (development branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/ubuntu/grub/grub.cfg

sdc2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe


================================ 3 OS detected =================================

OS#1:   The OS now in use - Ubuntu 20.04.5 LTS CurrentSession on sda3[/@]
OS#2:   Ubuntu Kinetic Kudu (development branch) on sdb2
OS#3:   Windows 10 or 11 on sdc3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: 4th Generation Core Processor Family Integrated Graphics Controller from Intel Corporation
BOOT_IMAGE of the installed session in use:
/@/boot/vmlinuz-5.15.0-50-generic root=UUID=fd7410fe-e68c-4d8b-8b30-8b0fa1846a80 ro rootflags=subvol=@ quiet splash vt.handoff=7
df -Th / : /dev/sda3      btrfs  915G  9.5G  904G   2% /

===================================== UEFI =====================================

BIOS/UEFI firmware: 0327(4.6) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled - SecureBoot disabled
Platform is in Setup Mode - Please report this message to boot.repair@gmail.com.
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0002,0006,0000,0004,0005
Boot0000* Windows Boot Manager    HD(1,GPT,40a2931d-414d-46da-a4ef-8546c696ceaa,0x800,0x177000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...o................
Boot0002* ubuntu    HD(2,GPT,d03a4954-6255-4e2a-ae06-f9f68142eb07,0x2134800,0x176cb4)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0004* UEFI OS    HD(2,GPT,d03a4954-6255-4e2a-ae06-f9f68142eb07,0x2134800,0x176cb4)/File(\EFI\BOOT\BOOTX64.EFI)..BO
Boot0005* ubuntu    HD(2,GPT,d03a4954-6255-4e2a-ae06-f9f68142eb07,0x2134800,0x176cb4)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO
Boot0006* ubuntu    HD(1,GPT,40a2931d-414d-46da-a4ef-8546c696ceaa,0x800,0x177000)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO

728124f6ec8e22fbdbe7034812c81b95   sdc1/Boot/bootx64.efi
85fa9d77b929ec4231aba29476574eb6   sdc1/Boot/fbx64.efi
469e608783843a701d172242f016c79c   sdc1/Boot/mmx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   sdc1/ubuntu/grubx64.efi
469e608783843a701d172242f016c79c   sdc1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sdc1/ubuntu/shimx64.efi
75348ac78723c93af400084cd96e6469   sdc1/Microsoft/Boot/bootmgfw.efi
32bcd3665cc5fb36e7e77961b819c4f3   sdc1/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
sdb    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sdc    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda3    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdb1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdb2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sdc1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc3    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

sda2    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb2    : isnotESP,    fstab-has-bad-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sdb1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sdb
sdc1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0D705E96-D297-490F-8DDC-A0CAF7E99CEA
         Start        End    Sectors   Size Type
sda1      2048   34818046   34815999  16.6G Linux swap
sda2  34818048   36353203    1535156 749.6M EFI System
sda3  36354048 1953523711 1917169664 914.2G Linux filesystem
Disk sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 34EE9007-A7B3-4BAC-A14D-C08C0900265F
        Start        End    Sectors   Size Type
sdb1     2048    1537203    1535156 749.6M EFI System
sdb2  1538048 1953523711 1951985664 930.8G Linux filesystem
Disk sdc: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: FB1078B0-D39D-4EA4-B1DD-9D7CE34FBAC2
        Start        End    Sectors   Size Type
sdc1     2048    1538047    1536000   750M EFI System
sdc2  1538048    1570815      32768    16M Microsoft reserved
sdc3  1570816 1953523711 1951952896 930.8G Microsoft basic data

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:gpt:ATA CT1000MX500SSD1:;
1:1049kB:17.8GB:17.8GB:linux-swap(v1)::swap;
2:17.8GB:18.6GB:786MB:fat32:EFI System Partition:boot, esp;
3:18.6GB:1000GB:982GB:btrfs::;
sdb:1000GB:scsi:512:4096:gpt:ATA CT1000MX500SSD1:;
1:1049kB:787MB:786MB:fat32:EFI System Partition:boot, esp;
2:787MB:1000GB:999GB:btrfs::;
sdc:1000GB:scsi:512:4096:gpt:ATA ST1000DM003-1SB1:;
1:1049kB:787MB:786MB:fat32:NO NAME:boot, esp;
2:787MB:804MB:16.8MB:linux-swap(v1):Microsoft reserved partition:msftres;
3:804MB:1000GB:999GB:ntfs:Basic data partition:msftdata;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL PARTLABEL
sda                                                                                             
&#9500;&#9472;sda1 swap     53ee6221-e60a-421d-a5f6-e33c74de435c 10437821-80d2-44ad-8bb0-897131f39ebd       
&#9500;&#9472;sda2 vfat     131E-0AE2                            d03a4954-6255-4e2a-ae06-f9f68142eb07       EFI System Partition
&#9492;&#9472;sda3 btrfs    fd7410fe-e68c-4d8b-8b30-8b0fa1846a80 d983687b-5ae6-4547-aa22-f8db64638be5       
sdb                                                                                             
&#9500;&#9472;sdb1 vfat     7D83-64F5                            935f9649-07ca-4c46-b1af-5046e825dc85       EFI System Partition
&#9492;&#9472;sdb2 btrfs    f8a8a0fa-a189-400d-b387-49c76c2cd73b 83d5c252-1686-4c85-bb5e-6773641d6204       
sdc                                                                                             
&#9500;&#9472;sdc1 vfat     5CBB-196D                            40a2931d-414d-46da-a4ef-8546c696ceaa       NO NAME
&#9500;&#9472;sdc2 swap     9c0f1852-047b-483c-8dc5-df160a2ed437 646e6cb0-41d0-4e4e-a6c2-a2bdc3c4d833       Microsoft reserved partition
&#9492;&#9472;sdc3 ntfs     CC00B9BD00B9AEB8                     e4cb266f-c078-435d-86d3-ab13a64b2021       Basic data partition

Mount points (filtered): _______________________________________________________

                   Avail Use% Mounted on
/dev/sda3[/@]       903G   1% /
/dev/sda3[/@home]   903G   1% /home
/dev/sdb1         748.1M   0% /mnt/boot-sav/sdb1
/dev/sdb2[/@]       912G   2% /mnt/boot-sav/sdb2
/dev/sdc1         709.8M   5% /mnt/boot-sav/sdc1
/dev/sdc3         881.3G   5% /mnt/boot-sav/sdc3

Mount options (filtered): ______________________________________________________

/dev/sda3[/@]     btrfs           rw,relatime,ssd,space_cache,subvolid=256,subvol=/@
/dev/sda3[/@home] btrfs           rw,relatime,ssd,space_cache,subvolid=257,subvol=/@home
/dev/sdb1         vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdb2[/@]     btrfs           rw,relatime,ssd,space_cache=v2,subvolid=256,subvol=/@
/dev/sdc1         vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdc3         fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096

===================== sda2/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid fd7410fe-e68c-4d8b-8b30-8b0fa1846a80 root hd0,gpt3 
set prefix=($root)'/@/boot/grub'
configfile $prefix/grub.cfg

====================== sda3/boot/grub/grub.cfg (filtered) ======================

Ubuntu   fd7410fe-e68c-4d8b-8b30-8b0fa1846a80
Ubuntu, with Linux 5.15.0-50-generic   fd7410fe-e68c-4d8b-8b30-8b0fa1846a80
Ubuntu, with Linux 5.13.0-30-generic   fd7410fe-e68c-4d8b-8b30-8b0fa1846a80
Windows Boot Manager (on sdc1)   osprober-efi-5CBB-196D
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda3/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=fd7410fe-e68c-4d8b-8b30-8b0fa1846a80 /               btrfs   defaults,subvol=@ 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=131E-0AE2  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda3 during installation
UUID=fd7410fe-e68c-4d8b-8b30-8b0fa1846a80 /home           btrfs   defaults,subvol=@home 0       2
# swap was on /dev/sda1 during installation
UUID=53ee6221-e60a-421d-a5f6-e33c74de435c none            swap    sw              0       0
# swap was on /dev/sdc2 during installation
UUID=9c0f1852-047b-483c-8dc5-df160a2ed437 none            swap    sw              0       0

======================= sda3/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda3: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
  19.224750519 = 20.642418688   boot/grub/grub.cfg                             1
  23.053901672 = 24.753938432   boot/vmlinuz                                   1
  25.353744507 = 27.223375872   boot/vmlinuz-5.13.0-30-generic                 1
  23.053901672 = 24.753938432   boot/vmlinuz-5.15.0-50-generic                 1
  25.353744507 = 27.223375872   boot/vmlinuz.old                               1
  20.994152069 = 22.542299136   boot/initrd.img                                2
  25.906543732 = 27.816939520   boot/initrd.img-5.13.0-30-generic              2
  20.994152069 = 22.542299136   boot/initrd.img-5.15.0-50-generic              2
  25.906543732 = 27.816939520   boot/initrd.img.old                            2

===================== sda3: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18224 Jan 11  2022 10_linux
-rwxr-xr-x 1 root root 42359 Aug 12  2021 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Aug 12  2021 20_linux_xen
-rwxr-xr-x 1 root root 12059 Aug 12  2021 30_os-prober
-rwxr-xr-x 1 root root  1424 Aug 12  2021 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 21  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Aug 12  2021 40_custom
-rwxr-xr-x 1 root root   216 Aug 12  2021 41_custom

=========================== sda3/etc/grub.d/35_fwupd ===========================

#! /bin/sh
# SPDX-License-Identifier: LGPL-2.1+
set -e
[ -d ${pkgdatadir:?} ]
# shellcheck source=/dev/null
. "$pkgdatadir/grub-mkconfig_lib"
if [ -f /var/lib/fwupd/uefi_capsule.conf ] &&
   ls /sys/firmware/efi/efivars/fwupd-*-0abba7dc-e516-4167-bbf5-4d9d1c739416 1>/dev/null 2>&1; then
      . /var/lib/fwupd/uefi_capsule.conf
      if [ "${EFI_PATH}" != "" ] && [ "${ESP}" != "" ]; then
      echo "Adding Linux Firmware Updater entry" >&2
cat << EOF
menuentry 'Linux Firmware Updater' \$menuentry_id_option 'fwupd' {
EOF
      ${grub_probe:?}
      prepare_grub_to_access_device '`${grub_probe} --target=device \${ESP}` | sed -e "s/^/\t/"'
cat << EOF
    chainloader ${EFI_PATH}
}
EOF
      fi
fi

====================== sdb2/boot/grub/grub.cfg (filtered) ======================

Ubuntu   f8a8a0fa-a189-400d-b387-49c76c2cd73b
Ubuntu, with Linux 5.19.0-21-generic   f8a8a0fa-a189-400d-b387-49c76c2cd73b
Ubuntu, with Linux 5.19.0-15-generic   f8a8a0fa-a189-400d-b387-49c76c2cd73b
Windows Boot Manager (on sdc1)   osprober-efi-5CBB-196D
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###
Ubuntu 20.04

========================== sdb2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=f8a8a0fa-a189-400d-b387-49c76c2cd73b /               btrfs   defaults,subvol=@ 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=B789-045E  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sdb2 during installation
UUID=f8a8a0fa-a189-400d-b387-49c76c2cd73b /home           btrfs   defaults,subvol=@home 0       2
# swap was on /dev/sda1 during installation
UUID=53ee6221-e60a-421d-a5f6-e33c74de435c none            swap    sw              0       0
# swap was on /dev/sdc2 during installation
UUID=9c0f1852-047b-483c-8dc5-df160a2ed437 none            swap    sw              0       0

======================= sdb2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sdb2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   1.856311798 = 1.993199616    boot/grub/grub.cfg                             1
   6.993743896 = 7.509475328    boot/vmlinuz                                   1
   8.355251312 = 8.971382784    boot/vmlinuz-5.19.0-15-generic                 1
   6.993743896 = 7.509475328    boot/vmlinuz-5.19.0-21-generic                 1
   8.355251312 = 8.971382784    boot/vmlinuz.old                               1
  13.919006348 = 14.945419264   boot/initrd.img                                1
  10.411079407 = 11.178811392   boot/initrd.img-5.19.0-15-generic              1
  13.919006348 = 14.945419264   boot/initrd.img-5.19.0-21-generic              1
  10.411079407 = 11.178811392   boot/initrd.img.old                            1

===================== sdb2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Sep 19 19:30 10_linux
-rwxr-xr-x 1 root root 43263 Sep 19 19:30 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Sep 19 19:30 20_linux_xen
-rwxr-xr-x 1 root root 13369 Sep 19 19:30 30_os-prober
-rwxr-xr-x 1 root root  1372 Sep 19 19:30 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Aug 31 00:03 35_fwupd
-rwxr-xr-x 1 root root   383 Oct 17 12:27 40_custom
-rwxr-xr-x 1 root root   215 Sep 19 19:30 41_custom

=========================== sdb2/etc/grub.d/35_fwupd ===========================

#! /bin/sh
# SPDX-License-Identifier: LGPL-2.1+
set -e
[ -d ${pkgdatadir:?} ]
# shellcheck source=/dev/null
. "$pkgdatadir/grub-mkconfig_lib"
if [ -f /var/lib/fwupd/uefi_capsule.conf ] &&
   ls /sys/firmware/efi/efivars/fwupd-*-0abba7dc-e516-4167-bbf5-4d9d1c739416 1>/dev/null 2>&1; then
      . /var/lib/fwupd/uefi_capsule.conf
      if [ "${EFI_PATH}" != "" ] && [ "${ESP}" != "" ]; then
      echo "Adding Linux Firmware Updater entry" >&2
cat << EOF
menuentry 'Linux Firmware Updater' \$menuentry_id_option 'fwupd' {
EOF
      ${grub_probe:?}
      prepare_grub_to_access_device '`${grub_probe} --target=device \${ESP}` | sed -e "s/^/\t/"'
cat << EOF
    chainloader ${EFI_PATH}
}
EOF
      fi
fi

========================== sdb2/etc/grub.d/40_custom ===========================

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu 20.04" {
   search --set=root --fs-uuid B789-045E
   linux ($root)/casper/vmlinuz.efi boot=casper quiet splash --
   initrd ($root)/casper/initrd.lz
}

===================== sdc1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 11abda28-06cc-4033-818b-573f95aa0468 root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== sdc1/efi/ubuntu/grub/grub.cfg (filtered) ===================

Elementary   11abda28-06cc-4033-818b-573f95aa0468
Elementary, with Linux 5.15.0-48-generic   11abda28-06cc-4033-818b-573f95aa0468
Elementary, with Linux 5.15.0-46-generic   11abda28-06cc-4033-818b-573f95aa0468
Windows Boot Manager (on sdc1)   osprober-efi-5CBB-196D
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

BTRFS detected on sdb2
ls sdb2:

---
mount /dev/sdb2 /mnt/boot-sav/sdb2/ 
MOUNTCODE=0
---
os-prober before @ subvol mount:
/dev/sdc1@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
---
umount /mnt/boot-sav/sdb2

---
mount -t btrfs -o subvol=@ /dev/sdb2 /mnt/boot-sav/sdb2/ 
---
MOUNTCODE=0
os-prober after @ subvol mount:
/dev/sdb2:Ubuntu Kinetic Kudu (development branch) (22.10):Ubuntu:linux
/dev/sdc1@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
---


Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sdb2,
using the following options:  sdb1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Blockers in case of suggested repair: __________________________________________

 Please use this software in a live-session (live-CD or live-USB). This will enable this feature.

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu Kinetic Kudu (development branch) entry (sdb1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)
```

---

### Post by tea for one on 2022-10-17
You have btrfs for both sda3 and sdb2 and Grub needs a bit of help to recognise the partition.

Look closely at the end of the following line.
OS#1:   The OS now in use - Ubuntu 20.04.5 LTS CurrentSession on sda3[[COLOR="#0000FF"]/@[/COLOR]]
The mountpoint is /@/ rather than / 

Kinetic is here  /dev/sdb2[/@]     btrfs           rw,relatime,ssd,space_cache=v2,subvolid=256,[COLOR="#0000FF"]subvol=/@[/COLOR]

btrfs has added an extra complication for Grub
Does this help [https://askubuntu.com/questions/1353540/grub-not-recognizing-btrfs-partition-after-ubuntu-installation](https://askubuntu.com/questions/1353540/grub-not-recognizing-btrfs-partition-after-ubuntu-installation)

In your position, I would simply continue to boot from the UEFI boot menu.

---

### Post by oldfred on 2022-10-17
Ubuntu's Ubiquity installer has always only installed grub2's EFI files into first drive's ESP - efi system partition.
I see two ESP on different drives & different UEFI boot entries using the different ESPs.
Did you do one of the many work arounds, or have they after many years fixed this bug?
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

I have used configfile in grub to in effect switch ESPs, or load other install's grub.cfg rather than os-prober's use of standard grub boot stanza for other install. 
You can add to 40_custom, configfile, or full boot stanza.
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Configfile example to another grub.cfg
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

