---
title: "multiple install issuses, now at no boot device found"
date: 2017-04-26
forum: New to Ubuntu
---

### Post by cypath on 2017-04-26
Looking for help to overcome my install issues

I am trying to install Ubuntu 16 on an alienware computer, Ubuntu as the only operating system. I used to run Linux Mint.

I created an installation usb and went through the installation as normal, would get to the end and say it couldn't install the grub bootloader to /dev/sda. Did some reading, tried the something else option from the installation menu, tried installing grub to a different place, would get to the same point of the installation but would say couldn't install grub to the new place I was trying to install it, as before.

Did some further reading, saw people overcame this issue by going into the bios and changing legacy to UEFI, so I did that and the install seems to work, now gets to the end and says its done, restart the system. But when I boot my machine it says no boot device found. 

Did some further reading, saw people overcame this issue by turning secure boot on and then following these steps [https://itsfoss.com/no-bootable-device-found-ubuntu/](https://itsfoss.com/no-bootable-device-found-ubuntu/)
Secure boot was greyed out in the boot menu so had to do some reading to get it turned on, finally got it turned on. But the next step says under security I should have an option to Select an UEFI file as trusted for executing but I have no such option. I do have options to set passwords and none of them were set. I set them all, still nothing came up. Searched around but couldn't find anything on getting the Select an UEFI file as trusted for executing option to appear.

Did some further reading, saw disk repair from the Try Ubuntu option in the installation suggested, installed and ran it, said it worked and that it pasted the record to http:paste2.org/ with nothing after it, said reboot the system. Rebooted, still same issue. Navigated to the paste record and its just the website.

I feel like I'm really close, Ubuntu has installed, I just can't find the options to get the computer to boot into it. Any help would be greatly appreciated.

Please let me know if anything is unclear or if there is further information I should provide. If there is something you want me to provide could you please let me know where to find it/how to get it as I may not know.

Edit: Having done further reading on RAID I'm wondering if picking the right place for all the requirements is the best way forward. I know I had to go through the something else option in the installer to get Mint to work previously, if I list out the entries under something else would this help?

---

### Post by oldfred on 2017-04-26
Which version of 16.04? You need Ubuntu 16.04.2 to have newer kernel.

Script must not have run correctly?
Are you running from the Ubuntu live installer/not the Boot-Repair ISO?

 May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

      
 Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[URL="http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr"]http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr

[/URL]
 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers) 

[URL="http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr"]
[/URL]

---

### Post by cypath on 2017-04-27
Hi Oldfred,

I'm trying to install 16.04.2 downloaded from [https://www.ubuntu.com/download/desktop/thank-you?country=CH&version=16.04.2&architecture=amd64](https://www.ubuntu.com/download/desktop/thank-you?country=CH&version=16.04.2&architecture=amd64)

I'm installing from the usb, when I ran the boot repair I booted from the usb, tried ubuntu without installing, downloaded from terminal and ran it before restarting.

On running 
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
it gets to Get:21 then says:
** (appstreamcli:3735): CRITICAL **: Error while moving old database out of the way. Appstream cache update failed.

on running the command again gets to Hit:7 and says Done.

