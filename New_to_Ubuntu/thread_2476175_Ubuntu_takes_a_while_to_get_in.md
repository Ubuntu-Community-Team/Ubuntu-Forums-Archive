---
title: "Ubuntu takes a while to get in"
date: 2022-06-18
forum: New to Ubuntu
---

### Post by ags8804 on 2022-06-18
Good afternoon. I have a trialboot on my notebook's ssd: Ubuntu 20.04, Windows 10 and Ubuntu 22.04. Everything was fine until using Ubuntu 20.04, when trying to open the terminal using ctrl+alt+t, by mistake I must have typed ctrl+windows+t, as I am used to using the desktop keyboard that only has one key between the ctrl and alt, while the notebook has two (it also has Fn). From there, the note crashed. I couldn't restart even with alt+print+reisub. I had to turn off the note button. And when I turned on, Ubuntu had the screen loading with the terms of loading quickly rising for more than 2 minutes until the login screen to put the password appeared, whereas before, Ubuntu entered in just 20 seconds and without the screen login and password. The strange thing is that Ubuntu 22.04 happened the same problem to start. Windows is normal. I've tried using the "advanced Ubuntu options" of boot (grub), including using another Kernel, I've tried using the restore point that I had created with timeshift, and other options I found in tutorials and nothing worked. I found that, if at the time of loading I keep pressing any key, Ubuntu enters fast and without the login screen. On Ubuntu 22.04, at the beginning of the loading screen the following appears: ^[[20~^[[20~^[[20~^. This until the end of the line and for several lines until then the normal loading terms appear, which takes more than 2 minutes until the login screen appears. Does anyone have any tips? Sorry if the translation from portuguese to english has errors, as this is using Google translator which often has errors.

---

### Post by oldfred on 2022-06-18
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by ags8804 on 2022-06-19
As I understand it, it's for me to use Ubuntu install stick to enter Ubuntu trial mode without installing. I did that and tried to install “Boot-repair”, but after typing “sudo add-apt-repository ppa:yannubuntu/boot-repair” the message appeared: “System program detected” and I could not install boot-repair.

---

### Post by oldfred on 2022-06-19
Boot-Repair only works on current versions.
What version is live installer.
I typically recommend the ppa as it may be more current than the ISO.
But you can download the ISO version & create a live system, its based on Lubuntu, so works with most systems.

---

### Post by ags8804 on 2022-06-19
The installer version is Ubuntu 22.04.

---

### Post by ags8804 on 2022-06-19
Sorry, I couldn't install Boot-repair because I forgot to enable wifi. Now I managed to install Boot-repair. I clicked "yes" in "Upload the report to a pastebin?" and the following URL was displayed: [https://paste.ubuntu.com/p/ndJH8fFFDg/](https://paste.ubuntu.com/p/ndJH8fFFDg/). Is this the link you asked to copy and paste? I entered this URL and the result was as follows:
boot-repair-4ppa200                                              [20220619_2309]

```
============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp fat part_msdos biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid 7014-BA98 root 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda5 and looks at sector 102870952 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda6 and looks at sector 102721600 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 20.04.4 LTS
    Boot files:        /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda7 and looks at sector 98292712 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/bootia32.efi 
                       /efi/BOOT/grub.cfg /boot/grub/i386-pc/core.img


================================ 4 OS detected =================================

OS#1:   Windows 10 (boot) on sda1
OS#2:   Ubuntu 20.04.4 LTS on sda6
OS#3:   Ubuntu 22.04 LTS on sda8
OS#4:   Windows 8 or 10 on sda2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: 2nd Generation Core Processor Family Integrated Graphics Controller from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: S0.08(4.6) from American Megatrends Inc.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).


c152ec201c37b6e97bbc2207e49d1271   sda7/BOOT/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   sda7/BOOT/mmx64.efi
f62c28d9b477b6a1a7b1c991b2b6637d   sda7/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sda7/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda7/ubuntu/shimx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda7/BOOT/BOOTX64.efi
ab98a3563cd3c5c0da1ec4eafc692f57   sdb1/BOOT/bootia32.efi
14287d943837802d99368ffa8dfa3425   sdb1/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has-noESP,     usb-disk,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda7    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdb1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda5    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    grubenv-ok,    noupdategrub,    not-far
sda8    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    not-far
sda6    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda7    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda8    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda6    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda7    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sdb1    : not--sepboot,    no-kernel,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sda5    : is---sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda8    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda6    : not--sepboot,    no-kernel,    fstab-has-goodBOOT,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk identifier: A09DB2B8-B5F6-43AE-AFB3-91E0A90189A1
          Start     End Sectors  Size Type
loop0p1      64 7129427 7129364  3.4G Microsoft basic data
loop0p2 7129428 7137923    8496  4.1M EFI System
loop0p3 7137924 7138523     600  300K Microsoft basic data
Disk sda: 111.79 GiB, 120034123776 bytes, 234441648 sectors
Disk identifier: 0x9f10eb00
      Boot     Start       End   Sectors  Size Id Type
sda1            2048   1126399   1124352  549M  7 HPFS/NTFS/exFAT
sda2         1126400  54802431  53676032 25.6G  7 HPFS/NTFS/exFAT
sda3        54804478 234440703 179636226 85.7G  5 Extended
sda5       102402048 103378943    976896  477M 83 Linux
sda6       103380992 234440703 131059712 62.5G 83 Linux
sda7  *     54804480  55781375    976896  477M ef EFI (FAT-12/16/32)
sda8        55783424 102397951  46614528 22.2G 83 Linux
Partition table entries are not in disk order.
Disk sdb: 14.41 GiB, 15472047104 bytes, 30218842 sectors
Disk identifier: 0x5d1a548c
      Boot Start      End  Sectors  Size Id Type
sdb1        2048 30218239 30216192 14.4G  b W95 FAT32

parted -lm (filtered): _________________________________________________________

sda:120GB:scsi:512:512:msdos:ATA GIGABYTE GP-GSTF:;
1:1049kB:577MB:576MB:ntfs::;
2:577MB:28.1GB:27.5GB:ntfs::;
3:28.1GB:120GB:92.0GB:::;
7:28.1GB:28.6GB:500MB:fat32::boot, esp;
8:28.6GB:52.4GB:23.9GB:ext4::;
5:52.4GB:52.9GB:500MB:ext4::;
6:52.9GB:120GB:67.1GB:ext4::;
sdb:15.5GB:scsi:512:512:msdos:Kingston DataTraveler 3.0:;
1:1049kB:15.5GB:15.5GB:fat32::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                              
&#9500;&#9472;sda1 ntfs     684E0F6E4E0F33FA                     9f10eb00-01                          Reservado pelo Sistema 
&#9500;&#9472;sda2 ntfs     66D81863D8183431                     9f10eb00-02                                                 
&#9500;&#9472;sda3                                               9f10eb00-03                                                 
&#9500;&#9472;sda5 ext4     9ee3f764-9551-4c57-a01c-3455ca9e8c2e 9f10eb00-05                                                 
&#9500;&#9472;sda6 ext4     51a4c3e3-972a-438d-ad5e-8dfbef404610 9f10eb00-06                                                 
&#9500;&#9472;sda7 vfat     654A-BA60                            9f10eb00-07                                                 
&#9492;&#9472;sda8 ext4     019152be-5134-47f1-bd93-2a2744e53e01 9f10eb00-08                                                 
sdb                                                                                                              
&#9492;&#9472;sdb1 vfat     7014-BA98                            5d1a548c-01                          MULTIBOOT              

Mount points (filtered): _______________________________________________________

                        Avail Use% Mounted on
/dev/sda1              157.1M  71% /mnt/boot-sav/sda1
/dev/sda2               12.9G  50% /mnt/boot-sav/sda2
/dev/sda5              249.5M  37% /mnt/boot-sav/sda5
/dev/sda6               39.7G  30% /mnt/boot-sav/sda6
/dev/sda7              470.8M   1% /mnt/boot-sav/sda7
/dev/sda8               10.6G  46% /mnt/boot-sav/sda8
/dev/sdb1               10.8G  25% /media/ubuntu/MULTIBOOT

Mount options (filtered): ______________________________________________________

/dev/sda1              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda2              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5              ext4            rw,relatime
/dev/sda6              ext4            rw,relatime
/dev/sda7              vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda8              ext4            rw,relatime
/dev/sdb1              vfat            rw,nosuid,nodev,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

======================== sda5/grub/grub.cfg (filtered) =========================

Ubuntu   51a4c3e3-972a-438d-ad5e-8dfbef404610
Ubuntu, com o Linux 5.13.0-51-generic   51a4c3e3-972a-438d-ad5e-8dfbef404610
Ubuntu, com o Linux 5.13.0-40-generic   51a4c3e3-972a-438d-ad5e-8dfbef404610
Windows 10 (em sda1)   684E0F6E4E0F33FA
Ubuntu 22.04 LTS (22.04) (em sda8)   019152be-5134-47f1-bd93-2a2744e53e01
Ubuntu (em sda8)   019152be-5134-47f1-bd93-2a2744e53e01
Ubuntu, with Linux 5.15.0-39-generic (em sda8)   019152be-5134-47f1-bd93-2a2744e53e01
Ubuntu, with Linux 5.15.0-30-generic (em sda8)   019152be-5134-47f1-bd93-2a2744e53e01
Ubuntu, with Linux 5.15.0-25-generic (em sda8)   019152be-5134-47f1-bd93-2a2744e53e01
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

==================== sda5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
  49.000984192 = 52.614406144   grub/grub.cfg                                  3
  49.048843384 = 52.665794560   grub/i386-pc/core.img                          1
  48.859008789 = 52.461961216   vmlinuz                                        1
  49.112014771 = 52.733624320   vmlinuz-5.13.0-40-generic                      1
  48.859008789 = 52.461961216   vmlinuz-5.13.0-51-generic                      1
  49.112014771 = 52.733624320   vmlinuz.old                                    1
  49.210277557 = 52.839133184   initrd.img                                     2
  49.131340027 = 52.754374656   initrd.img-5.13.0-40-generic                   3
  49.210277557 = 52.839133184   initrd.img-5.13.0-51-generic                   2
  49.131340027 = 52.754374656   initrd.img.old                                 3

========================== sda6/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=51a4c3e3-972a-438d-ad5e-8dfbef404610 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=9ee3f764-9551-4c57-a01c-3455ca9e8c2e /boot           ext4    defaults        0       2
/swapfile                                 none            swap    sw              0       0

======================= sda6/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda6: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
  81.798164368 = 87.830110208   boot/grub/i386-pc/core.img                     1

===================== sda6: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18224 Jan 11 15:09 10_linux
-rwxr-xr-x 1 root root 42359 Jan 11 15:09 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Apr 15  2020 20_linux_xen
-rwxr-xr-x 1 root root 12059 Apr 15  2020 30_os-prober
-rwxr-xr-x 1 root root  1424 Apr 15  2020 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 21 03:06 35_fwupd
-rwxr-xr-x 1 root root   214 Apr 15  2020 40_custom
-rwxr-xr-x 1 root root   216 Apr 15  2020 41_custom

=========================== sda6/etc/grub.d/35_fwupd ===========================

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

===================== sda7/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 019152be-5134-47f1-bd93-2a2744e53e01 root hd0,msdos8 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda8/boot/grub/grub.cfg (filtered) ======================

Ubuntu   019152be-5134-47f1-bd93-2a2744e53e01
Ubuntu, with Linux 5.15.0-39-generic   019152be-5134-47f1-bd93-2a2744e53e01
Ubuntu, with Linux 5.15.0-30-generic   019152be-5134-47f1-bd93-2a2744e53e01
Ubuntu, with Linux 5.15.0-25-generic   019152be-5134-47f1-bd93-2a2744e53e01
Windows 10 (on sda1)   684E0F6E4E0F33FA
Ubuntu 20.04.4 LTS (20.04) (on sda6)   51a4c3e3-972a-438d-ad5e-8dfbef404610
Ubuntu (on sda6)   51a4c3e3-972a-438d-ad5e-8dfbef404610
Ubuntu, com o Linux 5.13.0-51-generic (on sda6)   51a4c3e3-972a-438d-ad5e-8dfbef404610
Ubuntu, com o Linux 5.13.0-40-generic (on sda6)   51a4c3e3-972a-438d-ad5e-8dfbef404610
Ubuntu, com o Linux 5.4.0-26-generic (on sda6)   51a4c3e3-972a-438d-ad5e-8dfbef404610
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda8/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=019152be-5134-47f1-bd93-2a2744e53e01 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda7 during installation
/swapfile                                 none            swap    sw              0       0

======================= sda8/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda8: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
  42.968078613 = 46.136623104   boot/grub/grub.cfg                             1
  47.104019165 = 50.577555456   boot/grub/i386-pc/core.img                     1
  32.352119446 = 34.737823744   boot/vmlinuz                                   1
  31.794918060 = 34.139533312   boot/vmlinuz-5.15.0-25-generic                 2
  33.563037872 = 36.038037504   boot/vmlinuz-5.15.0-30-generic                 1
  32.352119446 = 34.737823744   boot/vmlinuz-5.15.0-39-generic                 1
  33.563037872 = 36.038037504   boot/vmlinuz.old                               1
  33.993305206 = 36.500033536   boot/initrd.img                                2
  32.930763245 = 35.359137792   boot/initrd.img-5.15.0-25-generic              2
  32.032302856 = 34.394423296   boot/initrd.img-5.15.0-30-generic              6
  33.993305206 = 36.500033536   boot/initrd.img-5.15.0-39-generic              2
  32.032302856 = 34.394423296   boot/initrd.img.old                            6

===================== sda8: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Apr 15 21:50 10_linux
-rwxr-xr-x 1 root root 43031 Apr 15 21:50 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Apr 15 21:50 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15 21:50 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15 21:50 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 19 13:21 35_fwupd
-rwxr-xr-x 1 root root   214 Apr 15 21:50 40_custom
-rwxr-xr-x 1 root root   215 Apr 15 21:50 41_custom

=========================== sda8/etc/grub.d/35_fwupd ===========================

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

====================== sdb1/boot/grub/grub.cfg (filtered) ======================


====================== sdb1/efi/BOOT/grub.cfg (filtered) =======================

[Reboot]
>Linux Distributions"{configfile /multiboot/menu/linux.cfg}

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/grub/i386-pc/core.img                     1



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub2 of
sda8 into the MBR of sda.
Grub-efi would not be selected by default because legacy Windows detected.
Additional repair would be performed: unhide-bootmenu-10s win-legacy-basic-fix

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your BIOS boot on sda (ATA GIGABYTE GP-GSTF) disk!
```

---

### Post by oldfred on 2022-06-19
You did not need to post the report, the link is all that is needed.
And if posting terminal output, please use Code Tags. Easy to add if using Forum's Go Advanced editor and the # icon.

You have a newer UEFI based system, but Windows installed in the old BIOS/MBR configuration.
Microsoft has required vendors to install in UEFI/gpt configuration since 2012 and release of Windows 8.

You show many installs of grub.
Grub should almost always only be installed to a drive like sda, not to a partition like sda6, sda7 & sda8 like you have done.
BIOS can only boot from MBR or first sector of a drive.

You cannot have BIOS Windows and UEFI Ubuntu on same drive. And should install all systems in same boot mode even if multiple drives.
Since Windows is BIOS, Ubuntu should be BIOS boot.
Issue is that Windows has to have boot flag on its boot partition, your sda1. But ESP - efi system partition has to have boot & esp flags. Only one boot flag per drive. 
So use gparted and right click on sda5 to remove boot flag & click on sda1 and add boot flag.

Grub will boot Windows, but it only boots working Windows. 
And with BIOS, you only have one MBR (if one drive), so have to have grub to dual boot. But then when Windows stops working or an update turns fast start up back on, you have to boot Windows. Then you need your Windows repair flash drive and temporarily restore the Windows boot loader to boot Windows (thats why boot flag must be on sda1).

You should only boot installers and repair disks in BIOS boot mode to make sure any repairs or new installs are in correct mode.

Long term, you may want to totally reinstall Windows and Ubuntu in UEFI mode to gpt partitioned drive. But conversion from MBR to gpt normally erases entire drive. So good backups are required. There have been some instructions on converting, but many have ended up just doing a total new install, anyway.
One advantage of UEFI, is that all installs share the ESP, so you can directly boot Windows & Ubuntu from UEFI boot menu. And then if Windows breaks and grub will not boot it, you can directly boot Windows without have to reinstall Windows boot loader and then reinstall grub bootloader to MBR.

---

### Post by ags8804 on 2022-06-20
Thanks for the directions. I really saw that I made mistakes in the systems installations. I followed your guidelines removing the flag and putting it on sda1, but I still have the problem. Now I'm thinking that the problem is the ram memory, because I noticed that using another USB flash drive to install Ubuntu 18.04 to enter the trial mode, the loading also took a long time and the screen loading similar to the operating system boot. I've already tested the RAM and it didn't show any errors. I think it must be a physical problem with the ram. Tomorrow I'm going to take the memory out and do a cleaning. Thank you for your attention and as soon as I have a result I'll post it here on the forum.

---

### Post by oldfred on 2022-06-20
May also be UEFI setting.
If UEFI and BIOS/Legacy/CSM modes enabled, then it may try to boot in UEFI mode, then try BIOS mode.
And if Network boot enabled, it may try to boot via network and have to time out.
Check UEFI settings

---

### Post by ags8804 on 2022-06-22
This notebook does not have UEFI Bios but Legacy. I did an experiment removing the ssd and putting it in another notebook (which also doesn't have UEFI Bios) and then it worked without problem. So the problem is not software. I put the ssd of the other notebook, which also has Ubuntu and working well, in the first notebook and that defect appeared, so the defect is a hardware one. I cleaned the ram memory, but it didn't help.

---

