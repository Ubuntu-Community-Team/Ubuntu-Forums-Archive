---
title: "Cant boot into Ubuntu after installation of windows8"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by medusa93 on 2012-05-16
Hi everyone.
I have a Toshiba laptop on which I had Ubuntu12.04 and Windows XP.  I installed Windows 8 (consumer preview) after which I cannot find a way to get into Ubuntu. As of now I can use XP or Windows 8 but not Ubuntu. The XP was installed on the C partition and I installed Windows8 on what used to be the G partition on windowsXP. I can see that the 26GB ubuntu partition is still intact. 
When I switch on the laptop now, intially I get the windows8 menu where I am offered the option to use "an older version of the windows". Dont see the Ubuntu option anywhere while booting
Is there any way to get back Ubuntu without reinstalltion ? 
I do realize that I have been extremely adventurous with my laptop (for a person who understands very little how things work below the hood)
Thanks as always

---

### Post by Face-Ache on 2012-05-16
I understand that Windows installs overwrite the Master Boot Record with their own bootloader, when they are installed *after *Ubuntu - i did the same thing!  :)  The Windows bootloader doesn't recognise Linux/Ubuntu installations.

To fix it, i installed Ubuntu on a USB drive, booted to that, then downloaded Boot-Repair via the Ubuntu Software Centre, ran it, which then recreated the Master Boot Record with Linux's GRUB program (Grand UNified Bootloader - Linux's version of the Windows bootloader).

GRUB will allow you to boot to either Windows or Ubuntu.

Keep us posted on how you go.

---

### Post by jtarin on 2012-05-16
Or use LiveCD and reinstall Grub2.

---

### Post by Face-Ache on 2012-05-16
> **jtarin said:**
> Or use LiveCD and reinstall Grub2.

Could you please how you would do that without having to download Boot-Repair?

I used a LiveUSB when i needed to reinstall the GRUB, and i couldn't figure out how to reinstall GRUB - had to download Boot-Repair to do it.

Many thanks :)

---

### Post by wilee-nilee on 2012-05-16
Boot a Ubuntu live cd run these commands and look in home for a results.txt, copy and paste all the text from it to a reply. In the reply click the # in the reply panel generating code tags paste between them.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
``` ```
chmod a+x bootinfoscript
``````
sudo bash bootinfoscript
```

---

### Post by firo2011 on 2012-05-16
If you have more problems there is a gui you could use               "sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update"                                                                      Use that to add the repo, Then                                         "sudo apt-get install -y boot-repair && boot-repair"                     use this to add it and run but you'll have to do it from a live cd of course

---

### Post by medusa93 on 2012-05-16
As always, I feel delighted by how quickly I find help here in these forums. Please give me time to download a fresh copy of ubuntu, go and come back from earning my daily bread. Thats atleast a good 8-10 hours from now. Will keep you all posted
Thanks again

---

### Post by Face-Ache on 2012-05-16
> **firo2011 said:**
> If you have more problems there is a gui you could use               "sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update"                                                                      Use that to add the repo, Then                                         "sudo apt-get install -y boot-repair && boot-repair"                     use this to add it and run but you'll have to do it from a live cd of course

That's the 'Terminal' way of doing what i have suggested - by all means, do it that way; you open a Terminal with Ctrl-Alt-T

---

### Post by wilee-nilee on 2012-05-16
> **firo2011 said:**
> If you have more problems there is a gui you could use               "sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update"                                                                      Use that to add the repo, Then                                         "sudo apt-get install -y boot-repair && boot-repair"                     use this to add it and run but you'll have to do it from a live cd of course

Or just download the boot-repair cd

OP if you just download the cd this script I posted earlier can be generated from it with a click, so do that and wait to use the tool to repair until the script can be looked at

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Face-Ache on 2012-05-16
wilee-nilee has WAY more experience than us with this sort of thing - do definitely take his advice first  :)

---

### Post by jtarin on 2012-05-16
> **Face-Ache said:**
> Could you please how you would do that without having to download Boot-Repair?

I used a LiveUSB when i needed to reinstall the GRUB, and i couldn't figure out how to reinstall GRUB - had to download Boot-Repair to do it.

Many thanks :)I use the Live CD or USB and the [Chroot method]("https://help.ubuntu.com/community/Grub2/Installing#ChRoot"). More or less the backend for Boot Repair. Using the terminal gives me feedback and assurances I need sometimes.

---

### Post by Face-Ache on 2012-05-16
Thanks for explaining that.

I'll keep that in mind for the next time i mess up the GRUB  :D  Medusa93, this might also be an option for you if you are comfortable with using the Terminal.

---

### Post by medusa93 on 2012-05-17
```
Or just download the boot-repair cd

