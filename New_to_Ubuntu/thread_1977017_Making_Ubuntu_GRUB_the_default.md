---
title: "Making Ubuntu GRUB the default"
date: 2012-05-09
forum: New to Ubuntu
---

### Post by joetait on 2012-05-09
Hi

I have a number of OS's, and when I update say Mint, then Mint GRUB seems to become the default one i.e. if I want to change the default OS, I need to edit the grub.cfg file in my Mint partition.

Is there a way to change it back so that my Ubuntu grub is the file that is used?

Thanks

Joe

---

### Post by grahammechanical on 2012-05-09
Use this. I do. Works great.

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

Put on the Ubuntu install and run it every time Mint takes over the boot loader.

Regards.

---

### Post by joetait on 2012-05-09
Much as that looks like an awesome GUI, and I will use it when my Ubuntu GRUB is working, I think it is just editing my files in Ubuntu. But this is not where the bootloader (I think this is the right term) is pointing to - it is pointing to the Mint bootloader, i.e. the file /mint/boot/grub/grub/cfg (I load my mint partition to /mint).

Thanks anyway :)

---

### Post by oldfred on 2012-05-09
Boot into Ubuntu

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
[COLOR=DarkRed]sudo grub-install /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

### Post by joetait on 2012-05-09
Just to check I haven't missed something, how does running
sudo fdisk -l
tell me which drive Ubuntu is on?
The output is
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa8a8a8a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    15624191     7811072   82  Linux swap / Solaris
/dev/sda2   *    15626238   976771071   480572417    5  Extended
/dev/sda5        15626240    46874623    15624192   83  Linux
/dev/sda6        46876672    78125055    15624192   83  Linux
/dev/sda7        78127104   109375487    15624192   83  Linux
/dev/sda8       109377536   140625919    15624192   83  Linux
/dev/sda9       140627968   171876351    15624192   83  Linux
/dev/sda10      171878400   203126783    15624192   83  Linux
/dev/sda11      203128832   234377215    15624192   83  Linux
/dev/sda12      234379264   265627647    15624192   83  Linux
/dev/sda13      898648064   976771071    39061504   83  Linux
/dev/sda14      265629696   898643967   316507136   83  Linux

