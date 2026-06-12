---
title: "Dual Boot Ok, Now Win 7 fails boot with 0xc0000225 on ASUS G75VW"
date: 2015-10-28
forum: New to Ubuntu
---

### Post by steve230 on 2015-10-28
Dual boot Ubuntu 14.04 and Windows 7 was working fine. Now Win 7 fails to start with 0xc0000225, The boot selection failed because a required device is inaccessible.

The time line of events leading to this was:
dual boot fine
created clone on USB external drive that was 4 sectors smaller than hard drive using G4L, Ghost for Linux. Cloning process failed. After speaking with developer, it appears the GPT partition was not accounted for.
Launched gparted from hard drive and erased partitions on cloned external drive. 
Windows hasn't booted since, no response on screen from Windows on startup, nothing. Boot process simply drops into Grub2.
Ran Ubuntu package testdisk from Live USB to recover partitions.
Now Windows Boot Manager responds with failed to start and error code 0xc0000225.

Multiple methods have been attempted. ASUS does not have Windows Repair; Recovery partition has stopped responding. Microsoft says to check with manufacturer after attempting download of repair disk using product key.

Launching cmd in Windows from Live DVD and running several commands only yields zero installations of Windows found.
Attempted commands
> bootrec /fixboot
> bootrec /ReBuild
0 installations found

> bcdedit /enum
requested system device cannot be found
The boot configuration data store could not be opened

>bcdboot c:\Windows /l en-us /s b: /f UEFI
0 installations found

Purchased and downloaded EasyRe, same results on automated repair, 0 installations found.

Ran bootinfoscript.


Bootinfoscript Results
bootinfoscript output follows:
 