OP if you just download the cd this script I posted earlier can be  generated from it with a click, so do that and wait to use the tool to  repair until the script can be looked at

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)                                                                                                                                    *                                              Last edited by wilee-nilee; 14 Hours Ago at 09:31 PM..                                                           *             

```I have taken this advice and did a boot from this "Boot-Repair" cd. The result is
```

            Boot Info Script 0.61-git-patched      [23 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   206,850,047   206,848,000   7 NTFS / exFAT / HPFS
/dev/sda2         206,850,109   976,768,064   769,917,956   5 Extended
/dev/sda5         206,850,111   421,894,080   215,043,970   7 NTFS / exFAT / HPFS
/dev/sda6         421,894,144   572,206,077   150,311,934   7 NTFS / exFAT / HPFS
/dev/sda7         630,792,288   837,645,164   206,852,877   7 NTFS / exFAT / HPFS
/dev/sda8         837,645,228   976,768,064   139,122,837   7 NTFS / exFAT / HPFS
/dev/sda9         572,207,104   622,424,063    50,216,960  83 Linux
/dev/sda10        622,426,112   630,792,191     8,366,080  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        10F4275BF4274278                       ntfs       Windows
/dev/sda10       0f6a35cb-4d2d-486e-b5a5-90795ceca895   swap       
/dev/sda5        F29C05F49C05B45F                       ntfs       Suneel
/dev/sda6        F218FCF418FCB8A5                       ntfs       Added Programs
/dev/sda7        38B095E7B095AC3E                       ntfs       Music
/dev/sda8        361A67A31A675F3D                       ntfs       
/dev/sda9        c93a2a87-7eb8-4b0e-9d12-a213ff362460   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr0         /live/image              iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT
--------------------------------------------------------------------------------

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos9)'
  search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
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
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    echo    'Loading Linux 3.2.0-24-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    linux    /boot/vmlinuz-3.0.0-16-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.0.0-16-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    echo    'Loading Linux 3.0.0-16-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-16-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    linux    /boot/vmlinuz-3.0.0-15-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.0.0-15-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    echo    'Loading Linux 3.0.0-15-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-15-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    linux    /boot/vmlinuz-3.0.0-14-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.0.0-14-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    echo    'Loading Linux 3.0.0-14-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-14-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    echo    'Loading Linux 3.0.0-12-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    echo    'Loading Linux 2.6.38-11-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    echo    'Loading Linux 2.6.38-10-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root c93a2a87-7eb8-4b0e-9d12-a213ff362460
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 10F4275BF4274278
    drivemap -s (hd0) ${root}
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

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=c93a2a87-7eb8-4b0e-9d12-a213ff362460 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=0f6a35cb-4d2d-486e-b5a5-90795ceca895 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-2.6.38-10-generic-pae          2
            ?? = ??             boot/initrd.img-2.6.38-11-generic-pae          3
            ?? = ??             boot/initrd.img-3.0.0-12-generic-pae           2
            ?? = ??             boot/initrd.img-3.0.0-14-generic-pae           2
            ?? = ??             boot/initrd.img-3.0.0-15-generic-pae           2
            ?? = ??             boot/initrd.img-3.0.0-16-generic-pae           6
            ?? = ??             boot/initrd.img-3.2.0-24-generic-pae          12
            ?? = ??             boot/vmlinuz-2.6.38-10-generic-pae             1
            ?? = ??             boot/vmlinuz-2.6.38-11-generic-pae             1
            ?? = ??             boot/vmlinuz-3.0.0-12-generic-pae              1
            ?? = ??             boot/vmlinuz-3.0.0-14-generic-pae              2
            ?? = ??             boot/vmlinuz-3.0.0-15-generic-pae              1
            ?? = ??             boot/vmlinuz-3.0.0-16-generic-pae              2
            ?? = ??             boot/vmlinuz-3.2.0-24-generic-pae              2
            ?? = ??             vmlinuz                                        2
            ?? = ??             vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  40 08 c8 90 10 a6 9d d4  fa ad b4 fd e5 73 bc 5e  |@............s.^|
