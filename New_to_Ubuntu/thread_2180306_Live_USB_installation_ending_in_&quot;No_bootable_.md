---
title: "Live USB installation ending in &quot;No bootable device&quot; during first real start-up."
date: 2013-10-12
forum: New to Ubuntu
---

### Post by Durabys on 2013-10-12
My experience with Linux OS's: newbie.

I got a new Acer TravelMate TMB113-M-323a4G50akk netbook, Intel i3 processor, 4gb sdram, 500gb HDD, no optical disc mechanic.

It had Linpus OS installed on it from the factory. I downloaded UNebootin to my desktop Windows 7 PC. Then I torrented down Xubuntu 13.04 64bit .iso and using UNe, I created a Live USB on a 2GB USB. I put the USB into the netbook. Switched on. Went into BIOS with F2, changed things around in boot order so it will load the USB. Loaded the "Try Xubuntu without installation" and had a look. Liked it so I clicked on the "Install Xubuntu" icon on the desktop. Formated the disk and the previous OS. Installed Xubuntu. All fine still.

Then I was normally restarted and clicked F2 to get into BIOS and default it back to original settinga.. Put the Live USB stick out. Restarted again..
..and after the Acer emblem went away this appeared:

> Broadcom UNDI PXE-2.1 v15.0.11
Copyright (C) 200-2011 Broadcom Corporation
All rights reserved.
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Broadcom PXE ROM.
No bootable device -- insert boot disk and press any key

..if I press any key the message just repeats itself..even if I put the Live USB back.

---

### Post by VMC on 2013-10-12
Open a terminal (Ctrl+Alt+t), then type ```
**sudo fdisk -l /dev/sda**
``` [Assuming your using the first hard drive]

---

### Post by philinux on 2013-10-12
Sounds like grub did not install correctly or in the right place.

