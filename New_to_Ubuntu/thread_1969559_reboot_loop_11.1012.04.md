---
title: "reboot loop 11.10/12.04"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by nachtigaller on 2012-04-30
hey everyone!

im not exactly new to linux but when it comes to needing help im as newbee as they come;). i have updated ubuntu from 10.10 to 11.10 a while ago and since then experienced various problems (programs crashing, network acting weird aso). most of them have thankfully been solved by updating again to 12.04.

the one problem that keeps popping up is the rebooting thing. if i start my computer everything goes normal up until the grub stage. from there booting xp works as it should but booting ubuntu is a pain, it keeps showing a blank screen and starts booting again. given i wait 5-8 reboots eventually the computer boots sucessfully. i have no idea what causes this, my googleing didnt yield any interesting results.

can you please tell me which commands i should run to diagnose my problem? (and subsequentlx help me solve it ;) )

thanks in advance!

---

### Post by audiomick on 2012-04-30
Hallo. 
That sounds to me like maybe Grub, the boot loader, is confused. I would suggest you go here

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

follow the instructions and post the output here. I can't promise to be able to interpret it myself, but that script will tell you pretty much all there is to know about things pertaining to booting. Hopefully it will help someone to help you. Who knows, maybe you will even see the problem yourself. The output looks daunting, but if you look at it carefully and closely and think about it a bit, a lot of it is actually very easy to understand. 

Anyway, run the script an post the output here. ;)

---

### Post by nachtigaller on 2012-04-30
thanks for helping out! below are the results. will look at them later, have to run now.



                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 Köpfe, 63 Sektoren/Spur, 9729 Zylinder, zusammen 156301488 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 NTFS / exFAT / HPFS
/dev/sda2          81,915,904   152,227,839    70,311,936  83 Linux
/dev/sda3         152,229,886   156,299,263     4,069,378   5 Extended
/dev/sda5         152,229,888   156,299,263     4,069,376  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        B09C788A9C784D3A                       ntfs       
/dev/sda2        95159273-687e-4193-b74e-353a8ae5ef24   ext4       
/dev/sda5        ad7676ca-96bb-4027-a942-c35020214b69   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 95159273-687e-4193-b74e-353a8ae5ef24
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 95159273-687e-4193-b74e-353a8ae5ef24
  set locale_dir=($root)/boot/grub/locale
  set lang=de_DE
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
menuentry 'Ubuntu, mit Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 95159273-687e-4193-b74e-353a8ae5ef24
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=95159273-687e-4193-b74e-353a8ae5ef24 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, mit Linux 3.2.0-24-generic-pae (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 95159273-687e-4193-b74e-353a8ae5ef24
    echo    'Linux 3.2.0-24-generic-pae wird geladen …'
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=95159273-687e-4193-b74e-353a8ae5ef24 ro recovery nomodeset 
    echo    'Initiale Ramdisk wird geladen …'
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 95159273-687e-4193-b74e-353a8ae5ef24
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 95159273-687e-4193-b74e-353a8ae5ef24
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root B09C788A9C784D3A
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=95159273-687e-4193-b74e-353a8ae5ef24 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ad7676ca-96bb-4027-a942-c35020214b69 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-24-generic-pae           2
               =                boot/vmlinuz-3.2.0-24-generic-pae              1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

xz: (stdin): Komprimierte Daten sind korrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

### Post by audiomick on 2012-04-30
Hmmm, looks alright to me, but don't take my word for it. Do have a look at it yourself, too. You should be able to work out what at least some of it is about.

How old is the computer? Is it possible that the hard drive is having problems?

Have a look in the hard drive utility and look at the SMART values for the drive. You can see my mouse pointer on the button for that in the screenshot.When you click on that, a window will open showing your the test result of the self testing that the drive does on itself. There is also a button in that window to run self tests on the disk surface. Go through that and make sure there is nothing wrong there.

The reason for looking at that is that the behaviour that you describe, including the fact that the old install had problems, might possibly be the result of difficulties reading the drive.

I have to admit I am guessing a bit. I do hope someone else looks at this thread who has a better idea.

---

### Post by nachtigaller on 2012-05-07
Hey,

sorry for the late answer. I have been sick. Anyhow, to me the last few line of this nice little report looked very fishy so i googled them. I now came up with a tool called boot-repair. I will keep you updated on whether it works and if not check my hard drives as you suggested.

---

### Post by nachtigaller on 2012-05-07
meh im sooo clever arent i, im having a process runing that keeps me from rebooting... for 80 more hours ;):p 
but i ran that script again and now it only says my compressed data is corrupt. that still doesnt sound nice to me but apparently i fixed a part of soem problem my computer had. now lets wait to see if it was the right one =)

---

### Post by nachtigaller on 2012-05-14
well it turns out these two neat little program solved my problem. thanks for helping me out!

---

### Post by nachtigaller on 2012-05-15
[ATTACH]217979[/ATTACH]it turns out i have been terribly wrong in my assessment of the situation. the first direct reboot was no problem. i shut the computer off, was out for the weekend, now i came back and it took about twice as long to boot as it did before i ran the bootrepair thingy. =( i will be trying to find out more about these corrupt compressed data files.

i opened that SMART window as you said (screenshots attached, its all german but from your location i infer you will be able to understand it, thankfully :) ) as you can see there are some values which might be iffy... im confused with so much data...
as for the age of the computer, well i dont really know but the information about the harddrive said its in use for 1.1 years now and i reckon that seems like close enough.

edit: as you might see the self test came up with no errors...

---

### Post by nachtigaller on 2012-05-18
as of now my windows partition also doesnt boot normally. please help!  :confused:     ](*,)    :-k   :cry:       [-o<       :shock:

---

### Post by nachtigaller on 2012-05-23
After a single kernel panic (and the old problem upon reboot) I installed 12.04 from scratch, the problem still persists. Im marking the thread as solved as im quite convinced this is not a problem of the OS...

---