00000010  59 4c a3 ef a8 15 22 82  f8 54 91 c0 2a 20 d8 e0  |YL...."..T..* ..|
00000020  1f 40 c7 fe b8 58 0c af  e6 24 d0 11 1b 7c fc 20  |.@...X...$...|. |
00000030  9d 00 ba c8 e0 42 62 0c  4e be e6 01 32 30 f3 ed  |.....Bb.N...20..|
00000040  20 3c 58 b8 79 19 ac 80  ce f0 86 ee 73 61 0a 0b  | <X.y.......sa..|
00000050  1d a0 19 ba ef a9 98 53  18 45 bf 84 91 08 04 f8  |.......S.E......|
00000060  8e 6c c2 0e 0b 98 50 a6  12 7b 78 03 bb f9 98 5b  |.l....P..{x....[|
00000070  88 1c 7d 91 6c f0 01 f4  7a 85 1e 66 85 0a 16 24  |..}.l...z..f...$|
00000080  7a b8 74 1d d4 4f a2 2f  a3 1d 60 1b 58 07 82 22  |z.t..O./..`.X.."|
00000090  04 24 06 84 f5 5f c0 9d  dc 01 d8 a8 80 ab f9 9a  |.$..._..........|
000000a0  da c0 3c 8c 22 9b 2e 03  6c 20 58 78 e8 80 af 7f  |..<."...l Xx....|
000000b0  97 77 f4 01 19 21 42 a3  60 1f 0a 80 e2 c0 07 f7  |.w...!B.`.......|
000000c0  f4 62 2e 17 c0 eb c2 65  9e 03 56 17 7f 03 e4 72  |.b.....e..V....r|
000000d0  0e b8 c3 a0 67 ff 85 07  eb f8 b6 06 9a cc 80 5e  |....g..........^|
000000e0  a2 71 1e fe 67 64 68 8b  0e 88 31 c4 fb ba 98 90  |.q..gdh...1.....|
000000f0  3c 79 97 89 01 e4 48 c9  70 0c da 14 72 bb 52 52  |<y....H.p...r.RR|
00000100  b7 f4 ed e2 24 2a f6 9b  a7 15 7e 7d cf dd 42 2f  |....$*....~}..B/|
00000110  ef 1f 4b 92 bc a3 e8 8d  fc 2a 58 a0 21 70 1c a2  |..K......*X.!p..|
00000120  2f cc 23 a4 e8 f7 5d fe  6a 48 f9 49 dc fa 23 7c  |/.#...].jH.I..#||
00000130  cf 94 1f 7e bf 1d 77 7e  e7 c0 76 ff 30 84 d5 fc  |...~..w~..v.0...|
00000140  fb aa 52 6f ac e3 2b 39  b6 da 65 ef 96 ef 7f de  |..Ro..+9..e.....|
00000150  44 bf b7 bb bf a3 b1 d7  71 16 fe ce cd bb fb 3b  |D.......q......;|
00000160  bb fb 71 f7 77 d3 a1 57  da 97 77 ea 1b 99 28 0d  |..q.w..W..w...(.|
00000170  df b9 77 7f 97 77 d7 b8  f0 f8 74 ca cd 29 ad b7  |..w..w....t..)..|
00000180  ba 32 f7 ee f7 4c 97 3f  11 7f 79 ff 5c 65 ab cc  |.2...L.?..y.\e..|
00000190  bd fb a9 6e ec 65 ef dd  4b 57 6c bd ee ef 68 a2  |...n.e..KWl...h.|
000001a0  26 ce 28 df df 11 f5 fa  7f 26 cc bf cd 26 dd fe  |&.(......&...&..|
000001b0  69 b1 f7 f7 72 62 ef db  e0 95 1c bb 64 38 00 fe  |i...rb......d8..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 82 4f d1 0c 00 fe  |...........O....|
000001d0  ff ff 05 fe ff ff 84 4f  d1 0c 3d 94 f5 08 00 00  |.......O..=.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[6534]) leaked on lvscan invocation. Parent PID 6649: bash
File descriptor 8 (pipe:[6534]) leaked on lvscan invocation. Parent PID 6649: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-05-17__21h14 ===================
boot-repair version : 3.18-0ppa13~lucid
boot-sav version : 3.18-0ppa29~lucid
/usr/share/boot-sav/gui-g2slaunch.sh: line 91: hash: glade2script: not found
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
internet: no-internet
File descriptor 7 (pipe:[6534]) leaked on lvs invocation. Parent PID 3269: /bin/sh
File descriptor 8 (pipe:[6534]) leaked on lvs invocation. Parent PID 3269: /bin/sh
No volume groups found
boot-repair is executed in live-session (Debian GNU/Linux 6.0.3 (squeeze) , squeeze , Debian , i686)