```
Boot Info Script 0.61 [1 April 2012]
============================= Boot Info Summary: ===============================
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector
1126572032 of the same hard drive for core.img, but core.img can not be
found at this location.
sda1: __________________________________________________________________________
File system: vfat
Boot sector type: Windows 7: FAT32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /efi/Boot/bkpbootx64.efi /efi/Boot/bkpbootx64_orig.efi
/efi/Boot/bootx64.efi /efi/Boot/bootx64_orig.efi
/efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi
/efi/ubuntu/shimx64.efi
sda2: __________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files:
sda3: __________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files:
sda4: __________________________________________________________________________
File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 14.04.3 LTS
Boot files: /boot/grub/grub.cfg /etc/fstab
sda5: __________________________________________________________________________
File system: swap
Boot sector type: -
Boot sector info:
sda6: __________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /bootmgr /boot/bcd
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
Partition Boot Start Sector End Sector # of Sectors Id System
/dev/sda1 1 1,953,525,167 1,953,525,167 ee GPT
GUID Partition Table detected.
Partition Start Sector End Sector # of Sectors System
/dev/sda1 2,048 411,647 409,600 EFI System partition
/dev/sda2 411,648 673,791 262,144 Data partition (Windows/Linux)
/dev/sda3 673,792 1,126,572,031 1,125,898,240 Data partition (Windows/Linux)
/dev/sda4 1,126,572,032 1,867,540,471 740,968,440 Data partition (Windows/Linux)
/dev/sda5 1,867,540,480 1,901,094,911 33,554,432 Swap partition (Linux)
/dev/sda6 1,901,094,912 1,953,523,711 52,428,800 Data partition (Windows/Linux)
"blkid" output: ________________________________________________________________
Device UUID TYPE LABEL
/dev/sda1 BE58-5669 vfat SYSTEM
/dev/sda2 312CDE4B30EE01F8 ntfs
/dev/sda3 94E094B9E094A2D2 ntfs OS
/dev/sda4 30ae8c72-396d-407b-a9e7-47f9cc8775d3 ext4
/dev/sda5 ae746612-618d-4206-acf1-61219ca58c2c swap
/dev/sda6 2434999C34997192 ntfs Recovery
================================ Mount points: =================================
Device Mount_Point Type Options
/dev/sda1 /boot/efi vfat (rw)
/dev/sda4 / ext4 (rw,errors=remount-ro)
=========================== sda4/boot/grub/grub.cfg: ===========================
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
if [ "${next_entry}" ] ; then
set default="${next_entry}"
set next_entry=
save_env next_entry
set boot_once=true
else
set default="0"
fi
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
insmod ext2
set root='hd0,gpt4'
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4 30ae8c72-396d-407b-a9e7-47f9cc8775d3
else
search --no-floppy --fs-uuid --set=root 30ae8c72-396d-407b-a9e7-47f9cc8775d3
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
if [ "${recordfail}" = 1 ] ; then
set timeout=30
else
if [ x$feature_timeout_style = xy ] ; then
set timeout_style=menu
set timeout=10
# Fallback normal timeout code in case the timeout_style feature is
# unavailable.
else
set timeout=10
fi
fi
### END /etc/grub.d/00_header ###
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
clear
fi
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-30ae8c72-396d-407b-a9e7-47f9cc8775d3' {
recordfail
load_video
gfxmode $linux_gfx_mode
gfxmode $linux_gfx_mode
insmod gzio
insmod part_gpt
insmod ext2
set root='hd0,gpt4'
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4 30ae8c72-396d-407b-a9e7-47f9cc8775d3
else
search --no-floppy --fs-uuid --set=root 30ae8c72-396d-407b-a9e7-47f9cc8775d3
fi
linux /boot/vmlinuz-3.13.0-66-generic.efi.signed root=UUID=30ae8c72-396d-407b-a9e7-47f9cc8775d3 ro quiet splash $vt_handoff
initrd /boot/initrd.img-3.13.0-66-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-30ae8c72-396d-407b-a9e7-47f9cc8775d3' {
menuentry 'Ubuntu, with Linux 3.13.0-66-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-66-generic-advanced-30ae8c72-396d-407b-a9e7-47f9cc8775d3' {
recordfail
load_video
gfxmode $linux_gfx_mode
insmod gzio
insmod part_gpt
insmod ext2
set root='hd0,gpt4'
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4 30ae8c72-396d-407b-a9e7-47f9cc8775d3
else
search --no-floppy --fs-uuid --set=root 30ae8c72-396d-407b-a9e7-47f9cc8775d3
fi
echo 'Loading Linux 3.13.0-66-generic ...'
linux /boot/vmlinuz-3.13.0-66-generic.efi.signed root=UUID=30ae8c72-396d-407b-a9e7-47f9cc8775d3 ro quiet splash $vt_handoff
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.13.0-66-generic
}
menuentry 'Ubuntu, with Linux 3.13.0-66-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-66-generic-recovery-30ae8c72-396d-407b-a9e7-47f9cc8775d3' {
recordfail
load_video
insmod gzio
insmod part_gpt
insmod ext2
set root='hd0,gpt4'
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4 30ae8c72-396d-407b-a9e7-47f9cc8775d3
else
search --no-floppy --fs-uuid --set=root 30ae8c72-396d-407b-a9e7-47f9cc8775d3
fi
echo 'Loading Linux 3.13.0-66-generic ...'
linux /boot/vmlinuz-3.13.0-66-generic.efi.signed root=UUID=30ae8c72-396d-407b-a9e7-47f9cc8775d3 ro recovery nomodeset
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.13.0-66-generic
}
menuentry 'Ubuntu, with Linux 3.13.0-65-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-65-generic-advanced-30ae8c72-396d-407b-a9e7-47f9cc8775d3' {
recordfail
load_video
gfxmode $linux_gfx_mode
insmod gzio
insmod part_gpt
insmod ext2
set root='hd0,gpt4'
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4 30ae8c72-396d-407b-a9e7-47f9cc8775d3
else
search --no-floppy --fs-uuid --set=root 30ae8c72-396d-407b-a9e7-47f9cc8775d3
fi
echo 'Loading Linux 3.13.0-65-generic ...'
linux /boot/vmlinuz-3.13.0-65-generic.efi.signed root=UUID=30ae8c72-396d-407b-a9e7-47f9cc8775d3 ro quiet splash $vt_handoff
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.13.0-65-generic
}
menuentry 'Ubuntu, with Linux 3.13.0-65-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-65-generic-recovery-30ae8c72-396d-407b-a9e7-47f9cc8775d3' {
recordfail
load_video
insmod gzio
insmod part_gpt
insmod ext2
set root='hd0,gpt4'
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4 30ae8c72-396d-407b-a9e7-47f9cc8775d3
else
search --no-floppy --fs-uuid --set=root 30ae8c72-396d-407b-a9e7-47f9cc8775d3
fi
echo 'Loading Linux 3.13.0-65-generic ...'
linux /boot/vmlinuz-3.13.0-65-generic.efi.signed root=UUID=30ae8c72-396d-407b-a9e7-47f9cc8775d3 ro recovery nomodeset
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.13.0-65-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-44-generic-advanced-30ae8c72-396d-407b-a9e7-47f9cc8775d3' {
recordfail
load_video
gfxmode $linux_gfx_mode
insmod gzio
insmod part_gpt
insmod ext2
set root='hd0,gpt4'
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4 30ae8c72-396d-407b-a9e7-47f9cc8775d3
else
search --no-floppy --fs-uuid --set=root 30ae8c72-396d-407b-a9e7-47f9cc8775d3
fi
echo 'Loading Linux 3.8.0-44-generic ...'
linux /boot/vmlinuz-3.8.0-44-generic.efi.signed root=UUID=30ae8c72-396d-407b-a9e7-47f9cc8775d3 ro quiet splash $vt_handoff
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.8.0-44-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-44-generic-recovery-30ae8c72-396d-407b-a9e7-47f9cc8775d3' {
recordfail
load_video
insmod gzio
insmod part_gpt
insmod ext2
insmod ext2
set root='hd0,gpt4'
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4 30ae8c72-396d-407b-a9e7-47f9cc8775d3
else
search --no-floppy --fs-uuid --set=root 30ae8c72-396d-407b-a9e7-47f9cc8775d3
fi
echo 'Loading Linux 3.8.0-44-generic ...'
linux /boot/vmlinuz-3.8.0-44-generic.efi.signed root=UUID=30ae8c72-396d-407b-a9e7-47f9cc8775d3 ro recovery nomodeset
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.8.0-44-generic
}
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/25_custom ###
menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root BE58-5669
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}
menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root BE58-5669
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}
menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root BE58-5669
chainloader (${root})/EFI/ubuntu/MokManager.efi
}
### END /etc/grub.d/25_custom ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-efi-BE58-5669' {
insmod part_gpt
insmod fat
set root='hd0,gpt1'
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1 BE58-5669
else
search --no-floppy --fs-uuid --set=root BE58-5669
fi
chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
set timeout=10
fi
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
### BEGIN /etc/grub.d/41_custom ###
if [ -f ${config_directory}/custom.cfg ]; then
source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------
=============================== sda4/etc/fstab: ================================
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda4 during installation
UUID=30ae8c72-396d-407b-a9e7-47f9cc8775d3 / ext4 errors=remount-ro 0 1
# /boot/efi was on /dev/sda1 during installation
#UUID=BE58-5669 /boot/efi vfat defaults 0 1
# swap was on /dev/sda6 during installation
UUID=546f03d9-79e9-451c-adb3-2183d6ced42e none swap sw 0 0
UUID=BE58-5669 /boot/efi vfat defaults 0 1
--------------------------------------------------------------------------------
=================== sda4: Location of files loaded by Grub: ====================
GiB - GB File Fragment(s)
=============================== StdErr Messages: ===============================
cat: /tmp/BootInfo-r2RUZVO9/Tmp_Log: No such file or directory
```