Might be worth running bootinfoscript from the usb stick. [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Durabys on 2013-10-12
> **VMC said:**
> Open a terminal (Ctrl+Alt+t), then type ```
sudo fdisl -l /dev/sda
``` [Assuming your using the first hard drive]

Open the terminal in BIOS, Post-Acer-emblem screen or through the Live Xubuntu USB?

*looks into BIOS* There is only a single HDD in the boot menu. *looks into the netbok specs on the internet* Yup. Only a single HDD.

> **philinux said:**
> Sounds like grub did not install correctly or in the right place.

 Might be worth running bootinfoscript from the usb stick. [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Interesting. Will try a little bit later. Thanks.

---

### Post by Durabys on 2013-10-12
Okay. Just for info. This is my BIOS settings.

[[IMG]http://s11.postimg.org/ejhzop3qn/DSC00068.jpg[/IMG]]("http://postimg.org/image/ejhzop3qn/")[[IMG]http://s11.postimg.org/5zu0d760f/DSC00069.jpg[/IMG]]("http://postimg.org/image/5zu0d760f/")[[IMG]http://s11.postimg.org/6zkb8wl67/DSC00070.jpg[/IMG]]("http://postimg.org/image/6zkb8wl67/")[[IMG]http://s11.postimg.org/uf28e94xb/DSC00071.jpg[/IMG]]("http://postimg.org/image/uf28e94xb/")

---

### Post by philinux on 2013-10-12
You need to run the fdisk command from the live usb and the bootinfoscript if anyone is going to be able to help you.

---

### Post by Durabys on 2013-10-12
Ok. First step. I will download the bootinfoscript and copy to the USB from my W7 desktop?

---

### Post by philinux on 2013-10-12
> **LhY8rJ7 said:**
> Ok. First step. I will download the bootinfoscript and copy to the USB from my W7 desktop?

yep you can run the script from the live usb you could use firefox on the live usb to download or from w7. Just read the instructions on the link I gave you.

---

### Post by Durabys on 2013-10-12
> **philinux said:**
> yep you can run the script from the live usb you could use firefox on the live usb to download or from w7. Just read the instructions on the link I gave you.

Problem.

> sudo: Downloads: command not found

---

### Post by philinux on 2013-10-12
I think you need 

```
cd Downloads
```

cd = change directories.

---

### Post by Durabys on 2013-10-12
> **philinux said:**
> I think you need 

```
cd Downloads
```

cd = change directories.

Okay. I extracted it and changed the directory. Now to use sudo?

EDIT1

Bingo. I have the file. I will post it in a minute.

---

### Post by Durabys on 2013-10-12
> **philinux said:**
> Sounds like grub did not install correctly or in the right place.

 Might be worth running bootinfoscript from the usb stick. [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)


Here is the result file.

```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sda3: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........|.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1716936 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

xubuntu-vg-root': ______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

xubuntu-vg-swap_1': ____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       391,167       389,120 EFI System partition
/dev/sda2         391,168       890,879       499,712 Data partition (Windows/Linux)
/dev/sda3         890,880   976,771,071   975,880,192 Logical Volume Manager (LVM) partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2021 MB, 2021654528 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     3,948,543     3,948,481   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/xubuntu--vg-root e4b6b348-9129-4c5e-9027-3d60dfd9e7b7   ext4       
/dev/mapper/xubuntu--vg-swap_1 5392879f-2f61-4571-aef6-170200c72dff   swap       
/dev/sda1        D64B-4896                              vfat       
/dev/sda2        c25b3b97-c3e4-49f4-9bb9-573b5a600b43   ext2       
/dev/sda3        RZ7CLK-l3ST-Srac-Vkgm-8cTs-BvDy-CRTJbf LVM2_member 
/dev/sdb1        8A97-C8A5                              vfat       TRAVELLER

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
xubuntu--vg-root
xubuntu--vg-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/xubuntu--vg-root /media/xubuntu/e4b6b348-9129-4c5e-9027-3d60dfd9e7b7 ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda2        /media/xubuntu/c25b3b97-c3e4-49f4-9bb9-573b5a600b43 ext2       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sda2/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod lvm
insmod ext2
set root='lvm/xubuntu--vg-root'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint='lvm/xubuntu--vg-root'  e4b6b348-9129-4c5e-9027-3d60dfd9e7b7
else
  search --no-floppy --fs-uuid --set=root e4b6b348-9129-4c5e-9027-3d60dfd9e7b7
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-e4b6b348-9129-4c5e-9027-3d60dfd9e7b7' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c25b3b97-c3e4-49f4-9bb9-573b5a600b43
    else
      search --no-floppy --fs-uuid --set=root c25b3b97-c3e4-49f4-9bb9-573b5a600b43
    fi
    linux    /vmlinuz-3.8.0-19-generic root=/dev/mapper/xubuntu--vg-root ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.8.0-19-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-e4b6b348-9129-4c5e-9027-3d60dfd9e7b7' {
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-e4b6b348-9129-4c5e-9027-3d60dfd9e7b7' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c25b3b97-c3e4-49f4-9bb9-573b5a600b43
        else
          search --no-floppy --fs-uuid --set=root c25b3b97-c3e4-49f4-9bb9-573b5a600b43
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /vmlinuz-3.8.0-19-generic root=/dev/mapper/xubuntu--vg-root ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.8.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-e4b6b348-9129-4c5e-9027-3d60dfd9e7b7' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c25b3b97-c3e4-49f4-9bb9-573b5a600b43
        else
          search --no-floppy --fs-uuid --set=root c25b3b97-c3e4-49f4-9bb9-573b5a600b43
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /vmlinuz-3.8.0-19-generic root=/dev/mapper/xubuntu--vg-root ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.8.0-19-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/grub.cfg                                  1
               =                initrd.img-3.8.0-19-generic                   70
               =                vmlinuz-3.8.0-19-generic                      23

=========================== sdb1/boot/grub/grub.cfg: ===========================

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

menuentry "Try Xubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Xubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash -- persistent

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit  persistent

label ubnentry1
menu label ^Try Xubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper  quiet splash -- persistent

label ubnentry2
menu label ^Install Xubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity  quiet splash -- persistent

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- persistent

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit  persistent

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit  persistent

label ubnentry6
menu label Try Xubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash -- persistent

label ubnentry7
menu label Install Xubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity quiet splash -- persistent

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true -- persistent

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash -- persistent

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on xubuntu-vg-root'


Unknown BootLoader on xubuntu-vg-swap_1'



=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/xubuntu/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
  skip_dev_dir: Couldn't split up device name xubuntu-vg-root'
  Volume group name xubuntu-vg-root' has invalid characters
  Skipping volume group xubuntu-vg-root'
  skip_dev_dir: Couldn't split up device name xubuntu-vg-root'
  Volume group name xubuntu-vg-root' has invalid characters
  Skipping volume group xubuntu-vg-root'
  skip_dev_dir: Couldn't split up device name xubuntu-vg-root'
  Volume group name xubuntu-vg-root' has invalid characters
  Skipping volume group xubuntu-vg-root'
hexdump: /dev/mapper/xubuntu-vg-root': No such file or directory
hexdump: /dev/mapper/xubuntu-vg-root': No such file or directory
  skip_dev_dir: Couldn't split up device name xubuntu-vg-swap_1'
  Volume group name xubuntu-vg-swap_1' has invalid characters
  Skipping volume group xubuntu-vg-swap_1'
  skip_dev_dir: Couldn't split up device name xubuntu-vg-swap_1'
  Volume group name xubuntu-vg-swap_1' has invalid characters
  Skipping volume group xubuntu-vg-swap_1'
  skip_dev_dir: Couldn't split up device name xubuntu-vg-swap_1'
  Volume group name xubuntu-vg-swap_1' has invalid characters
  Skipping volume group xubuntu-vg-swap_1'
hexdump: /dev/mapper/xubuntu-vg-swap_1': No such file or directory
hexdump: /dev/mapper/xubuntu-vg-swap_1': No such file or directory
```

---

### Post by Durabys on 2013-10-12
Could someone tell me how to repair the GRUB loader?

---

### Post by Durabys on 2013-10-13
Assistance requested, please.

---

### Post by philinux on 2013-10-13
I'm not familiar to be honest with this efi partition.  Or this new stuff UEFI. Other members and some staff are. I'll post this for you to read though.

I assume there's nothing important on the machine or at least you have a data backup.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Durabys on 2013-10-13
> **philinux said:**
> I'm not familiar to be honest with this efi partition.  Or this new stuff UEFI. Other members and some staff are. I'll post this for you to read though.

I assume there's nothing important on the machine or at least you have a data backup.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Nope. Nothing on the machine.

---

### Post by oldfred on 2013-10-13
From UEFI menu with UEFI on, but secure boot off does it give you ubuntu as a boot choice?
And with only one system installed, you may not get grub menu. Usually you have to hold shift key down until menu appears, but some with UEFI have to use escape key.
Then you may need boot paramater if black screen. 

But I do not know LVM. Did you install with full drive encryption? That is often why you get LVM which is a logical partition overlay over the physical partitions. Adds flexibility but is a lot more complex.

---

### Post by baabsaget on 2013-10-13
If you are on an EFI system, try installing rEFInd. On my setup, you have to run the grubx64.efi file from refind. Otherwise, I get the same error you do. Also, try using the partition table syncing tool that comes with.

refind - [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by Durabys on 2013-10-14
> **philinux said:**
> I'm not familiar to be honest with this efi partition.  Or this new stuff UEFI. Other members and some staff are. I'll post this for you to read though.

I assume there's nothing important on the machine or at least you have a data backup.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Something fishy is going on. I looked into the "Install Xubuntu" icon and then got to choosing the Installation type and this comes out:

[[IMG]http://s11.postimg.org/ut480q4i7/DSC00072.jpg[/IMG]]("http://postimg.org/image/ut480q4i7/")

How did Ubuntu appear there!?

> **oldfred said:**
> From UEFI menu with UEFI on, but secure boot off does it give you ubuntu as a boot choice?
And with only one system installed, you may not get grub menu. Usually you have to hold shift key down until menu appears, but some with UEFI have to use escape key.
Then you may need boot paramater if black screen. 

But I do not know LVM. Did you install with full drive encryption? That is often why you get LVM which is a logical partition overlay over the physical partitions. Adds flexibility but is a lot more complex.

Wait. Could you please repeat what you just said. I couldn't understand heads or tails from that.

> **baabsaget said:**
> If you are on an EFI system, try installing rEFInd. On my setup, you have to run the grubx64.efi file from refind. Otherwise, I get the same error you do. Also, try using the partition table syncing tool that comes with.

refind - [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

I will first try previously proposed ideas. Thank you nevertheless.

---

### Post by oldfred on 2013-10-14
If in your last screen shot you change from legacy to UEFI but leave secure boot off then does it give you a ubuntu boot option?
In legacy mode you do not have an install. Some system will just auto boot the UEFI anyway, yours may see no boot loader in MBR and just say you cannot boot.

Installer and boot managers do not know what gui or desktop environment you are running. So the all may say Ubuntu as the kernel is the same with all of them.

---

### Post by Durabys on 2013-10-16
Sorry. Still working on sorting this mess.

---

### Post by Durabys on 2013-10-17
My previous attempts to work with EFI/UEFI went awry. I got furious. Yeah. You can imagine how that went: I used GParted and formated the entire HDD. All of it. There is only non-used HDD space left.

Can someone please analyse this Boot Info Script RESULTS.txt that I made after this cataclysm soI know where to start anew?

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........|.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1716936 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2021 MB, 2021654528 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     3,948,543     3,948,481   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdc1        8A97-C8A5                              vfat       TRAVELLER
/dev/sr0                                                iso9660    Mobilni internet

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

menuentry "Try Xubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Xubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash -- persistent

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit  persistent

label ubnentry1
menu label ^Try Xubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper  quiet splash -- persistent

label ubnentry2
menu label ^Install Xubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity  quiet splash -- persistent

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- persistent

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit  persistent

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit  persistent

label ubnentry6
menu label Try Xubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash -- persistent

label ubnentry7
menu label Install Xubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity quiet splash -- persistent

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true -- persistent

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash -- persistent

--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

/home/xubuntu/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
  No volume groups found
```

---

### Post by oldfred on 2013-10-17
I have used gpt(GUID) partitioning since 10.10, but with BIOS only on Ubuntu only drives. XP was always on separate MBR drive.
Ubuntu will boot from gpt with either BIOS or UEFI if correct partitioning. 
If thinking of using Windows then if gpt you can only boot Windows with UEFI.
If drive is MBR(msdos), both Windows & Ubuntu have to boot in BIOS mode.

If Ubuntu only or you want to boot with UEFI, I would suggest gpt partitioning.

       I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning

If reinstalling Windows install it first as it has specific partition requirements on UEFI systems. But maybe make efi partition first so it is a bit larger than default from Windows installer.


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by Durabys on 2013-10-17
> **oldfred said:**
> I have used gpt(GUID) partitioning since 10.10, but with BIOS only on Ubuntu only drives. XP was always on separate MBR drive.
Ubuntu will boot from gpt with either BIOS or UEFI if correct partitioning. 
If thinking of using Windows then if gpt you can only boot Windows with UEFI.
If drive is MBR(msdos), both Windows & Ubuntu have to boot in BIOS mode.

If Ubuntu only or you want to boot with UEFI, I would suggest gpt partitioning.

       I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning

If reinstalling Windows install it first as it has specific partition requirements on UEFI systems. But maybe make efi partition first so it is a bit larger than default from Windows installer.


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

There was a Linux, Linpus, on the HDD before I formated it. I want to install Xubuntu there nothing else. There is also this little problem of GParted showing me only ~460GB on mz HDD.

---

### Post by oldfred on 2013-10-17
If a 500GB drive, 460GiB seems correct.

Similar thread.
[http://ubuntuforums.org/showthread.php?t=2180947](http://ubuntuforums.org/showthread.php?t=2180947)

1 Gigabyte (GB) = 1,000,000,000 bytes.
1 Gibibyte (GiB) = 1024x1024x1024 = 1,073,741,824 bytes
500/1.073 = 465

---

### Post by Durabys on 2013-10-18
> **oldfred said:**
> If a 500GB drive, 460GiB seems correct.

Similar thread.
[http://ubuntuforums.org/showthread.php?t=2180947](http://ubuntuforums.org/showthread.php?t=2180947)

1 Gigabyte (GB) = 1,000,000,000 bytes.
1 Gibibyte (GiB) = 1024x1024x1024 = 1,073,741,824 bytes
500/1.073 = 465

Hm. Thanks. So you think I should try the EFI/UEFI road? Isn't there an easier solution? :sad:

---

### Post by oldfred on 2013-10-18
Once installed both UEFI without secure boot and BIOS are the same as far as difficulty.

The new complexity is the choices of booting with UEFI or CSM/BIOS as that is how it installs. Before only some systems needed BIOS settings changed. Now every system does.

Then the standard issues of video drivers which you may have with any system depending on what video you have.

---

### Post by Durabys on 2013-10-22
Sweet holy mother of Christ! I solved this sucker. Ok. Here is what:

 Go into BIOS w/F2.
 Go to th "Boot" directory.
 Change Legacy into UEFI..and then got and install Xubuntu 13.04 from Life CD/USB. Works like a charm.

 I officially declare my problem solved and thank all the people and patient mods who helped me. Thank you all. :D

---

### Post by lodp2 on 2013-12-13
Thanks for posting your solution - saved me a lot of trouble. For reference I installed Kubuntu 13.10 on a Acer Travelmate P253 with pre-installed Linpus Linux. Bios was set to "Legacy Mode", changed it to UEFI, re-installed, boom, now it's working.

---