=================== OSPROBER:
/dev/sda1:Windows Recovery Environment (loader):Windows:chain
/dev/sda9:Ubuntu 12.04 LTS (12.04):Ubuntu:linux

=================== BLKID:
/dev/sda1: LABEL="Windows" UUID="10F4275BF4274278" TYPE="ntfs"
/dev/sda5: LABEL="Suneel" UUID="F29C05F49C05B45F" TYPE="ntfs"
/dev/sda6: LABEL="Added Programs" UUID="F218FCF418FCB8A5" TYPE="ntfs"
/dev/sda7: LABEL="Music" UUID="38B095E7B095AC3E" TYPE="ntfs"
/dev/sda8: UUID="361A67A31A675F3D" TYPE="ntfs"
/dev/sda9: UUID="c93a2a87-7eb8-4b0e-9d12-a213ff362460" TYPE="ext4"
/dev/sda10: UUID="0f6a35cb-4d2d-486e-b5a5-90795ceca895" TYPE="swap"
/dev/loop0: TYPE="squashfs"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== /mnt/boot-sav/sda9/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not-on-gpt-disk,    part-has-no-fstab,    ntldr,    no-winload,    no-recov-nor-hid,    bootmgr,    no-grldr,    Boot/BCD,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda1.
sda5    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not-on-gpt-disk,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda5.
sda6    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not-on-gpt-disk,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda6.
sda7    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not-on-gpt-disk,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda7.
sda8    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not-on-gpt-disk,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda8.
sda9    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    32,    with-boot,    is-os,    not-on-gpt-disk,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    /mnt/boot-sav/sda9.

sda    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     2048 sectors * 512 bytes

=================== PARTED:

Model: ATA WDC WD5000BEVT-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  106GB  106GB   primary   ntfs            boot
2      106GB   500GB  394GB   extended
5      106GB   216GB  110GB   logical   ntfs
6      216GB   293GB  77.0GB  logical   ntfs
9      293GB   319GB  25.7GB  logical   ext4
10      319GB   323GB  4283MB  logical   linux-swap(v1)
7      323GB   429GB  106GB   logical   ntfs
8      429GB   500GB  71.2GB  logical   ntfs



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


=================== MOUNT:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sr0 on /live/image type iso9660 (ro,noatime)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda7 on /mnt/boot-sav/sda7 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda8 on /mnt/boot-sav/sda8 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda9 on /mnt/boot-sav/sda9 type ext4 (rw)


/sys/block/sda:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda10 sda2 sda5 sda6 sda7 sda8 sda9 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  agpgart block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dri dvd dvdrw fb0 fd full fuse fw0 hidraw0 hidraw1 hidraw2 hpet initctl input kmsg log MAKEDEV md mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda10 sda2 sda5 sda6 sda7 sda8 sda9 sg0 sg1 shm snapshot snd sndstat sr0 stderr stdin stdout urandom usb vga_arbiter xconsole zero

=================== DF:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.5G  8.3M  1.5G   1% /
tmpfs        tmpfs    1.5G     0  1.5G   0% /lib/init/rw
udev         tmpfs    1.5G  236K  1.5G   1% /dev
tmpfs        tmpfs    1.5G     0  1.5G   0% /dev/shm
/dev/sr0   iso9660    340M  340M     0 100% /live/image
tmpfs        tmpfs    1.5G  8.3M  1.5G   1% /live/cow
tmpfs        tmpfs    1.5G     0  1.5G   0% /live
tmpfs        tmpfs    1.5G  8.0K  1.5G   1% /tmp
/dev/sda1  fuseblk     99G   34G   66G  34% /mnt/boot-sav/sda1
/dev/sda5  fuseblk    103G   85G   18G  83% /mnt/boot-sav/sda5
/dev/sda6  fuseblk     72G   31G   42G  43% /mnt/boot-sav/sda6
/dev/sda7  fuseblk     99G   57G   43G  58% /mnt/boot-sav/sda7
/dev/sda8  fuseblk     67G   14G   53G  21% /mnt/boot-sav/sda8
/dev/sda9     ext4     24G   18G  4.7G  80% /mnt/boot-sav/sda9