---

### Post by oldfred on 2015-10-28
Please use code tags which are easy to add with forum's advanced editor and the # icon for any longer code or terminal output. With Boot-Repair's Summary report often easiest to just post link it gives.

After all the repairs not sure what is going on.
Was Windows 7 installed in UEFI boot mode? Windows only boots from gpt partitioned drives with UEFI. And almost all Windows 7 installs were BIOS and have to be MBR(msdos) partitioned. If you convert drive from MBR to gpt then you break Windows.

You do have a non-working grub in the MBR for BIOS boot.

Your grub menu shows the Windows UEFI boot entry as /EFI/Microsoft/Boot/bootmgfw.efi, but script does not show that folder in sda1 at top of script. Did script just not show it or is that Microsoft folder now missing in ESP - efi system partition?

Does Ubuntu boot ok, in UEFI boot mode? Are you booting the /efi/ubuntu entry from UEFI?
And often the /efi/Boot entry of bootx64.efi is just a copy of Windows efi boot file bootmgfw.efi from the /efi/Microsoft folder.

If /efi/Microsoft folder is missing, we need to recreate it and add at least the Microsoft boot file & a /boot/BCD file. But those are all Widows repairs and cannot be done from Linux.

---

### Post by steve230 on 2015-10-28
The system was running dual boot for months. I think Windows was UEFI, but at this point I would need some kind of confirmation. I tried a reg query but did not have the correct key to confirm which boot mode.
[COLOR=#000000]/EFI/Microsoft/Boot/bootmgfw.efi does exist on /dev/sda1. There is another *.efi that is double the size at 1.2Mb. Bootmgfw.efi is 672Kb as per Microsoft. 
There are Windows Dos commands to get to that folder after launching Windows LiveDVD.
The system started out of the box Win 7 1Tb hard drive. I shrank, added partitions, and installed 12.04, then upgraded months later to 14.04. Everything was fine until deleting partitions on the clone drive.

I think Ubuntu boots fine. It goes to grub2 after Windows fails. Again, I do not know how to confirm the boot mode is UEFI. USBs only work if selecting UEFI in Win Boot manager.

I tried commands to recreate BCD but zero Windows installations were found.

I did fix one error. The UUID of the swap was incorrect between bootinfoscript and gparted. I edited the /etc/fstab to match the gparted UUID and Ubuntu booted with no issues.[/COLOR]

---

### Post by oldfred on 2015-10-28
If drive is gpt, then Windows has to boot in UEFI mode.
And since you have the Microsoft files in the ESP then that must be UEFI boot.

Did you turn secure boot on? Windows 7 is not compatible with Secure boot.

In the /efi/Microsoft is there also the /Boot with the BCD? If not you need to rebuild that. You do show a /Boot/BCD in sda6, but that is probably your recovery partition. And if Windows 7 it may just be a BIOS recovery?

Do you have a Windows entry in UEFI?

Run Boot-Repair but do not make any fixes yet, just post the link to the summary report. The first third of the report is just bootinfoscript (with some updates) but it has a lot more info. Be sure to boot it in UEFI mode or just run from your installed Ubuntu.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If partition sizes may have changed, you should run chkdsk from your Windows repair CD/Flash drive or installer. And run on all NTFS partitions.
       Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)