On running
sudo apt-get install -y boot-info && boot-infothe boot-info runs. I select online report and it runs, when it finishes it lists the url as [http://paste2.org/](http://paste2.org/) and that's it, so it's not generating anything. Ran it again to generate the text file, expected nothing but it did generate:

 ```
Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdc.

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32832 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 28.9 GiB, 30970740736 bytes, 60489728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048    60,489,727    60,487,680   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0                                                   
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p1 5F91-48CB                              vfat       
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p2 7850d9d1-b04f-436b-84f0-3548e3a860ae   ext2       
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p3 6791520e-1318-4d41-8927-1cd239450765   crypto_LUKS 
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sdc1        32CF-EE64                              vfat       UBUNTU 16_0

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Apr 27 10:58 ata-HL-DT-ST_DVDRW_BDROM_CA30N_K0FC5831255 -> ../../sr0
lrwxrwxrwx 1 root root  9 Apr 27 11:14 ata-WDC_WD5000BPKT-75PK4T0_WD-WXB1A9154404 -> ../../sdb
lrwxrwxrwx 1 root root  9 Apr 27 11:14 ata-WDC_WD5000BPKT-75PK4T0_WD-WXU1EB1NYMFM -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 27 10:58 dm-name-isw_dgbjdadccd_M17XR4_RAID0 -> ../../dm-0
lrwxrwxrwx 1 root root 10 Apr 27 11:14 dm-name-isw_dgbjdadccd_M17XR4_RAID0p1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Apr 27 11:14 dm-name-isw_dgbjdadccd_M17XR4_RAID0p2 -> ../../dm-2
lrwxrwxrwx 1 root root 10 Apr 27 11:14 dm-name-isw_dgbjdadccd_M17XR4_RAID0p3 -> ../../dm-3
lrwxrwxrwx 1 root root 10 Apr 27 10:58 dm-uuid-DMRAID-isw_dgbjdadccd_M17XR4_RAID0 -> ../../dm-0
lrwxrwxrwx 1 root root 10 Apr 27 11:14 dm-uuid-part1-DMRAID-isw_dgbjdadccd_M17XR4_RAID0 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Apr 27 11:14 dm-uuid-part2-DMRAID-isw_dgbjdadccd_M17XR4_RAID0 -> ../../dm-2
lrwxrwxrwx 1 root root 10 Apr 27 11:14 dm-uuid-part3-DMRAID-isw_dgbjdadccd_M17XR4_RAID0 -> ../../dm-3
lrwxrwxrwx 1 root root 10 Apr 27 11:14 raid-DMRAID-isw_dgbjdadccd_M17XR4_RAID0-part1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Apr 27 11:14 raid-DMRAID-isw_dgbjdadccd_M17XR4_RAID0-part2 -> ../../dm-2
lrwxrwxrwx 1 root root 10 Apr 27 11:14 raid-DMRAID-isw_dgbjdadccd_M17XR4_RAID0-part3 -> ../../dm-3
lrwxrwxrwx 1 root root 10 Apr 27 11:14 raid-isw_dgbjdadccd_M17XR4_RAID0-part1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Apr 27 11:14 raid-isw_dgbjdadccd_M17XR4_RAID0-part2 -> ../../dm-2
lrwxrwxrwx 1 root root 10 Apr 27 11:14 raid-isw_dgbjdadccd_M17XR4_RAID0-part3 -> ../../dm-3
lrwxrwxrwx 1 root root  9 Apr 27 11:14 usb-Verbatim_STORE_N_GO_07016BE1773D5214-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Apr 27 11:14 usb-Verbatim_STORE_N_GO_07016BE1773D5214-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Apr 27 11:14 wwn-0x50014ee6027d0180 -> ../../sda
lrwxrwxrwx 1 root root  9 Apr 27 11:14 wwn-0x50014ee657d26888 -> ../../sdb

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_dgbjdadccd_M17XR4_RAID0
isw_dgbjdadccd_M17XR4_RAID0p1
isw_dgbjdadccd_M17XR4_RAID0p2
isw_dgbjdadccd_M17XR4_RAID0p3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig 
 
LABEL loadconfig 
  CONFIG /isolinux/isolinux.cfg 
  APPEND /isolinux/ 
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

{All_DMRaid} 

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/13752/mounts) leaked on lvs invocation. Parent PID 20501: bash
File descriptor 63 (pipe:[43962]) leaked on lvs invocation. Parent PID 20501: bash

ADDITIONAL INFORMATION :
=================== log of boot-info 2017-04-27__11h14 ===================
boot-info version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40

BLKID BEFORE RAID ACTIVATION:
/dev/sdb: TYPE="isw_raid_member"
/dev/sdc1: LABEL="UBUNTU 16_0" UUID="32CF-EE64" TYPE="vfat" PARTUUID="24bc2f02-01"
/dev/loop0: TYPE="squashfs"
/dev/sda: TYPE="isw_raid_member"
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p3: UUID="6791520e-1318-4d41-8927-1cd239450765" TYPE="crypto_LUKS" PARTUUID="8b208320-9d4a-40b1-a5a6-c6f4f90b367f"
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p1: UUID="5F91-48CB" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="4ba96b94-464c-4ac2-981b-62b7f53b6a2c"
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p2: UUID="7850d9d1-b04f-436b-84f0-3548e3a860ae" TYPE="ext2" PARTUUID="7cda22b9-93bb-4360-9cd0-c024d7c026b6"
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0: PTUUID="63f635d2-f6f1-459b-878e-c6176c104e2d" PTTYPE="gpt"
dmraid -si -c:
dmraid -ay:
RAID set "isw_dgbjdadccd_M17XR4_RAID0" already active
dmraid -sa -c: isw_dgbjdadccd_M17XR4_RAID0
Error: Invalid argument during seek for read on /dev/sda
Error: /dev/sdb: unrecognised disk label
Error: /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p3: unrecognised disk label
Error: Invalid argument during seek for read on /dev/sda
Error: /dev/sdb: unrecognised disk label
Error: /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p3: unrecognised disk label
boot-info is executed in live-session (Ubuntu 16.04.2 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory
[dmraid -sa -c] isw_dgbjdadccd_M17XR4_RAID0
[dmraid -sa -c] isw_dgbjdadccd_M17XR4_RAID0
[dmraid -sa -c] isw_dgbjdadccd_M17XR4_RAID0
[dmraid -sa -c] isw_dgbjdadccd_M17XR4_RAID0
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p3 : Error code 32
mount -r /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p3 /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0p3
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p3 : Error code 32
mount: /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0 is already mounted or /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0 busy
mount /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0 : Error code 32
mount -r /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0 /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0
mount: /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0 is already mounted or /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0 busy
mount -r /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0 : Error code 32
ls: cannot access '/sys/block/mapper/isw_dgbjdadccd_M17XR4_RAID0/': No such file or directory
GPT PMBR size mismatch (1953536511 != 976773167) will be corrected by w(rite).
Partition 1 does not start on physical sector boundary.

=================== os-prober:


=================== blkid:
/dev/sdb: TYPE="isw_raid_member"
/dev/sdc1: LABEL="UBUNTU 16_0" UUID="32CF-EE64" TYPE="vfat" PARTUUID="24bc2f02-01"
/dev/loop0: TYPE="squashfs"
/dev/sda: TYPE="isw_raid_member"
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p3: UUID="6791520e-1318-4d41-8927-1cd239450765" TYPE="crypto_LUKS" PARTUUID="8b208320-9d4a-40b1-a5a6-c6f4f90b367f"
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p1: UUID="5F91-48CB" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="4ba96b94-464c-4ac2-981b-62b7f53b6a2c"
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p2: UUID="7850d9d1-b04f-436b-84f0-3548e3a860ae" TYPE="ext2" PARTUUID="7cda22b9-93bb-4360-9cd0-c024d7c026b6"
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0: PTUUID="63f635d2-f6f1-459b-878e-c6176c104e2d" PTTYPE="gpt"

mount: unknown filesystem type 'crypto_LUKS'
mount /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p3 : Error code 32
mount -r /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p3 /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0p3
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p3 : Error code 32
mount: /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0 is already mounted or /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0 busy
mount /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0 : Error code 32
mount -r /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0 /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0
mount: /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0 is already mounted or /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0 busy
mount -r /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0 : Error code 32
/dev/sdb: device contains a valid 'isw_raid_member' signature; it is strongly recommended to wipe the device with wipefs(8) if this is unexpected, in order to avoid possible collisions
sfdisk: failed to dump partition table: Success
GPT PMBR size mismatch (1953536511 != 976773167) will be corrected by w(rite).
GPT PMBR size mismatch (1953536511 != 976773167) will be corrected by w(rite).
Partition 1 does not start on physical sector boundary.

=================== efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 2001
Boot0000* UEFI Onboard LAN IPv4    PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(d4bed935f058,0)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)RC
Boot0001* EFI USB1 PATH1 (VerbatimSTORE N GO)    PciRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(2,0)/HD(1,MBR,0x2,0x800,0x39af800)RC
Boot2001* EFI USB Device    RC

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.


=================== PARTITIONS & DISKS:
mapper/isw_dgbjdadccd_M17XR4_RAID0p3    : mapper/isw_dgbjdadccd_M17XR4_RAID0,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0p3.
mapper/isw_dgbjdadccd_M17XR4_RAID0p1    : mapper/isw_dgbjdadccd_M17XR4_RAID0,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0p1.
mapper/isw_dgbjdadccd_M17XR4_RAID0p2    : mapper/isw_dgbjdadccd_M17XR4_RAID0,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0p2.
mapper/isw_dgbjdadccd_M17XR4_RAID0    : mapper/isw_dgbjdadccd_M17XR4_RAID0,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0.

sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
sda    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
mapper/isw_dgbjdadccd_M17XR4_RAID0    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    no-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD5000BPKT-7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags:

Model: ATA WDC WD5000BPKT-7 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags:

Model: Verbatim STORE N GO (scsi)
Disk /dev/sdc: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      1049kB  31.0GB  31.0GB  primary  fat32        boot, lba


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p2: 512MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags:

Number  Start  End    Size   File system  Flags
1      0.00B  512MB  512MB  ext2


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p1: 537MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags:

Number  Start  End    Size   File system  Flags
1      0.00B  537MB  537MB  fat32


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p3: 999GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags:

Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size   File system  Name                  Flags
1      1049kB  538MB   537MB  fat32        EFI System Partition  boot, esp
2      538MB   1050MB  512MB  ext2
3      1050MB  1000GB  999GB

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:unknown:ATA WDC WD5000BPKT-7:;

BYT;
/dev/sdb:500GB:scsi:512:4096:unknown:ATA WDC WD5000BPKT-7:;

BYT;
/dev/sdc:31.0GB:scsi:512:512:msdos:Verbatim STORE N GO:;
1:1049kB:31.0GB:31.0GB:fat32::boot, lba;

BYT;
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p2:512MB:dm:512:4096:loop:Linux device-mapper (linear):;
1:0.00B:512MB:512MB:ext2::;

BYT;
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p1:537MB:dm:512:4096:loop:Linux device-mapper (linear):;
1:0.00B:537MB:537MB:fat32::;

BYT;
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p3:999GB:dm:512:4096:unknown:Linux device-mapper (linear):;

BYT;
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0:1000GB:dm:512:4096:gpt:Linux device-mapper (striped):;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:1050MB:512MB:ext2::;
3:1050MB:1000GB:999GB:::;

=================== lsblk:
KNAME TYPE   FSTYPE            SIZE LABEL
sdb   disk   isw_raid_member 465.8G
dm-0  dmraid                 931.5G
dm-1  part   vfat              512M
dm-2  part   ext2              488M
dm-3  part   crypto_LUKS     930.6G
sr0   rom                     1024M
loop0 loop   squashfs          1.4G
sdc   disk                    28.9G
sdc1  part   vfat             28.9G UBUNTU 16_0
sda   disk   isw_raid_member 465.8G
dm-0  dmraid                 931.5G
dm-1  part   vfat              512M
dm-2  part   ext2              488M
dm-3  part   crypto_LUKS     930.6G

KNAME ROTA RO RM STATE   MOUNTPOINT
sdb      1  0  0 running
dm-0     1  0  0 running
dm-1     1  0  0 running /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0p1
dm-2     1  0  0 running /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0p2
dm-3     1  0  0 running
sr0      1  0  1 running
loop0    1  1  0         /rofs
sdc      1  0  1 running
sdc1     1  0  1         /cdrom
sda      1  0  0 running
dm-0     1  0  0 running
dm-1     1  0  0 running /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0p1
dm-2     1  0  0 running /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0p2
dm-3     1  0  0 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4009708k,nr_inodes=1002427,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=805060k,mode=755)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=28057cd7a466e64b)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=13877)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=805060k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p1 on /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0p1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p2 on /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0p2 type ext2 (rw,relatime,block_validity,barrier,user_xattr,acl,stripe=256)


=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset badblocks bdi capability dev discard_alignment dm ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-1 (filtered):  alignment_offset badblocks bdi capability dev discard_alignment dm ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-2 (filtered):  alignment_offset badblocks bdi capability dev discard_alignment dm ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-3 (filtered):  alignment_offset badblocks bdi capability dev discard_alignment dm ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dm-0 dm-1 dm-2 dm-3 dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 drm_dp_aux3 dvd dvdrw ecryptfs fb0 fb1 fd freefall full fuse hidraw3 hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-14 i2c-15 i2c-16 i2c-17 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kfd kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sdb sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb userio v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control isw_dgbjdadccd_M17XR4_RAID0 isw_dgbjdadccd_M17XR4_RAID0p1 isw_dgbjdadccd_M17XR4_RAID0p2 isw_dgbjdadccd_M17XR4_RAID0p3

=================== hexdump -n512 -C /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 00 10 00 fe 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 cb 48 91 5f 4e  4f 20 4e 41 4d 45 20 20  |..).H._NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
GPT PMBR size mismatch (1953536511 != 976773167) will be corrected by w(rite).
Partition 1 does not start on physical sector boundary.

=================== df -Th:

Filesystem                                Type      Size  Used Avail Use% Mounted on
udev                                      devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs                                     tmpfs     787M  9.6M  777M   2% /run
/dev/sdc1                                 vfat       29G  1.5G   28G   6% /cdrom
/dev/loop0                                squashfs  1.4G  1.4G     0 100% /rofs
aufs                                      aufs      3.9G   51M  3.8G   2% /
tmpfs                                     tmpfs     3.9G  220K  3.9G   1% /dev/shm
tmpfs                                     tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                                     tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs                                     tmpfs     3.9G  304K  3.9G   1% /tmp
tmpfs                                     tmpfs     787M   88K  787M   1% /run/user/999
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p1 vfat      511M  3.5M  508M   1% /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0p1
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0p2 ext2      473M  124M  325M  28% /mnt/boot-sav/mapper/isw_dgbjdadccd_M17XR4_RAID0p2

=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1497772032 bytes, 2925336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1           1 1953536511 1953536511 931.5G ee GPT



Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sdc: 28.9 GiB, 30970740736 bytes, 60489728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x24bc2f02

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 60489727 60487680 28.9G  c W95 FAT32 (LBA)




Disk /dev/mapper/isw_dgbjdadccd_M17XR4_RAID0: 931.5 GiB, 1000210694144 bytes, 1953536512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disklabel type: gpt
Disk identifier: 63F635D2-F6F1-459B-878E-C6176C104E2D

Device                                          Start        End    Sectors   Size Type
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0-part1    2048    1050623    1048576   512M EFI System
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0-part2 1050624    2050047     999424   488M Linux filesystem
/dev/mapper/isw_dgbjdadccd_M17XR4_RAID0-part3 2050048 1953535999 1951485952 930.6G Linux filesystem


No OS or WinEFI system
gui-tab-other.sh: line 93: _checkbutton_repairfilesystems: command not found


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.


It's probably worth noting just because I said I tried it doesn't mean I  tried it properly, pretty sure this isn't an esoteric error rather than  a clear one two fix if I could figure it out.
```

---

### Post by oldfred on 2017-04-27
It says you have RAID.
Is this standard "FakeRAID" or BIOS RAID and then what type or the Intel SRT which looks like RAID to Linux drivers?

Desktop installer does not support RAID well, often server installer and then installing desktop of choice can work.
I thought it now saw the RAID, but grub never installs.

If you want to break the RAID  and it is RAID 0 (for speed, but risk of lost data) not much you can  do unless you want to totally back up & restore.
Some with RAID 1 break the RAID and have two drives. And RAID is not backup.
Those with Intel SRT need to turn off the Intel SRT and set drives for AHCI.

 Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by cypath on 2017-04-27
I'm not sure what kind of RAID it is. It's what shipped with the laptop, I've not touched it. I'll do some reading on identifying what types it is and see what I turn up. Backing up is no issue.

You think I should make a server install and then do the desktop? I'll look into this as well.

---

### Post by oldfred on 2017-04-27
May depend on type of RAID.

This is an older thread.
 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04.
15.04 or later now uses mdadm to support intel fakeraids 
User who installed fakeRAID
How to install Ubuntu 14.04 in software fakeraid RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126) 