=================== FDISK:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003dd9b

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12876   103424000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           12876       60801   384958978    5  Extended
/dev/sda5           12876       26262   107521985    7  HPFS/NTFS
/dev/sda6           26262       35619    75155967    7  HPFS/NTFS
/dev/sda7           39266       52141   103426438+   7  HPFS/NTFS
/dev/sda8           52142       60801    69561418+   7  HPFS/NTFS
/dev/sda9           35619       38745    25108480   83  Linux
/dev/sda10          38745       39265     4183040   82  Linux swap / Solaris

Partition table entries are not in disk order



=================== Before mainwindow
FSCK no PASTEBIN yes WUBI no WINBOOT yes
recommendedrepair, reinstall, QTY_OF_PART_FOR_REINSTAL 1 no-kernel-purge
UNHIDEBOOT_ACTION yes (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB sda9, FORCE_GRUB no (sda) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sda5) grub2 (0, 0 , )
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE  ( )

=================== Actions
FSCK no PASTEBIN yes WUBI no WINBOOT no
bootinfo, nombraction, QTY_OF_PART_FOR_REINSTAL 1 no-kernel-purge
UNHIDEBOOT_ACTION no (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB sda9, FORCE_GRUB no (sda) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sda5) grub2 (0, 0 , )
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE  ( )
No change has been performed on your computer. See you soon!
internet: no-internet
internet: no-internet


