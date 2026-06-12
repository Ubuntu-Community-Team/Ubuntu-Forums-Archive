---
title: "Problems with Grub"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by GenerationII on 2011-10-18
I'm a big newbie here. I've had limited experience with OpenSuse and Fedora, but that's it. I installed Ubuntu on my main hard drive alongside Windows 7Windows installation disk and restore my original boot loader, but GRUB can't boot that either.

---

### Post by oldfred on 2011-10-18
Welcome to the forums.

Post this so we can see where things are at.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

If repairs are simple this may fix them and it runs to boot script so we can suggest what to fix.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by GenerationII on 2011-10-19
```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    20,686,847    20,480,000   7 NTFS / exFAT / HPFS
/dev/sda3          20,686,848   143,566,847   122,880,000   7 NTFS / exFAT / HPFS
/dev/sda4         143,568,894   625,141,759   481,572,866   f W95 Extended (LBA)
/dev/sda5         143,568,896   543,968,427   400,399,532   7 NTFS / exFAT / HPFS
/dev/sda6         543,969,280   619,384,831    75,415,552  83 Linux
/dev/sda7         619,386,880   625,141,759     5,754,880  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3030-3030                              vfat       DELLUTILITY
/dev/sda2        CC70378A703779F2                       ntfs       Recovery
/dev/sda3        AC7C4EC27C4E86D4                       ntfs       OS
/dev/sda5        7CE2D52DE2D4EC80                       ntfs       DATA
/dev/sda6        ae92edf4-81f9-4900-a72b-746ce7c8bff8   ext4       
/dev/sda7        d5b5ecdd-10de-40c1-8985-4f3555c606af   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root ae92edf4-81f9-4900-a72b-746ce7c8bff8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root ae92edf4-81f9-4900-a72b-746ce7c8bff8
  set locale_dir=($root)/boot/grub/locale
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root ae92edf4-81f9-4900-a72b-746ce7c8bff8
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ae92edf4-81f9-4900-a72b-746ce7c8bff8 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root ae92edf4-81f9-4900-a72b-746ce7c8bff8
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ae92edf4-81f9-4900-a72b-746ce7c8bff8 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root ae92edf4-81f9-4900-a72b-746ce7c8bff8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root ae92edf4-81f9-4900-a72b-746ce7c8bff8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root CC70378A703779F2
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=ae92edf4-81f9-4900-a72b-746ce7c8bff8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=d5b5ecdd-10de-40c1-8985-4f3555c606af none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  1c 58 00 00 00 00 00 00  19 ff 02 fe 9b c5 ca 01  |.X..............|
00000010  de 8c 53 0c f0 fe ca 01  de 8c 53 0c f0 fe ca 01  |..S.......S.....|
00000020  19 ff 02 fe 9b c5 ca 01  00 c0 01 00 00 00 00 00  |................|
00000030  d6 b1 01 00 00 00 00 00  20 00 00 00 00 00 00 00  |........ .......|
00000040  19 ff 02 fe 9b c5 ca 01  de 8c 53 0c f0 fe ca 01  |..........S.....|
00000050  de 8c 53 0c f0 fe ca 01  19 ff 02 fe 9b c5 ca 01  |..S.............|
00000060  00 c0 01 00 00 00 00 00  60 b1 01 00 00 00 00 00  |........`.......|
00000070  20 00 00 00 00 00 00 00  8f dd 01 0d 00 00 00 00  | ...............|
00000080  76 dd 01 0d 00 00 00 00  76 dd 01 0d 00 00 00 00  |v.......v.......|
00000090  98 00 00 00 00 00 00 00  01 00 00 00 18 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  14 00 14 00 28 00 38 00  |............(.8.|
000000b0  60 00 38 00 a8 01 01 00  00 00 a0 0b 00 00 08 00  |`.8.............|
000000c0  04 00 00 00 00 00 00 00  1c 58 00 00 00 00 00 00  |.........X......|
000000d0  19 ff 02 fe 9b c5 ca 01  de 8c 53 0c f0 fe ca 01  |..........S.....|
000000e0  de 8c 53 0c f0 fe ca 01  19 ff 02 fe 9b c5 ca 01  |..S.............|
000000f0  00 c0 01 00 00 00 00 00  d6 b1 01 00 00 00 00 00  |................|
00000100  20 00 00 00 00 00 00 00  19 ff 02 fe 9b c5 ca 01  | ...............|
00000110  de 8c 53 0c f0 fe ca 01  de 8c 53 0c f0 fe ca 01  |..S.......S.....|
00000120  19 ff 02 fe 9b c5 ca 01  00 c0 01 00 00 00 00 00  |................|
00000130  60 b1 01 00 00 00 00 00  20 00 00 00 00 00 00 00  |`....... .......|
00000140  a8 dd 01 0d 00 00 00 00  8f dd 01 0d 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  28 00 00 00 00 00 00 00  |........(.......|
00000160  01 00 00 00 18 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  1b 00 01 00 28 00 00 00  28 00 00 00 18 00 00 00  |....(...(.......|
00000180  00 00 00 00 00 00 02 00  00 00 00 00 00 00 00 00  |................|
00000190  22 00 00 00 30 40 eb 83  b3 dd 01 0d 00 00 00 00  |"...0@..........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  58 00 00 00 00 00 00 00  01 00 00 00 18 00 00 fe  |X...............|
000001c0  ff ff 07 fe ff ff 02 00  00 00 ac 9c dd 17 00 fe  |................|
000001d0  ff ff 05 fe ff ff ae 9c  dd 17 54 c3 7e 04 00 00  |..........T.~...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by mörgæs on 2011-10-19
Changed the title to a more descriptive one.

---

### Post by oldfred on 2011-10-19
Is this an older computer with newer larger hard drive and a BIOS with the 137GB boot limit.

Or a newer computer with BIOS settings that act like an older computer? Some need settings changed like these comments I have saved from others:

Disable Quickboot in BIOS
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

---

### Post by GenerationII on 2011-10-19
It's a Dell Inspiron only a little over a year old. I don't know about the BIOS, but I can't get into it anyway. I really have no idea what I'm doing. all I want to do is uninstall Ubuntu and GRUB so I can reinstall it and uninstall Windows.

---

### Post by oldfred on 2011-10-19
You have to be able to get to BIOS. Sometimes settings in BIOS are essential. It should show you on the BIOS start screen what key to use, often del, or f2 but systems vary.

If removing windows you should back it up first. Make the full set of recovery DVDs so if you ever sell it and the buyer wants Windows you have it. Vendor should have info on exactly how to do that.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by GenerationII on 2011-10-20
I have backed everything up. At the beginning of my BIOS start screen it gives me the keys to press for the settings and to choose my boot device but pressing these keys doesn't do anything and it just goes to the GRUB start screen.

---

### Post by oldfred on 2011-10-20
Then is keyboard working or plugged in. BIOS should see keyboard.

---