The server installer is not a gui, & is text based. But still similar in process.

One of last screens should be similar to this:
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)
      
 Or:
sudo apt-get install ubuntu-desktop 
Or any of the other desktops.

---

### Post by cypath on 2017-04-28
I'm still yet to read over the RAID documents, will do soon. Also yet to try the server install, non GUI install is fine.

I had a second stab at the something else option from the installer, tried the below to no success but now have a bit better understanding of the partitions.
[https://www.youtube.com/watch?v=j5iFE6zBHPE](https://www.youtube.com/watch?v=j5iFE6zBHPE)
[https://www.youtube.com/watch?v=OU_dkeFprhY](https://www.youtube.com/watch?v=OU_dkeFprhY)
[https://www.youtube.com/watch?v=BcRnqqybMIQ](https://www.youtube.com/watch?v=BcRnqqybMIQ)

---

### Post by oldfred on 2017-04-28
Only looked at first video.
That is a standard BIOS/MBR install to a blank drive using Something Else.
Almost all new systems are UEFI/gpt. And you have added complication of RAID.

In your case I might consider another drive and full install to that.
I have done full installs to flash drives in both BIOS & UEFI mode. Not as speedy as internal drive and lot slower than SSD. But if USB3 using lighter weight gui like Lubuntu and a few minor settings changes to reduce writes to flash drive makes a very functional system. USB just will not be as long life as standard drive.
UEFI install to external drive is a bit more complex than BIOS. Most UEFI system can boot in either mode.

---

### Post by cypath on 2017-05-13
We were rapidly getting outside of my technical experience, I had a different OS installed just to get the comp working. On the bright side though, I have a much more modern non-raid comp that I did get Ubuntu running on, so I am still an Ubuntu user! Thanks for your assistance oldfred.

---