```

---

### Post by wilee-nilee on 2012-05-17
I think if you run the recommended repair on the boot-repair tool you will be set.

If this gets you into Ubuntu just to be sure your are set run this command.

```
sudo update-grub
```

---

### Post by medusa93 on 2012-05-17
I am now able to boot into Ubuntu and use it 
Please see the attached images
The boot loader now contains one extra-line, "previous linux versions". There are no previous linux versions on my laptop
[IMG]http://http://s910.photobucket.com/albums/ac302/havtrouble/?action=view&current=1.jpg[/IMG]
The windows option is now abbreviated as windows 8 loader (on /dev/sda1) If I opt for this I get to boot into windows 8 or "previous version of windows" which is XP.  All of these OS works.
[IMG]http://http://s910.photobucket.com/albums/ac302/havtrouble/?action=view&current=1.jpg#%21oZZ3QQcurrentZZhttp%3A%2F%2Fs910.photobucket.com%2Falbums%2Fac302%2Fhavtrouble%2F%3Faction%3Dview%26current%3D2.jpg[/IMG]
when I ran the update command after booting into Ubuntu,
[IMG]http://s910.photobucket.com/albums/ac302/havtrouble/?action=view&current=1.jpg#%21oZZ2QQcurrentZZhttp%3A%2F%2Fs910.photobucket.com%2Falbums%2Fac302%2Fhavtrouble%2F%3Faction%3Dview%26current%3D3.jpg[/IMG]```
sudo update-grub 
```
 I find that there is another extra line added windows 8 loader (on /dev/sda6) 
Choosing this option results in the screen looping to the Toshiba splash screen and to boot loader 
Fair enough! As far as I am concerned, this problem is solved

---

### Post by wilee-nilee on 2012-05-17
> **medusa93 said:**
> I am now able to boot into Ubuntu and use it 
Please see the attached images
The boot loader now contains one extra-line, "previous linux versions". There are no previous linux versions on my laptop
[IMG]http://http://s910.photobucket.com/albums/ac302/havtrouble/?action=view&current=1.jpg[/IMG]
The windows option is now abbreviated as windows 8 loader (on /dev/sda1) If I opt for this I get to boot into windows 8 or "previous version of windows" which is XP.  All of these OS works.
[IMG]http://http://s910.photobucket.com/albums/ac302/havtrouble/?action=view&current=1.jpg#%21oZZ3QQcurrentZZhttp%3A%2F%2Fs910.photobucket.com%2Falbums%2Fac302%2Fhavtrouble%2F%3Faction%3Dview%26current%3D2.jpg[/IMG]
when I ran the update command after booting into Ubuntu,
[IMG]http://s910.photobucket.com/albums/ac302/havtrouble/?action=view&current=1.jpg#%21oZZ2QQcurrentZZhttp%3A%2F%2Fs910.photobucket.com%2Falbums%2Fac302%2Fhavtrouble%2F%3Faction%3Dview%26current%3D3.jpg[/IMG]```
sudo update-grub 
``` I find that there is another extra line added windows 8 loader (on /dev/sda6) 
Choosing this option results in the screen looping to the Toshiba splash screen and to boot loader 
Fair enough! As far as I am concerned, this problem is solved

The previous versions of ubuntu are just extra kernels, standard stuff, best to keep at least one extra kernel set.

With a windows setup, if you have installed W8 while you have W7 installed without doing specific installs to preformatted NTFS partitions there is a boot partition made in the original W7 and W8 becomes attached to the W7. I never use a windows boot partition myself but make a NTFS and custom install to it, this prevents entanglement of the boot in windows. The boot partition has several uses in windows, first it is for encrypting, and second for using a recovery partition, I never use either. Probably other uses, but those are the main ones. 

Not sure how to adjust the windows boot, but I suspect someone on the forum is aware.

Glad you are back in at the least. ;)

---

### Post by oldfred on 2012-05-17
Your Windows 8 is not in a primary partition, so it can only boot thru the XP install in sda1.

Normally Windows 7 moves both bootmgr & BCD to the primary partition with the boot flag and grub2 os-prober only finds the one version of Windows which then will let you boot multiple Windows. But grub does not boot each version of Windows independently.  If you installed  8 to a primary partition then you may be able to directly boot it from grub2's menu.

You are getting the entry for sda8 as that copy still has bootmgr in it. Not sure if Windows 8 needs that or not as you also have a copy in your XP sda1 partition.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by jtarin on 2012-05-17
Until you feel more proficient, you might look to my signature for the link to _EasyBCD_ as a way to setup your dual/triple boot scheme.

---

### Post by wilee-nilee on 2012-05-17
> **jtarin said:**
> until you feel more proficient, you might look to my signature for the link to easybcd as a way to setup your dual/triple boot scheme.

rotfl. :)

---

### Post by jtarin on 2012-05-17
> **wilee-nilee said:**
> rotfl. :)I assume this is a derisive response? If not I apologize for the assumption.If you don't fully realize something don't deride it. Appreciate someone else's experience. ;)

Let me quote **_you_** in another post on another tool, Boot Repair:
> *As an addendum to my rhetoric I rather give a link or tool to be used rather then having to carefully explain and write commands. I would rather people have tools or knowledge that they can use when no help is around or limited for whatever reason.


I understand from that thread where your coming from with your attachment to "Boot Script"....it's an excellent diagnostic tool for knowledgeable adherents to use. I have my own philosophy considering multi-boots and repairing MBR's and these run the gamut from beginner to advance. 
I have been dual-booting since Win95/boot.ini
Not everyone prefers their MBR overwritten by Grub/Lilo. Reinstallation of Windows causes these very kind of problems with Grub we're discussing here.
As an addendum to my post....also in my signature:"The post above and the post below suffer from the Rashomon effect!";)

---

### Post by Face-Ache on 2012-05-17
> **medusa93 said:**
> As far as I am concerned, this problem is solved

That's good news; well done!  :)

I recommend Grub Customizer as a way of tidying up your boot options. It uses simple tick-boxes for the OS's you want displayed. You can also change the names of those OS's, so that they just say "Ubuntu 11.10" or "Windows XP".

Via the Grub Customizer Preferences ---> Appearance tab you can also customize the background for the OS selection screen, and the colors of the words.

---

### Post by medusa93 on 2012-05-18
I have used the grub customizer and changed the boot menu from this[IMG]http://i910.photobucket.com/albums/ac302/havtrouble/3.jpg[/IMG]
[IMG]http://http://i910.photobucket.com/albums/ac302/havtrouble/3.jpg[/IMG]
to this
[IMG]http://i910.photobucket.com/albums/ac302/havtrouble/4-400x400.jpg[/IMG]
I removed the last line Windows 8 (loader)  (on /dev/sda8 ) This option was doing nothing. Choosing this option simply lead the laptop screen to loop between the Introductory screen and the boot screen. That is as much as I dare. 
Thank you all.  You have all been a great help

---