```

I think I am confusing drive and partition perhaps, because at first I thought you would wanted /dev/sda5, which is where Ubuntu (root files etc) are installed. But is the drive actually just /dev/sda? 

I wanted to check just in case I leave myself with an unbootable system, so I am being a bit paranoid. Sorry for the annoying questions!

---

### Post by oldfred on 2012-05-09
The assumption then is you only have one Linux partition and one drive sda. But you just want the MBR to point to the install that you primarily boot into.

In your case I would run boot info script to both know where everything is at and document system.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by joetait on 2012-05-09
Output of the Boot Info Script:

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v0.97) is installed in the boot sector 
                       of sda2 and looks at sector 127049264 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #8 
                       for /boot/grub/menu.lst.

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 12 Lisa
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Welcome to openSUSE 11.4 
                       "Celadon" - Kernel ().
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v0.97) is installed in the boot sector 
                       of sda9 and looks at sector 151332520 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #9 
                       for /boot/grub/menu.lst.
    Operating System:  PCLinuxOS release 2011 
                       (PCLinuxOS) for i586 Kernel 2.6.38.8-pclos1.bfs on a 
                       4-processor i686 /
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Trisquel GNU/Linux 5.5
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda13: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda14: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    15,624,191    15,622,144  82 Linux swap / Solaris
/dev/sda2    *     15,626,238   976,771,071   961,144,834   5 Extended
/dev/sda5          15,626,240    46,874,623    31,248,384  83 Linux
/dev/sda6          46,876,672    78,125,055    31,248,384  83 Linux
/dev/sda7          78,127,104   109,375,487    31,248,384  83 Linux
/dev/sda8         109,377,536   140,625,919    31,248,384  83 Linux
/dev/sda9         140,627,968   171,876,351    31,248,384  83 Linux
/dev/sda10        171,878,400   203,126,783    31,248,384  83 Linux
/dev/sda11        203,128,832   234,377,215    31,248,384  83 Linux
/dev/sda12        234,379,264   265,627,647    31,248,384  83 Linux
/dev/sda13        898,648,064   976,771,071    78,123,008  83 Linux
/dev/sda14        265,629,696   898,643,967   633,014,272  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5   swap       
/dev/sda10       3a997e4d-3835-4afc-9eac-f177731407c9   ext4       
/dev/sda11       175b7ad6-ca78-447b-b00b-164ed7bad9e3   ext4       
/dev/sda12       c24d3e2d-5215-4476-8672-d7dee8cf1d6c   ext4       
/dev/sda14       c4813164-1ffb-485a-aab1-5039d8b51510   ext4       
/dev/sda5        7d2aec80-c363-49ce-aeca-83bbfd436499   ext4       
/dev/sda6        7cb5ec52-7a5c-40c9-983b-ead92e812fca   ext4       
/dev/sda7        01966a49-f488-4171-b153-6f29725eae24   ext4       _Fedora-15-x86_6
/dev/sda8        1aef5c91-3a2e-4da1-939d-72ac0eb429f2   ext4       
/dev/sda9        ab57dbf3-3166-470f-bdcf-7313114f59f6   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /kubuntu                 ext4       (rw,noatime)
/dev/sda11       /trisquel                ext4       (rw,noatime)
/dev/sda12       /other2                  ext4       (rw)
/dev/sda14       /home/joe/files          ext4       (rw,noatime)
/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /mint                    ext4       (rw)
/dev/sda7        /fedora                  ext4       (rw,noatime)
/dev/sda9        /pclinux                 ext4       (rw)


=========================== sda5/boot/grub/menu.lst: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux    /boot/vmlinuz-3.0.0-14-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    echo    'Loading Linux 3.0.0-14-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-14-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux    /boot/vmlinuz-3.0.0-13-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    echo    'Loading Linux 3.0.0-13-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-13-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    echo    'Loading Linux 3.0.0-12-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=3a997e4d-3835-4afc-9eac-f177731407c9 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=3a997e4d-3835-4afc-9eac-f177731407c9 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Linux Mint 11, 2.6.38-8-generic-pae (/dev/sda6) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Linux Mint 11, 2.6.38-8-generic-pae (/dev/sda6) -- recovery mode (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro single
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Fedora (2.6.38.6-26.rc1.fc15.x86_64) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 01966a49-f488-4171-b153-6f29725eae24
    linux /boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=UUID=01966a49-f488-4171-b153-6f29725eae24 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=uk rhgb quiet
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
}
menuentry "Desktop -- openSUSE 11.4 - 2.6.37.6-0.7 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1aef5c91-3a2e-4da1-939d-72ac0eb429f2
    linux /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part8 resume=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part1 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.37.6-0.7-desktop
}
menuentry "Failsafe -- openSUSE 11.4 - 2.6.37.6-0.7 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1aef5c91-3a2e-4da1-939d-72ac0eb429f2
    linux /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part8 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x317
    initrd /boot/initrd-2.6.37.6-0.7-desktop
}
menuentry "linux (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet vmalloc=256M acpi=on resume=UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5 splash=silent vga=788
    initrd (hd0,8)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet vmalloc=256M acpi=on resume=UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5
    initrd (hd0,8)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet failsafe vmalloc=256M acpi=on
    initrd (hd0,8)/boot/initrd.img
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

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos14)'
search --no-floppy --fs-uuid --set=root c4813164-1ffb-485a-aab1-5039d8b51510
insmod jpeg
if background_image /Pictures/wallpapers/677KP.jpg; then
  set color_normal=dark-gray/black
  set color_highlight=magenta/light-cyan
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
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
    savedefault
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    echo    'Loading Linux 3.2.0-24-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=3a997e4d-3835-4afc-9eac-f177731407c9 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=3a997e4d-3835-4afc-9eac-f177731407c9 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Trisquel GNU/Linux, with Linux-Libre 3.0.0-19-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux /boot/vmlinuz-3.0.0-19-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-19-generic
}
menuentry "Trisquel GNU/Linux, with Linux-Libre 3.0.0-19-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux /boot/vmlinuz-3.0.0-19-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-19-generic
}
menuentry "Trisquel GNU/Linux, with Linux-Libre 2.6.38-13-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux /boot/vmlinuz-2.6.38-13-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-13-generic
}
menuentry "Trisquel GNU/Linux, with Linux-Libre 2.6.38-13-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux /boot/vmlinuz-2.6.38-13-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro single nomodeset
    initrd /boot/initrd.img-2.6.38-13-generic
}
menuentry "Trisquel GNU/Linux, with Linux-Libre 2.6.35-28-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Trisquel GNU/Linux, with Linux-Libre 2.6.35-28-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro single nomodeset
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Linux Mint 12 32-bit, 3.0.0-19-generic-pae (/dev/sda6) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux /boot/vmlinuz-3.0.0-19-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-19-generic-pae
}
menuentry "Linux Mint 12 32-bit, 3.0.0-19-generic-pae (/dev/sda6) -- recovery mode (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux /boot/vmlinuz-3.0.0-19-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-19-generic-pae
}
menuentry "Linux Mint 12 32-bit, 2.6.38-15-generic-pae (/dev/sda6) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux /boot/vmlinuz-2.6.38-15-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-15-generic-pae
}
menuentry "Linux Mint 12 32-bit, 2.6.38-15-generic-pae (/dev/sda6) -- recovery mode (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux /boot/vmlinuz-2.6.38-15-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro recovery nomodeset
    initrd /boot/initrd.img-2.6.38-15-generic-pae
}
menuentry "Linux Mint 12 32-bit, 2.6.38-8-generic-pae (/dev/sda6) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Linux Mint 12 32-bit, 2.6.38-8-generic-pae (/dev/sda6) -- recovery mode (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro recovery nomodeset
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Fedora (2.6.38.6-26.rc1.fc15.x86_64) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 01966a49-f488-4171-b153-6f29725eae24
    linux /boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=UUID=01966a49-f488-4171-b153-6f29725eae24 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=uk rhgb quiet
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
}
menuentry "Desktop -- openSUSE 11.4 - 2.6.37.6-0.7 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1aef5c91-3a2e-4da1-939d-72ac0eb429f2
    linux /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part8 resume=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part1 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.37.6-0.7-desktop
}
menuentry "Failsafe -- openSUSE 11.4 - 2.6.37.6-0.7 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1aef5c91-3a2e-4da1-939d-72ac0eb429f2
    linux /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part8 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x317
    initrd /boot/initrd-2.6.37.6-0.7-desktop
}
menuentry "linux (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet vmalloc=256M acpi=on resume=UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5 splash=silent vga=788
    initrd (hd0,8)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet vmalloc=256M acpi=on resume=UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5
    initrd (hd0,8)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet failsafe vmalloc=256M acpi=on
    initrd (hd0,8)/boot/initrd.img
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 /               ext4    errors=remount-ro 0       1
# /fedora was on /dev/sda7 during installation
UUID=55e37d2e-248d-489b-99c1-f611320dd608 /fedora         ext4    defaults        0       2
# /mint was on /dev/sda6 during installation
UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca /mint           ext4    defaults        0       2
# /other2 was on /dev/sda12 during installation
UUID=c24d3e2d-5215-4476-8672-d7dee8cf1d6c /other2         ext4    defaults        0       2
# /pclinux was on /dev/sda9 during installation
UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 /pclinux        ext4    defaults        0       2
/dev/sda1       none            swap    sw              0       0
/dev/sda7 /fedora ext4 defaults,noatime 0 2
/dev/sda14 /home/joe/files ext4 defaults,noatime 0 2
/dev/sda11 /trisquel ext4 defaults,noatime 0 2
/dev/sda10 /kubuntu ext4 defaults,noatime 0 2
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  12.228885651 = 13.130665984   boot/grub/core.img                             1
  18.775917053 = 20.160487424   boot/grub/grub.cfg                             1
  11.589294434 = 12.443910144   boot/grub/menu.lst                             1
  14.836883545 = 15.930982400   boot/initrd.img-3.2.0-24-generic              22
  21.451171875 = 23.033020416   boot/initrd.img-3.2.0-24-generic-pae          11
   9.748672485 = 10.467557376   boot/vmlinuz-3.2.0-24-generic                  1
  10.816234589 = 11.613843456   boot/vmlinuz-3.2.0-24-generic-pae              4
  21.451171875 = 23.033020416   initrd.img                                    11
  14.836883545 = 15.930982400   initrd.img.old                                22
  10.816234589 = 11.613843456   vmlinuz                                        4
   9.748672485 = 10.467557376   vmlinuz.old                                    1

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
search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
if background_color 0,0,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

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
menuentry 'Linux Mint 12 32-bit, 3.0.0-19-generic-pae (/dev/sda6)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux    /boot/vmlinuz-3.0.0-19-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-19-generic-pae
}
menuentry 'Linux Mint 12 32-bit, 3.0.0-19-generic-pae (/dev/sda6) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    echo    'Loading Linux 3.0.0-19-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-19-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-19-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Linux Mint 12 32-bit, 2.6.38-15-generic-pae (/dev/sda6)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux    /boot/vmlinuz-2.6.38-15-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-15-generic-pae
}
menuentry 'Linux Mint 12 32-bit, 2.6.38-15-generic-pae (/dev/sda6) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    echo    'Loading Linux 2.6.38-15-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-15-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-15-generic-pae
}
menuentry 'Linux Mint 12 32-bit, 2.6.38-8-generic-pae (/dev/sda6)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Linux Mint 12 32-bit, 2.6.38-8-generic-pae (/dev/sda6) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=3a997e4d-3835-4afc-9eac-f177731407c9 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=3a997e4d-3835-4afc-9eac-f177731407c9 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Trisquel GNU/Linux, with Linux-Libre 3.0.0-19-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux /boot/vmlinuz-3.0.0-19-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-19-generic
}
menuentry "Trisquel GNU/Linux, with Linux-Libre 3.0.0-19-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux /boot/vmlinuz-3.0.0-19-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-19-generic
}
menuentry "Trisquel GNU/Linux, with Linux-Libre 2.6.38-13-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux /boot/vmlinuz-2.6.38-13-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-13-generic
}
menuentry "Trisquel GNU/Linux, with Linux-Libre 2.6.38-13-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux /boot/vmlinuz-2.6.38-13-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro single nomodeset
    initrd /boot/initrd.img-2.6.38-13-generic
}
menuentry "Trisquel GNU/Linux, with Linux-Libre 2.6.35-28-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Trisquel GNU/Linux, with Linux-Libre 2.6.35-28-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro single nomodeset
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Haiku (on /dev/sda13)" --class windows --class os {
    insmod part_msdos
    insmod befs
    set root='(hd0,msdos13)'
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.2.0-24-generic-pae (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-24-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux /boot/vmlinuz-3.2.0-24-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-24-generic
}
menuentry "Ubuntu, with Linux 3.2.0-24-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux /boot/vmlinuz-3.2.0-24-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-24-generic
}
menuentry "Fedora (2.6.38.6-26.rc1.fc15.x86_64) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 01966a49-f488-4171-b153-6f29725eae24
    linux /boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=UUID=01966a49-f488-4171-b153-6f29725eae24 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=uk rhgb quiet
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
}
menuentry "Desktop -- openSUSE 11.4 - 2.6.37.6-0.7 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1aef5c91-3a2e-4da1-939d-72ac0eb429f2
    linux /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part8 resume=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part1 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.37.6-0.7-desktop
}
menuentry "Failsafe -- openSUSE 11.4 - 2.6.37.6-0.7 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1aef5c91-3a2e-4da1-939d-72ac0eb429f2
    linux /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part8 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x317
    initrd /boot/initrd-2.6.37.6-0.7-desktop
}
menuentry "linux (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet vmalloc=256M acpi=on resume=UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5 splash=silent vga=788
    initrd (hd0,8)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet vmalloc=256M acpi=on resume=UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5
    initrd (hd0,8)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet failsafe vmalloc=256M acpi=on
    initrd (hd0,8)/boot/initrd.img
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca /               ext4    errors=remount-ro 0       1
# /home/files was on /dev/sda14 during installation
UUID=c4813164-1ffb-485a-aab1-5039d8b51510 /home/files     ext4    defaults        0       2
# /other1 was on /dev/sda11 during installation
UUID=6d63e63f-dcdc-46dd-b864-74a7271e7667 /other1         ext4    defaults        0       2
# /other2 was on /dev/sda12 during installation
UUID=c24d3e2d-5215-4476-8672-d7dee8cf1d6c /other2         ext4    defaults        0       2
# /pclinux was on /dev/sda9 during installation
UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 /pclinux        ext4    defaults        0       2
# /ubuntu was on /dev/sda5 during installation
UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 /ubuntu         ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5 none            swap    sw              0       0
/dev/sda7 /fedora ext4 defaults,noatime 0 2
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  24.495605469 = 26.301956096   boot/grub/core.img                             1
  36.807994843 = 39.522283520   boot/grub/grub.cfg                             1
  36.979240417 = 39.706157056   boot/initrd.img-2.6.38-15-generic-pae          2
  24.813476562 = 26.643267584   boot/initrd.img-2.6.38-8-generic-pae           2
  33.738132477 = 36.226043904   boot/initrd.img-3.0.0-19-generic-pae           2
  33.567829132 = 36.043182080   boot/vmlinuz-2.6.38-15-generic-pae             1
  23.083435059 = 24.785649664   boot/vmlinuz-2.6.38-8-generic-pae              1
  36.903881073 = 39.625240576   boot/vmlinuz-3.0.0-19-generic-pae              1
  36.979240417 = 39.706157056   initrd.img.old                                 2
  36.903881073 = 39.625240576   vmlinuz                                        1
  33.567829132 = 36.043182080   vmlinuz.old                                    1

========================== sda7/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,6)
#          kernel /boot/vmlinuz-version ro root=/dev/sda7
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,6)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.6-26.rc1.fc15.x86_64)
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=UUID=01966a49-f488-4171-b153-6f29725eae24 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=uk rhgb quiet
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
title Mint
    rootnoverify (hd0,5)
    chainloader +1
title Ubuntu
    rootnoverify (hd0,4)
    chainloader +1
title PcLinuxOS
    rootnoverify (hd0,8)
    chainloader +1
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Mon Oct 24 16:02:56 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=01966a49-f488-4171-b153-6f29725eae24 /                       ext4    defaults        1 1
UUID=c4813164-1ffb-485a-aab1-5039d8b51510 /home/files             ext4    defaults        1 2
UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca /mint                   ext4    defaults        1 2
UUID=6d63e63f-dcdc-46dd-b864-74a7271e7667 /other1                 ext4    defaults        1 2
UUID=c24d3e2d-5215-4476-8672-d7dee8cf1d6c /other2                 ext4    defaults        1 2
UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 /pclinux                ext4    defaults        1 2
UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 /ubuntu                 ext4    defaults        1 2
UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  37.389106750 = 40.146247680   boot/grub/grub.conf                            1
  37.389106750 = 40.146247680   boot/grub/menu.lst                             1
  37.393917084 = 40.151412736   boot/grub/stage2                               1
  39.509452820 = 42.422951936   boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img  2
  38.399440765 = 41.231085568   boot/initrd-plymouth.img                       1
  38.407909393 = 41.240178688   boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64       1

=========================== sda8/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Modified by YaST2. Last modification on Tue Oct 25 16:40:19 BST 2011
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,7)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.4 - 2.6.37.6-0.7
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part8 resume=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part1 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.37.6-0.7-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.4 - 2.6.37.6-0.7
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part8 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x317
    initrd /boot/initrd-2.6.37.6-0.7-desktop
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part1 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part8 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part7 /fedora              ext4       defaults              1 2
/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part14 /home/files          ext4       defaults              1 2
/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part10 /kubuntu             ext4       defaults              1 2
/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part6 /mint                ext4       defaults              1 2
/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part11 /other1              ext4       defaults              1 2
/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part12 /other2              ext4       defaults              1 2
/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part9 /pclinux             ext4       defaults              1 2
/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part5 /ubuntu              ext4       defaults              1 2
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  60.280281067 = 64.725458944   boot/grub/menu.lst                             1
  60.581905365 = 65.049325568   boot/grub/stage2                               1
  53.585918427 = 57.537441792   boot/initrd                                    1
  53.585918427 = 57.537441792   boot/initrd-2.6.37.6-0.7-desktop               1
  60.676025391 = 65.150386176   boot/vmlinuz                                   1
  60.676025391 = 65.150386176   boot/vmlinuz-2.6.37.6-0.7-desktop              1

=========================== sda9/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
timeout 5
color black/cyan yellow/cyan
gfxmenu (hd0,8)/boot/gfxmenu
default 0

title linux
kernel (hd0,8)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6  quiet vmalloc=256M acpi=on resume=UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5 splash=silent vga=788
initrd (hd0,8)/boot/initrd.img

title linux-nonfb
kernel (hd0,8)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6  quiet vmalloc=256M acpi=on resume=UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5
initrd (hd0,8)/boot/initrd.img

title failsafe
kernel (hd0,8)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6  quiet failsafe vmalloc=256M acpi=on
initrd (hd0,8)/boot/initrd.img
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# Entry for /dev/sda9 :
UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 / ext4 defaults 1 1
# Entry for /dev/sda7 :
UUID=01966a49-f488-4171-b153-6f29725eae24 /fedora ext4 defaults 1 2
# Entry for /dev/sda14 :
UUID=c4813164-1ffb-485a-aab1-5039d8b51510 /home/files ext4 defaults 1 2
# Entry for /dev/sda6 :
UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca /mint ext4 defaults 1 2
none /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 /ubuntu ext4 defaults 1 2
# Entry for /dev/sda1 :
UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5 swap swap defaults 0 0
none /dev/pts devpts defaults 0 0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  71.183753967 = 76.432973824   boot/grub/menu.lst                             1
  72.161075592 = 77.482364928   boot/grub/stage2                               1
  67.776660919 = 72.774635520   boot/initrd-2.6.38.8-pclos1.bfs.img            1
  67.776660919 = 72.774635520   boot/initrd.img                                1
  71.186626434 = 76.436058112   boot/vmlinuz                                   1
  71.186626434 = 76.436058112   boot/vmlinuz-2.6.38.8-pclos1.bfs               1

========================== sda10/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos10)'
  search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
if background_color 0,71,115; then
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
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3a997e4d-3835-4afc-9eac-f177731407c9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3a997e4d-3835-4afc-9eac-f177731407c9 ro recovery nomodeset 
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
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-12-generic-pae (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Linux Mint 11, 2.6.38-8-generic-pae (/dev/sda6) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Linux Mint 11, 2.6.38-8-generic-pae (/dev/sda6) -- recovery mode (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro single
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Fedora (2.6.38.6-26.rc1.fc15.x86_64) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 01966a49-f488-4171-b153-6f29725eae24
    linux /boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=UUID=01966a49-f488-4171-b153-6f29725eae24 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=uk rhgb quiet
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
}
menuentry "Desktop -- openSUSE 11.4 - 2.6.37.6-0.7 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1aef5c91-3a2e-4da1-939d-72ac0eb429f2
    linux /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part8 resume=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part1 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.37.6-0.7-desktop
}
menuentry "Failsafe -- openSUSE 11.4 - 2.6.37.6-0.7 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1aef5c91-3a2e-4da1-939d-72ac0eb429f2
    linux /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part8 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x317
    initrd /boot/initrd-2.6.37.6-0.7-desktop
}
menuentry "linux (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet vmalloc=256M acpi=on resume=UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5 splash=silent vga=788
    initrd (hd0,8)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet vmalloc=256M acpi=on resume=UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5
    initrd (hd0,8)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet failsafe vmalloc=256M acpi=on
    initrd (hd0,8)/boot/initrd.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

# Haiku on /dev/sda13
menuentry "Haiku Alpha" {
    set root=(hd0,7)
    chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=3a997e4d-3835-4afc-9eac-f177731407c9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5 none            swap    sw              0       0
/dev/sda6 /media/mint ext4 defaults,noatime 0 2
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

  84.901866913 = 91.162685440   boot/grub/core.img                             1
  86.454113007 = 92.829396992   boot/grub/grub.cfg                             1
  83.786132812 = 89.964675072   boot/initrd.img-3.0.0-12-generic               3
  86.386428833 = 92.756721664   boot/vmlinuz-3.0.0-12-generic                  1
  83.786132812 = 89.964675072   initrd.img                                     3
  86.386428833 = 92.756721664   vmlinuz                                        1

========================== sda11/boot/grub/grub.cfg: ===========================

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
set default="5"
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
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos11)'
  search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/01_PASSWORD ###
set superusers=grub
password grub 14728
### END /etc/grub.d/01_PASSWORD ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_trisquel_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
insmod png
if background_image /usr/share/backgrounds/trisquel-grub.png ; then
  set color_normal=white/black
  set color_highlight=yellow/white
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/06_trisquel_theme ###

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
menuentry 'Trisquel GNU/Linux, with Linux-Libre 3.0.0-19-generic' --class trisquel --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux    /boot/vmlinuz-3.0.0-19-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-19-generic
}
menuentry 'Trisquel GNU/Linux, with Linux-Libre 3.0.0-19-generic (recovery mode)' --class trisquel --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    echo    'Loading Linux 3.0.0-19-generic ...'
    linux    /boot/vmlinuz-3.0.0-19-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro single nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-19-generic
}
submenu "Previous Linux versions" {
menuentry 'Trisquel GNU/Linux, with Linux-Libre 2.6.38-13-generic' --class trisquel --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-13-generic
}
menuentry 'Trisquel GNU/Linux, with Linux-Libre 2.6.38-13-generic (recovery mode)' --class trisquel --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    echo    'Loading Linux 2.6.38-13-generic ...'
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro single nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-13-generic
}
menuentry 'Trisquel GNU/Linux, with Linux-Libre 2.6.35-28-generic' --class trisquel --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Trisquel GNU/Linux, with Linux-Libre 2.6.35-28-generic (recovery mode)' --class trisquel --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 175b7ad6-ca78-447b-b00b-164ed7bad9e3
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 ro single nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=3a997e4d-3835-4afc-9eac-f177731407c9 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 3a997e4d-3835-4afc-9eac-f177731407c9
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=3a997e4d-3835-4afc-9eac-f177731407c9 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.2.0-24-generic-pae (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-24-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux /boot/vmlinuz-3.2.0-24-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-24-generic
}
menuentry "Ubuntu, with Linux 3.2.0-24-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d2aec80-c363-49ce-aeca-83bbfd436499
    linux /boot/vmlinuz-3.2.0-24-generic root=UUID=7d2aec80-c363-49ce-aeca-83bbfd436499 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-24-generic
}
menuentry "Linux Mint 11, 2.6.38-8-generic-pae (/dev/sda6) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Linux Mint 11, 2.6.38-8-generic-pae (/dev/sda6) -- recovery mode (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 7cb5ec52-7a5c-40c9-983b-ead92e812fca
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=7cb5ec52-7a5c-40c9-983b-ead92e812fca ro single
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Fedora (2.6.38.6-26.rc1.fc15.x86_64) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 01966a49-f488-4171-b153-6f29725eae24
    linux /boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=UUID=01966a49-f488-4171-b153-6f29725eae24 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=uk rhgb quiet
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
}
menuentry "Desktop -- openSUSE 11.4 - 2.6.37.6-0.7 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1aef5c91-3a2e-4da1-939d-72ac0eb429f2
    linux /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part8 resume=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part1 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.37.6-0.7-desktop
}
menuentry "Failsafe -- openSUSE 11.4 - 2.6.37.6-0.7 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 1aef5c91-3a2e-4da1-939d-72ac0eb429f2
    linux /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-ST9500325AS_6VEMJCHW-part8 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x317
    initrd /boot/initrd-2.6.37.6-0.7-desktop
}
menuentry "linux (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet vmalloc=256M acpi=on resume=UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5 splash=silent vga=788
    initrd (hd0,8)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet vmalloc=256M acpi=on resume=UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5
    initrd (hd0,8)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root ab57dbf3-3166-470f-bdcf-7313114f59f6
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=ab57dbf3-3166-470f-bdcf-7313114f59f6 quiet failsafe vmalloc=256M acpi=on
    initrd (hd0,8)/boot/initrd.img
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

=============================== sda11/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=175b7ad6-ca78-447b-b00b-164ed7bad9e3 /               ext4    errors=remount-ro 0       1
# /home/files was on /dev/sda14 during installation
UUID=c4813164-1ffb-485a-aab1-5039d8b51510 /home/files     ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=0e8a45b8-c53d-4dee-9ed4-438b9c9a83c5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda11: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 107.381282806 = 115.299774464  boot/grub/core.img                             1
  99.091808319 = 106.399019008  boot/grub/grub.cfg                             1
 101.437500000 = 108.917686272  boot/initrd.img-2.6.35-28-generic              2
  97.601562500 = 104.798879744  boot/initrd.img-2.6.38-13-generic              3
 107.499588013 = 115.426803712  boot/initrd.img-3.0.0-19-generic               2
  98.991355896 = 106.291159040  boot/vmlinuz-2.6.35-28-generic                 1
  98.484680176 = 105.747120128  boot/vmlinuz-2.6.38-13-generic                 1
 104.687942505 = 112.407822336  boot/vmlinuz-3.0.0-19-generic                  1
  97.601562500 = 104.798879744  initrd.img.old                                 3
 104.687942505 = 112.407822336  vmlinuz                                        1
  98.484680176 = 105.747120128  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda13

00000000  0e 1f 0e 07 0e 17 bc 00  7c fa fc 88 16 00 80 b4  |........|.......|
00000010  41 bb aa 55 cd 13 72 10  81 fb 55 aa 75 0a f6 c1  |A..U..r...U.u...|
00000020  01 74 05 c6 06 98 7d 01  66 31 c0 40 66 8d 2e 00  |.t....}.f1.@f...|
00000030  7e e8 28 00 66 81 3e 20  7e 31 53 46 42 74 05 be  |~.(.f.> ~1SFBt..|
00000040  a4 7d eb 03 e9 9c 02 e8  06 00 b4 00 cd 16 cd 19  |.}..............|
00000050  ac 08 c0 74 06 b4 0e cd  10 eb f5 c3 bf 01 00 66  |...t...........f|
00000060  60 66 03 06 fa 7d 8a 16  00 80 80 3e 98 7d 00 74  |`f...}.....>.}.t|
00000070  28 c7 06 04 80 10 00 89  3e 06 80 66 89 2e 08 80  |(.......>..f....|
00000080  66 a3 0c 80 66 31 c0 66  a3 10 80 be 04 80 b4 42  |f...f1.f.......B|
00000090  cd 13 73 50 be 99 7d eb  ae 66 50 b4 08 cd 13 72  |..sP..}..fP....r|
000000a0  f3 66 58 86 d6 30 f6 52  66 31 d2 66 83 e1 3f 66  |.fX..0.Rf1.f..?f|
000000b0  f7 f1 fe c2 59 52 31 d2  30 ed 41 f7 f1 08 d6 89  |....YR1.0.A.....|
000000c0  c1 86 cd c0 c9 02 5a 08  d1 66 89 e8 66 c1 e8 10  |......Z..f..f...|
000000d0  06 50 07 89 eb 89 f8 8a  16 00 80 b4 02 cd 13 07  |.P..............|
000000e0  39 f8 75 b0 66 61 c3 31  c0 66 60 87 26 96 7d 66  |9.u.fa.1.f`.&.}f|
000000f0  61 66 21 c9 7f 38 fe ca  7d 1d 4b 7c 4d 66 31 f6  |af!..8..}.K|Mf1.|
00000100  8d 36 34 82 66 60 66 97  66 89 f5 e8 4e ff 66 61  |.64.f`f.f...N.fa|
00000110  66 47 66 31 d2 b2 40 e8  92 02 66 21 c0 74 db 66  |fGf1..@...f!.t.f|
00000120  91 66 0f b7 44 06 e8 9a  02 66 91 83 c6 08 66 83  |.f..D....f....f.|
00000130  e9 02 66 57 bf 02 00 e8  25 ff 66 05 02 00 00 00  |..fW....%.f.....|
00000140  8b 3e 96 7d c6 45 1c 01  66 5f 66 60 87 26 96 7d  |.>.}.E..f_f`.&.}|
00000150  66 61 c3 66 60 87 26 96  7d 66 61 31 db 8d 36 ec  |fa.f`.&.}fa1..6.|
00000160  80 66 83 3c 00 75 07 66  83 7c 04 00 74 17 8d 36  |.f.<.u.f.|..t..6|
00000170  e4 80 e8 37 02 66 21 c0  74 0b 66 97 66 0f b7 44  |...7.f!.t.f.f..D|
00000180  06 e8 3f 02 93 66 31 c9  b2 0c 8d 36 7c 80 66 31  |..?..f1....6|.f1|
00000190  ed bd 34 84 eb b4 e0 5b  00 72 65 61 64 20 65 72  |..4....[.read er|
000001a0  72 6f 72 00 62 61 64 20  73 75 70 65 72 62 6c 6f  |ror.bad superblo|
000001b0  63 6b 00 6e 6f 74 20 61  20 64 69 72 65 63 74 6f  |ck.not a directo|
000001c0  72 79 00 62 61 64 20 69  6e 6f 64 65 00 68 61 69  |ry.bad inode.hai|
000001d0  6b 75 5f 6c 6f 61 64 65  72 20 6e 6f 74 20 66 6f  |ku_loader not fo|
000001e0  75 6e 64 00 06 73 79 73  74 65 6d 0c 68 61 69 6b  |und..system.haik|
000001f0  75 5f 6c 6f 61 64 65 72  00 00 00 48 90 35 55 aa  |u_loader...H.5U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```

Sorry for how absurdly long it is.

---

### Post by oldfred on 2012-05-09
You can just reinstall grub from Ubuntu as posted above.

Is the issue when you run updates in Mint for example that it then overwrites your Ubuntu boot?

Grub remembers which drive it installed to and on a major update may reinstall to the MBR.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

I think if you unchoose all drives then it will not reinstall.
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by joetait on 2012-05-09
The 
sudo grub-install /dev/sda
line worked, thanks very much :)

The issue in very layman terms is that when I upgrade most distros I have, the grub it uses (config files et al) is the one from the updated distro. It doesn't affect the stuff on the Ubuntu partition at all, but what the computer chooses to load at boot. I am not sure if that is what you mean by overwriting Ubuntu boot (though I guess it is).

And thank you very much for the extra info too

---