---

### Post by steve230 on 2015-10-28
BCD file does exist in same folder as the bootmgfs.efi. \EFI\Microsoft\boot

/dev/sda6 is the Recovery partition installed by ASUS.
I am not sure what Secure boot is. Some of the options that sound like they might be in the BIOS setup do not show up in my BIOS. I did not modify the BIOS.
I'll check the other items.

---

### Post by steve230 on 2015-10-29
BIOS is American Megatrends 223. There does not appear to be a secure boot. Security menu shows several hardware that are all unlock so they will function.
chkdsk run on 3 partitions with ntfs: /dev/sda2 and /dev/sda5 (Recovery partition) did have issues and were fixed. /dev/sda3 did not have issues. Win7 failed to start afterwards.

From another comment: /sys/firmware/efi does exist, so it would appear Ubuntu booted in UEFI mode.
$ sudo parted -l 
returns "Partition Table: gpt"  --> showing that the Windows was booting in UEFI.

Burning a Repair disc for Windows 7 home premium 64 bit failed to boot on ASUS laptop because Microsoft said the Windows versions did not match. The disc was burned on a Dell running Win 7 Home Premium 64 bit.

Do you have a Windows entry in UEFI? I don't know what this question means.
Will run Boot-Repair later.

---

### Post by steve230 on 2015-10-29
Ran boot-repair from the hard drive. Summary URL is below.
[http://paste.ubuntu.com/12998317/](http://paste.ubuntu.com/12998317/)

Summary report states SecureBoot is disabled.

Do you have a Windows entry in UEFI? Does this mean a line in the Grub2 menu for booting Windows?
The Grub2 menu does have several lines for booting Windows. Each can be edited on the fly to point to another file.

How do Mount points work? Does the /dev/sda3 where Windows data resides need to be mounted? Is the mount point of "/" correct for the Ubuntu partition /dev/sda4?

---

### Post by oldfred on 2015-10-29
Somewhere in your UEFI/BIOS should be a boot tab. It should show the same as this:
```
 efibootmgr -v
BootCurrent: 001A
Timeout: 0 seconds
BootOrder: 0019,001A,001B
Boot0019* Windows Boot Manager	HD(1,800,64000,090c8528-e85e-d34c-a45d-8546e4d07c6c)File(EFIMicrosoftBootbootmgfw.efi)
Boot001A* ubuntu	HD(1,800,64000,090c8528-e85e-d34c-a45d-8546e4d07c6c)File(EFIUbuntugrubx64.efi)
Boot001B* CD/DVD Drive 	BIOS(3,0,00)AMGOAMNO........o.H.L.-.D.T.-.S.T. .D.V.D.R.A.M. .G.T.5.1.N....................A...........................>..Gd-.;.A..MQ..L.7.M.C.J.I.5.4.I.2.5. .4. . . . . . . . ......AMBO

```

And sometimes booting directly from UEFI works to boot Windows. Grub only boots a working Windows. But you are not showing this file which should be in your main Windows partition.
 Windows/System32/winload.exe

Windows auto mounts other NTFS partitions and assigns labels like d:, e: etc.
Ubuntu can auto mount, but does not until you click on that partition with Nautilus or whatever file manager you use. And it assigns a the label, if you created one, or may use UUID or the very long number.
If an internal partition you should create a mount point and add an entry to fstab to auto mount in the same place every time you reboot. You also have to give yourself ownership & permissions to use that partition.

      
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

            [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
    
Manual mount from terminal:
 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data
[http://askubuntu.com/questions/324705/first-full-backup-on-usb-permission-denied/324942#324942](http://askubuntu.com/questions/324705/first-full-backup-on-usb-permission-denied/324942#324942)

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

Default install of Ubuntu is / (root) and swap. Many add either /home as another partition or data partition(s). I have data, backup, ISOs, and 25GB each for several other installs. And when using Windows had another NTFS shared data partition.

---

### Post by steve230 on 2015-10-29
If I mount the /dev/sda3 where the Windows data should be I find the familiar file structure under
/mnt/.Trash-1000/files.
What is a safe way to proceed? I do have a copy of these files on an external drive.
Could a simple massive copy of everything under directory "files" allow Windows to find what it needs?
Like this command? There is space on the partition to do this.
$ cp * /mnt

/mnt/.Trash-1000/files/Windows/System32/winload.exe does exist, as does winload.efi.

So, the main question of this post is could this copy work?

---

### Post by oldfred on 2015-10-29
Your trash-1000 is from Linux. Not sure why that would ever have occurred. 

If you open trash, does it see those files and can you just undelete them in trash?
Do not delete everything in trash or all those files will be gone. Or empty trash.

Did you have a full backup of Windows? Always best to have that.
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by steve230 on 2015-10-29
Copying a single file from ~/mnt/.Trash-1000/files/filename.txt ~/mnt
looks ok.

I will copy everything in same manner and see if Windows can boot.
I could not do a Windows backup. It would not work. That's why I was investigating cloning.

---

### Post by oldfred on 2015-10-29
Only if you are able to totally restore Windows will you have a working system.

But you may get enough back that a Windows full repair/restore may work.
This is for Windows 8.

 Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by steve230 on 2015-10-29
undo

---

### Post by steve230 on 2015-10-30
having issues posting replies.

---

### Post by steve230 on 2015-10-30
Made some progress. Win7 splash screen does come up, but blue screen error "unmountable_boot_volume"
I think the new guid is not being picked up somewhere by Windows on startup.
Steps taken:


launched Ubuntu, discovered Windows files and directories from original C: drive were in a separate path, /mnt/.Trash-1000/files.
Copied these files to path Windows was expecting.
$ cp -r -v -p * /mnt
This took hours, approx 1GiB per minute.


Launched Win Live DVD cmd.exe
> diskpart
diskpart> list vol
diskpart> sel vol 4    -- This is first partition containing bootmgr etc.
diskpart> assign letter=b:
diskpart> exit
> cd /d b:\EFI\Microsoft\boot
> ren BCD BCD_2.bak
> bcdedit /createstore BCD
> bcdedit /store BCD /create {bootmgr} /d "Windows Boot Manager"
> bcdedit /store BCD /create /d "Windows 7" /application osloader
> bcdedit /store BCD /set {bootmgr} default {guid num from previous step}
> bcdedit /store BCD /set {bootmgr} path \EFI\Microsoft\boot\bootmgfw.efi
> bcdedit /store BCD /set {bootmgr} locale en-us
> bcdedit /store BCD /set {bootmgr} displayorder {default}
> bcdedit /store BCD /set {default} device partition=c:
> bcdedit /store BCD /set {default} osdevice partition=c:
> bcdedit /store BCD /set {default} path \Windows\System32\winload.efi
> bcdedit /store BCD /set {default} systemroot \Windows
> exit


Restart computer. Windows fails after splash screen with above blue screen error.
Safe Mode
Last known Good
Normal


All selections failed.

---

### Post by oldfred on 2015-10-30
From Windows repair console run repairs 3 times.
And run chkdsk.

Not sure what else to suggest as something caused all Windows files to be deleted and unless restore to the same size partition and all files are there, it will not work.

---

### Post by steve230 on 2015-11-01
Reran bcdedit /enum and error stated it could not find device.
I'm not sure how to run a Windows Repair when the only apparent disc available from ASUS is a total erasure of the hard drive. 
I ran EasyRE and selected automated repair. It did get Windows to boot. Hard drive data for Windows appears to be intact. But it does a chkdsk each startup and has some kind of error as before. Windows complains something was installed and needs to be undone. The hex number is meaningless. Previous search does not show anything that make sense.
Now upon restart GRUB2 is no where to be found. Ubuntu is not even offered for booting.

C: drive in Windows is the correct size. Makes me think the other partitions are still there. 
Can $ sudo update-grub be run from Ubuntu Live USB to restore Grub2 on hard drive?

---

### Post by oldfred on 2015-11-01
You have to mount Ubuntu install and then install grub to sda.
You can also do same thing with Boot-Repair.

But grub only boots working Windows, so you need to resolve Windows issues first.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by steve230 on 2015-11-01
Ran Boot-repair, now Windows and Ubuntu both boot, but it is messy. In Ubuntu gparted is very confused. Windows always runs chkdsk and finds nothing wrong on its partition, NTFS. Gparted calls this same partition ext4 type filesystem. Something is very wrong.
So, boot-repair summary is below.
[http://paste.ubuntu.com/13079824/](http://paste.ubuntu.com/13079824/)

The machine is supposed to be GPT partition tables. Boot-Repair detects but says it is not used.

---

### Post by oldfred on 2015-11-02
It looks like you have created a hybrid system.
       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

And Since MBR only holds 4 partitions not all of the gpt partitions are in the MBR partition table. 
And formats in partition tables are different, so not fully sync'd.

When booting Windows are you booting the Windows boot in the MBR in BIOS mode? 
If UEFI it should boot from UEFI, using ESP - efi system partition and gpt partition table.

Windows only boots from MBR(msdos) with BIOS. Or BIOS boot can only be from MBR.
Windows only boots from gpt with UEFI.

Apple Macs uses to have to use hybrid to boot Windows as the Mac was one of the first with UEFI, but Windows on the Mac could only boot in MBR. Macs had a tool to sync partitions. Newer Mac & Windows installs are now all UEFI.

---

### Post by steve230 on 2015-11-02
I would like to go back to GPT, like you said MBR only sees 4 partitions. I did not intentionally create a MBR table. Boot-Repair on default settings was run and then the MBR showed up.
How do I answer the question:
[COLOR=#000000]    When booting Windows are you booting the Windows boot in the MBR in BIOS mode? [/COLOR]
[COLOR=#000000]    If UEFI it should boot from UEFI, using ESP - efi system partition and gpt partition table.

How do I undo the MBR table creation or set UEFI as default for startup?[/COLOR]

---

### Post by oldfred on 2015-11-02
You control booting from UEFI/BIOS boot menu. You should have settings for UEFI or CSM.

We normally do not erase the MBR boot code, it can be done with dd, but dd's nickname is data destroyer. And with BIOS boot you just write a new boot loader when desired. I do not think your Windows boot loader in the MBR will work anyway (it should not).

 [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
You can use gdisk to update gpt partition tables.
      
 [http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

If newer Ubuntu the live installer should have gdisk.
      
 sudo gdisk /dev/sda
Command (? for help): 

      
 Use gdisk and verify partitions are correct with p, and use w to write the partition table. The v command can give more details on issues if necessary.  If not correct just use q to quit. The w -write should update primary, backup & protective MBR.

---

### Post by steve230 on 2015-11-04
Thank you. System appears to have been returned to operational status with no loss of data, just tons of time.
gdisk worked as advertised. GPT was available to select and after checking with p and i options used w to write to disk. Gparted is no longer confused. I think the windows error of not finding the device was a partition needed by Windows, a partition of type Microsoft Reserved. - 128MiB. This partition follows the EFI System partition and immediately precedes the Windows data partition.

So quick recap...
GPT disks must be cloned carefully because of what I think is a lack of unique GUID numbers. But gdisk has an option to change GUID.
Deleting partitions on clone may have caused issues with partitions on hard drive, because the GUID's were not unique.
testdisk helped recover partitions
Copying Windows data from /mnt/.Trash-1000/files helped Windows find what it needed
EasyRE progressed the effort a little bit farther
gdisk returned GTP to an active status
--System now dual boots Ubuntu 14.04 and Win7
ASUS was of no help, does not provide Windows System Recovery disks

---

### Post by oldfred on 2015-11-04
Glad to got it resolved.

With gpt you should only copy entire drive, not clone each partition. Internal to partition is GUID which must match primary & backup gpt partition table. As you did find out, you can do major repairs with gdisk or sgdisk.

And these Windows backup tools supposedly work with Windows and gpt.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

