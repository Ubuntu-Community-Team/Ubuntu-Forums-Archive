---
title: "no internet home page"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by kerrry on 2012-05-12
I have installed ubuntu 12.04 on lenovo notebook, everything normal, net connection is esablished but can't find home page server not found, also computer will not boot without usb. What have I done?:sad:

---

### Post by wilee-nilee on 2012-05-12
Sounds like grub, the bootloader, was put in the usb's mbr.

You can run a script to check that, and post it, here is a link, extract it to the desktop and run the command and look at the results.txt and post it.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

The other error I'm not sure.

---

### Post by kerrry on 2012-05-12
kerry@kerry-Lenovo-IdeaPad-S10-2:~$ sudo bash ~/Desktop/bootinfoscript-061.tar.gz  
 [sudo] password for kerry:  
 /home/kerry/Desktop/bootinfoscript-061.tar.gz: /home/kerry/Desktop/bootinfoscript-061.tar.gz: cannot execute binary file  
 kerry@kerry-Lenovo-IdeaPad-S10-2:~$

---

### Post by wilee-nilee on 2012-05-12
> **kerrry said:**
> kerry@kerry-Lenovo-IdeaPad-S10-2:~$ sudo bash ~/Desktop/bootinfoscript-061.tar.gz  
 [sudo] password for kerry:  
 /home/kerry/Desktop/bootinfoscript-061.tar.gz: /home/kerry/Desktop/bootinfoscript-061.tar.gz: cannot execute binary file  
 kerry@kerry-Lenovo-IdeaPad-S10-2:~$

You have to extract the tar to the desktop just click it and it will open a gui to extract with. Extract to the desktop then run the exact command I posted.

---

### Post by kerrry on 2012-05-12
kerry@kerry-Lenovo-IdeaPad-S10-2:~$ sudo bash ~/Desktop/bootinfoscript-061.tar.gz.zip  
 /home/kerry/Desktop/bootinfoscript-061.tar.gz.zip: line 1: $'PK\003\004': command not found  
 /home/kerry/Desktop/bootinfoscript-061.tar.gz.zip: line 2: kw&#65533;ƒ&#65533;: No such file or directory  
 /home/kerry/Desktop/bootinfoscript-061.tar.gz.zip: line 3: syntax error near unexpected token `$'\320\204\361\260\323\376\320\354\312''  
 &#65533;9&#65533;&#65533;#x|g&#65533;&#65533;r#j@&#65533;&#65533;X=&#65533;#&#65533;&#65533;&#65533;VU&#65533;&#65533;x[FONT=Lohit Hindi]&#1465;&#65533;[/FONT]w&#65533;&#65533;$#&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;[FONT=Lohit Hindi]&#1882;&#65533;[/FONT]m{&#65533;5&#65533;[FONT=Lohit Hindi]&#1881;[/FONT]c&#65533;&#65533;o&#65533;&#65533;&#65533;#|~z&#65533;#&#65533;k?&#65533;=&#65533;##&#65533;y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;j;&#65533;k&#65533;I~|&#65533;&#65533;#&#446;1f|&#65533;O&#65533;&#65533;q&#65533;&#65533;&#65533;#&#65533;&#65533;}[&#65533;#Vu&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;##&#65533;#&#65533;&#65533;Z&#65533;&#65533;#&#65533;&#65533;&#65533;&#65533;&#65533;=i5&#65533;&#65533;F&#65533;&#410;k&#65533;0&#65533;&#65533;A&#65533;#:&#65533;&#65533;&#65533;xr&#65533;#ON#&#65533;^g&#65533;(&#1028;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;)&#1076;&#65533;&#159;&#65533;#{#<&#65533;&#65533;&#65533;Xz&#65533;8+&#65533;~&#65533;&#65533;"&#256;K&#65533;1fK&#65533;&#65533;#w&#65533;&#65533;pk&#65533;M&#65533;Yk5#x(#&#65533;q&#65533;c&#65533;&#65533;&#65533;rs&#65533;Y&#65533;#Q&#65533;&#65533;##x&#65533;&#65533;&#65533;&#7814;m1&#65533;eK&#65533;&#65533;&#65533;=[&#65533;&#65533;<&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;s6[j&#898;&#65533;&#65533;g3&#890;gk&#65533;&#65533;0&#65533;&#65533;z&#65533;a#&#1410;il#+%&#65533;0&#65533;[#([FONT=Lohit Hindi]&#1502;[/FONT]{#&#65533;&#65533;0Ag&#65533;&#65533;&#65533;3C#&#65533;L&#65533;g&#65533;&#65533;[&#65533;&#65533;!&#953;ar&#65533;#&#65533;%g&#65533;H&#65533;PJ&#65533;(&#65533;P&#65533;&#65533;&#65533; 
 q#&#65533;&#65533;&#154;&#65533;&#65533;2[[FONT=Lohit Hindi]&#1658;[/FONT]1&#65533;oN      &#65533;&#65533;&#65533;&#65533;#&#65533;&#65533;&#65533;=&#65533;p[FONT=Lohit Hindi]&#1475;[/FONT]mAXe#43}#&#65533;	&#65533;MceHL8]&#65533; 
               ]&#65533;S&#65533;p&#65533;e&#65533;#&#65533;`&#65533;{&#65533;&#65533;b&#65533;&#65533;[8 
                                   VU&#65533;###6&#65533;D0#,&#65533;&#65533;##J##&#65533;#&#65533;&#65533;I&#65533;#&#65533;&#65533;&#65533;^%#e&#65533;&#65533;¹&#65533;X&#65533;&#65533;&#65533;L&#65533;#^#85&#65533;r&#65533;`}&#65533;&#65533;#&#65533;#c&#65533;&#65533;&#65533;kly#l&#65533;&#65533;vhui[FONT=Lohit Hindi]&#1450;[/FONT]OS&#65533;&#65533;K>o&#65533;&#65533;&#65533;t|&#65533;#&#65533;Yg&#65533;.&#65533;&#65533;&#65533;V&#65533;&#340;&#65533;&#65533;2&#65533;&#65533;&#65533;&#65533;&#65533;c##&#65533;&#65533;&#65533;&#65533;##&#65533;&#65533;f&#65533;#&#65533;&#65533;&#65533;o&#65533;Y&#65533;o#&#65533;&#65533;h&#65533;#C	&#65533;&#1275;&#65533;v&#65533;&#65533;&#65533;&#65533;&#65533;t/[&#65533;&#65533;#;&#65533;&#65533;&#65533;&#65533;&#65533;u;`I#&#65533;x@h%&#65533;N{&#65533; {&#65533;&#65533;&#65533;9<6&#65533;&#65533;&#65533;c9&#65533;&#65533;&#65533;3&#65533;#&#65533;S@&#65533;d#&#65533;&#65533;&#65533;sr&#65533;m&#65533;&#65533;&#65533;&#65533;b0j#1-&#65533;&#65533;&#65533;O&#65533;&#65533;&#65533;&#65533;k&#65533;&#65533;*`&#65533;6&#65533;&#65533;lt&#65533;&#65533;v	%#l^&#130;&#65533;D&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;sv>f&#65533;&#65533;n 
                                                             &#65533;#;n#&#65533;&#65533;&#65533;n[&#65533;&#65533;u&#65533;t&#65533;&#65533;^&#65533;&#65533;I#&#65533;C&#65533; &#65533;&#65533;:oS'&#65533;o&#65533;'cp8&#65533;&#65533;&#65533;A<&#65533;&#65533;2,~8&#65533;\uF&#65533;2k;#&#65533;S&#65533;&#65533;&#65533;0"&#65533;a[FONT=WenQuanYi Micro Hei][SIZE=2]&#40992;[/SIZE][/FONT]#&#65533;~[&#65533; 
   &#65533;&#65533;&#65533;Q;"&#65533;&#65533;nv#&#65533;HlJ?1&#65533;	!&#65533;B&#65533;y&#65533;&#65533;[FONT=Lohit Hindi]&#1983;&#65533;[/FONT]#&#65533;#,<X&#65533;[n&#65533;`#&#65533;&#65533;#_&#65533;&#65533; 
                                                    &#65533;M&#65533;&#65533;v&#65533;&#65533;&#65533;J&#65533;&#65533;X&#1119;&#65533;&#65533;&#65533;&#65533;m&#65533;_&#65533;&#65533;&#65533;,J	&#65533;`&#65533;&#65533;&#65533;&#65533;	&#65533;L3&#65533;&#65533;&#65533;&#65533; 
                v&#65533;c&#65533;?q&#65533;[FONT=WenQuanYi Micro Hei][SIZE=2]&#32139;&#65533;[/SIZE][/FONT]W&#65533;b^b&#65533;y&#65533;&#65533;j&#1397;}g&#385;&#65533;W-&#65533;U[FONT=Lohit Hindi]&#1486;&#65533;&#65533;[/FONT]&#429;N#9A&#65533;/&#65533;#}&#65533;&#65533;p&#65533;Y`&#65533;5&#65533;n6"&#65533;[FONT=Lohit Hindi]&#1662;&#65533;[/FONT]i&#65533;Y#&#65533;&#65533;&#65533;nT[FONT=Lohit Hindi]&#1893;&#65533;&#65533;[/FONT]tu&#65533;\&#65533;&#65533;#?&#65533;&#65533;&#65533;&#65533;_j&#65533;&#65533;&#65533;#Z&#65533;6&#65533;XE&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;[FONT=Lohit Hindi]&#1845;[/FONT]6&#65533;&#65533;P&#65533;#&#65533;#&#65533;&#65533;&#65533;#>{` &#65533;|v&#65533;  
                                                        &#65533;&#965;pa&#65533;&#65533;&#65533;#En  
                                                                  &#65533;#&#65533;#!^&#65533;&#65533;&#640;X&#65533;Y;#&#65533;&#65533;&#65533;<&#65533;&#65533;;&#65533;&#65533;&#596;&#65533;&#65533;&#65533;&#65533;|"S#&#65533;}bu#g&#65533;&#65533;p>[[FONT=Lohit Hindi]&#1708;&#65533;[/FONT]#!fq&#65533;S&#65533;#&#65533;#&#65533;*&#65533;w&#65533;#&#65533;	&#65533;#&#65533;n&#65533;z~n&#65533;&#65533; 
                                                           wmj&#65533;#/&#65533;k&#65533;&#65533;;%%&#65533;&#65533;)&#65533;a&#65533;&#65533;&#65533;v&#65533;&#65533;&#65533;K&#65533;&#65533;<&#65533;/&#65533;&#65533;#R1&#65533;<&#65533;&#65533;&#65533;#v&#65533;&#65533;^&#65533;s&#65533;[FONT=Lohit Hindi]&#1829;&#65533;[/FONT]-&#65533;&#65533;&#65533;&#65533;s&#65533;&#65533;al&#65533;[q&#65533;&#65533;&#65533;}&#65533;##(&#65533;#=&#65533;&#65533;&#65533;&#65533;G&#65533;+&#65533;&#65533;k&#65533;&#65533;#&#65533;&#65533;&#65533;&#65533;&#65533; 
                                                                        &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;##P&#65533;#,&#65533;

---

### Post by kerrry on 2012-05-12
Maybe because I used a usb to install, the whole ubuntu is still on the stick only therefore so would the net stuff, When I intsalled I told it to take over the whole system which it has but I cant seem to save it to the hard drive I still need to use usb to load ubuntu or anything now. How do I get Ubuntu onto hard drive so it boots normally without usb?

---

### Post by wilee-nilee on 2012-05-12
> **kerrry said:**
> Maybe because I used a usb to install, the whole ubuntu is still on the stick only therefore so would the net stuff, When I intsalled I told it to take over the whole system which it has but I cant seem to save it to the hard drive I still need to use usb to load ubuntu or anything now. How do I get Ubuntu onto hard drive so it boots normally without usb?

This command is wrong.

```
sudo bash ~/Desktop/bootinfoscript-061.tar.gz.zip  
```It should be 

```
sudo bash ~/Desktop/bootinfoscript
```After you  have extracted the tar that you have downloaded by clicking on it then choosing extract to the desktop.

---

### Post by kerrry on 2012-05-13
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 2bb1458c-04e8-4018-a32a-5b61e35f9831 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 1449880 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   308,408,319   308,406,272  83 Linux
/dev/sda2         308,410,366   312,580,095     4,169,730   5 Extended
/dev/sda5         308,410,368   312,580,095     4,169,728  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,826,383     7,826,322   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        2bb1458c-04e8-4018-a32a-5b61e35f9831   ext4       
/dev/sda5        0d2811d7-f7c6-4526-9b52-162404b78537   swap       
/dev/sdb1        E165-17B4                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/E165-17B4         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 2bb1458c-04e8-4018-a32a-5b61e35f9831
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 2bb1458c-04e8-4018-a32a-5b61e35f9831
  set locale_dir=($root)/boot/grub/locale
  set lang=en_AU
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 2bb1458c-04e8-4018-a32a-5b61e35f9831
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=2bb1458c-04e8-4018-a32a-5b61e35f9831 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 2bb1458c-04e8-4018-a32a-5b61e35f9831
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=2bb1458c-04e8-4018-a32a-5b61e35f9831 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 2bb1458c-04e8-4018-a32a-5b61e35f9831
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 2bb1458c-04e8-4018-a32a-5b61e35f9831
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2bb1458c-04e8-4018-a32a-5b61e35f9831 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0d2811d7-f7c6-4526-9b52-162404b78537 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           2
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  15 f5 0f ef 77 c7 c2 0a  b3 b1 2d d7 02 f5 f9 02  |....w.....-.....|
00000010  62 b6 e3 3e d3 03 8c 0e  9e 0b 0c 63 a9 67 fc f4  |b..>.......c.g..|
00000020  e8 a2 3e 77 01 46 3f b9  c1 91 4a 17 56 3a 0b c2  |..>w.F?...J.V:..|
00000030  0a 7a 8b 19 e6 c4 45 d7  46 41 45 26 3b 0e fc 72  |.z....E.FAE&;..r|
00000040  ed e5 f5 05 98 eb 93 7b  60 7e 80 63 b5 84 7b 7c  |.......{`~.c..{||
00000050  73 9a 58 b4 f4 c1 fa 17  bb 92 d7 a0 d3 99 e9 32  |s.X............2|
00000060  53 ac dc 8b 27 a3 5c 74  b1 f9 93 02 1e dd 4c 78  |S...'.\t......Lx|
00000070  98 55 c3 cb 9d 70 72 5b  1a e7 74 a7 f4 7f 0b 69  |.U...pr[..t....i|
00000080  71 79 64 d9 52 d2 af 5d  e7 d9 f7 db 17 4d c4 5c  |qyd.R..].....M.\|
00000090  e2 89 83 46 1c 97 38 22  21 c4 5a 62 6d 5a 5b af  |...F..8"!.ZbmZ[.|
000000a0  72 b5 f3 cf 35 59 72 6a  b4 53 a2 10 50 b0 de 7d  |r...5Yrj.S..P..}|
000000b0  e0 1f a5 d3 63 1f 69 97  3d f5 16 a5 ae ba 9d fd  |....c.i.=.......|
000000c0  b7 69 a8 c1 74 73 fa 2d  a5 5e 27 70 3e 51 4b 1f  |.i..ts.-.^'p>QK.|
000000d0  75 3a 3e e2 ba a7 33 7f  2d d7 56 cb e0 75 67 ef  |u:>...3.-.V..ug.|
000000e0  6b 7b f5 67 44 5e 4e bf  0e 8e 3f bf 32 99 75 5a  |k{.gD^N...?.2.uZ|
000000f0  b3 b0 0b f3 cd bb 41 0d  0d 84 26 dc fd ad d9 74  |......A...&....t|
00000100  19 f3 cd 1f 68 fe 75 d6  8a eb 93 b1 ff 3a 48 53  |....h.u......:HS|
00000110  bd 3e c8 af dc 47 13 41  75 21 4d 72 fc dc af d8  |.>...G.Au!Mr....|
00000120  1e d7 98 3f ad 03 b2 07  27 40 42 ef c7 56 91 13  |...?....'@B..V..|
00000130  d9 50 95 6b f3 d8 79 d1  cf d5 74 32 b6 5c 7b ba  |.P.k..y...t2.\{.|
00000140  2d cb 42 66 39 64 1d fe  5c ca f4 5c ed 42 03 5f  |-.Bf9d..\..\.B._|
00000150  f6 3e 96 ff 7f 1c 49 8e  b4 79 2d b9 8e 5d 6e 03  |.>....I..y-..]n.|
00000160  5d f6 42 69 5f 49 49 aa  1e 83 cb 67 d7 ff 42 d8  |].Bi_II....g..B.|
00000170  ce 57 76 23 37 da b2 ce  59 b5 ea 3a 19 24 a6 21  |.Wv#7...Y..:.$.!|
00000180  61 cc db b6 e4 01 c3 50  c7 a6 1c 42 e3 a4 e9 f0  |a......P...B....|
00000190  d5 37 32 28 b4 85 f1 37  e7 59 f1 55 50 7c b2 ae  |.72(...7.Y.UP|..|
000001a0  a2 1d b8 5f 77 bc 96 dd  29 bb a2 99 9a 7c a7 e7  |..._w...)....|..|
000001b0  51 7d 1c 26 01 af b8 f6  66 32 2f 8d 32 af 00 fe  |Q}.&....f2/.2...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a0 3f 00 00 00  |............?...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/kerry/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

---

### Post by pissedoffdude on 2012-05-13
You can fix the booting problem by ensuring your flash drive is unplugged and running the following commands: 
```
sudo grub-install /dev/sda
sudo update-grub
```

As for your networking problem, let us know if this occurs only with the homepage, or all pages as well. You can test if your wireless card is working by typing ```
ping www.google.com 
``` and checking if it reports any info.

---

### Post by Utkarsh Ray on 2012-05-13
> **wilee-nilee said:**
> Sounds like grub, the bootloader, was put in the usb's mbr.

You can run a script to check that, and post it, here is a link, extract it to the desktop and run the command and look at the results.txt and post it.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

The other error I'm not sure.

Results confirm that bootloader is in flash drive.
sda is your HDD
sdb is your USB flash drive

I am not experienced in bootloader stuff but can help with the internet thing.
The error is in the browser's connection configuration, check for proxy, APN, etc.
If it's firefox, you'll get it in
connection settings

---

### Post by kerrry on 2012-05-13
i have put in the codes and no problem has occurred but the Internet or Firefox still doesn't work at all

---

### Post by pissedoffdude on 2012-05-13
The first two codes fix the booting problem.  Did you get any output from the last one?  Let us know which type of card you have by typing: ```
lspci -v
```
There should be a block that mentions "wireless." Post that block here.  Also, does the network applet say you're connected with a certain signal percentage, and do you have any type of wireless security on your network?

---

### Post by Utkarsh Ray on 2012-05-13
Is network connection really established?
Check network tools for that (it's preinstalled), if it shows your connection and the 'in' ' out' counters are not zero then somethings in firefox connection settings.
Check if the networking is enabled (click on the network applet on the top right)
Which kind of connection are you trying to use?
You can ping through the network tools

---

### Post by wilee-nilee on 2012-05-13
> **pissedoffdude said:**
> You can fix the booting problem by ensuring your flash drive is unplugged and running the following commands: 
```
sudo grub-install /dev/sda
sudo update-grub
```As for your networking problem, let us know if this occurs only with the homepage, or all pages as well. You can test if your wireless card is working by typing ```
ping www.google.com 
``` and checking if it reports any info.

Thread starter these commands are correct when run in the installed ubuntu.

---

### Post by kerrry on 2012-05-13
kerry@kerry-Lenovo-IdeaPad-S10-2:~$ sudo update-grub  
 [sudo] password for kerry:  
 Generating grub.cfg ...  
 Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae  
 Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae  
 Found memtest86+ image: /boot/memtest86+.bin  
 done  
 kerry@kerry-Lenovo-IdeaPad-S10-2:~$ lspci -v  
 00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)  
 	Subsystem: Lenovo Device 386f  
 	Flags: bus master, fast devsel, latency 0  
 	Capabilities: <access denied>  
 	Kernel driver in use: agpgart-intel  
 

 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])  
 	Subsystem: Lenovo Device 3870  
 	Flags: bus master, fast devsel, latency 0, IRQ 16  
 	Memory at 98280000 (32-bit, non-prefetchable) [size=512K]  
 	I/O ports at 60c0 [size=8]  
 	Memory at 80000000 (32-bit, prefetchable) [size=256M]  
 	Memory at 98300000 (32-bit, non-prefetchable) [size=256K]  
 	Expansion ROM at <unassigned> [disabled]  
 	Capabilities: <access denied>  
 	Kernel driver in use: i915  
 	Kernel modules: intelfb, i915  
 

 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)  
 	Subsystem: Lenovo Device 3870  
 	Flags: bus master, fast devsel, latency 0  
 	Memory at 98200000 (32-bit, non-prefetchable) [size=512K]  
 	Capabilities: <access denied>  
 

 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)  
 	Subsystem: Lenovo Lenovo 3000 C200 audio [Realtek ALC861VD]  
 	Flags: bus master, fast devsel, latency 0, IRQ 46  
 	Memory at 98340000 (64-bit, non-prefetchable) [size=16K]  
 	Capabilities: <access denied>  
 	Kernel driver in use: snd_hda_intel  
 	Kernel modules: snd-hda-intel  
 

 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0  
 	I/O behind bridge: 00005000-00005fff  
 	Memory behind bridge: 97200000-981fffff  
 	Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff  
 	Capabilities: <access denied>  
 	Kernel driver in use: pcieport  
 	Kernel modules: shpchp  
 

 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0  
 	I/O behind bridge: 00004000-00004fff  
 	Memory behind bridge: 96100000-971fffff  
 	Prefetchable memory behind bridge: 0000000091000000-0000000091ffffff  
 	Capabilities: <access denied>  
 	Kernel driver in use: pcieport  
 	Kernel modules: shpchp  
 

 00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0  
 	I/O behind bridge: 00002000-00003fff  
 	Memory behind bridge: 95100000-960fffff  
 	Prefetchable memory behind bridge: 0000000092000000-00000000930fffff  
 	Capabilities: <access denied>  
 	Kernel driver in use: pcieport  
 	Kernel modules: shpchp  
 

 00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0  
 	I/O behind bridge: 00001000-00001fff  
 	Memory behind bridge: 94100000-950fffff  
 	Prefetchable memory behind bridge: 0000000093100000-00000000940fffff  
 	Capabilities: <access denied>  
 	Kernel driver in use: pcieport  
 	Kernel modules: shpchp  
 

 00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])  
 	Subsystem: Lenovo Device 3807  
 	Flags: bus master, medium devsel, latency 0, IRQ 16  
 	I/O ports at 6080 [size=32]  
 	Kernel driver in use: uhci_hcd  
 

 00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])  
 	Subsystem: Lenovo Device 3808  
 	Flags: bus master, medium devsel, latency 0, IRQ 17  
 	I/O ports at 6060 [size=32]  
 	Kernel driver in use: uhci_hcd  
 

 00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])  
 	Subsystem: Lenovo Device 3809  
 	Flags: bus master, medium devsel, latency 0, IRQ 18  
 	I/O ports at 6040 [size=32]  
 	Kernel driver in use: uhci_hcd  
 

 00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])  
 	Subsystem: Lenovo Device 380a  
 	Flags: bus master, medium devsel, latency 0, IRQ 19  
 	I/O ports at 6020 [size=32]  
 	Kernel driver in use: uhci_hcd  
 

 00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])  
 	Subsystem: Lenovo Device 380b  
 	Flags: bus master, medium devsel, latency 0, IRQ 16  
 	Memory at 98344400 (32-bit, non-prefetchable) [size=1K]  
 	Capabilities: <access denied>  
 	Kernel driver in use: ehci_hcd  
 

 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32  
 	Capabilities: <access denied>  
 

 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)  
 	Subsystem: Lenovo Device 380d  
 	Flags: bus master, medium devsel, latency 0  
 	Capabilities: <access denied>  
 	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng  
 

 00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02) (prog-if 80 [Master])  
 	Subsystem: Lenovo Device 3835  
 	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17  
 	I/O ports at 01f0 [size=8]  
 	I/O ports at 03f4 [size=1]  
 	I/O ports at 0170 [size=8]  
 	I/O ports at 0374 [size=1]  
 	I/O ports at 60a0 [size=16]  
 	Capabilities: <access denied>  
 	Kernel driver in use: ata_piix  
 

 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)  
 	Subsystem: Lenovo Device 380f  
 	Flags: medium devsel, IRQ 11  
 	I/O ports at 6000 [size=32]  
 	Kernel modules: i2c-i801  
 

 02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection  
 	Subsystem: Intel Corporation WiFi Link 5100 AGN  
 	Flags: bus master, fast devsel, latency 0, IRQ 45  
 	Memory at 96100000 (64-bit, non-prefetchable) [size=8K]  
 	Capabilities: <access denied>  
 	Kernel driver in use: iwlwifi  
 	Kernel modules: iwlwifi  
 

 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)  
 	Subsystem: Lenovo Device 389e  
 	Flags: bus master, fast devsel, latency 0, IRQ 44  
 	I/O ports at 2000 [size=256]  
 	Memory at 92010000 (64-bit, prefetchable) [size=4K]  
 	Memory at 92000000 (64-bit, prefetchable) [size=64K]  
 	[virtual] Expansion ROM at 92020000 [disabled] [size=128K]  
 	Capabilities: <access denied>  
 	Kernel driver in use: r8169  
 	Kernel modules: r8169

---

### Post by pissedoffdude on 2012-05-13
Looks like you have an intel 5100agn.  Based on previous posts on the forums, it looks like the card works for an indefinite amount of time and then requires a reboot.  [http://ubuntuforums.org/showthread.php?p=11929828]("http://ubuntuforums.org/showthread.php?p=11929828")
[http://ubuntuforums.org/showthread.php?p=11914732]("http://ubuntuforums.org/showthread.php?p=11914732")

Does it work at all after you reboot?

A user in that last thread I linked claims that the drivers from [http://linuxwireless.org/en/users/Download]("http://linuxwireless.org/en/users/Download") helped.  If you have an ethernet cable, you can install those drivers by using synaptic and marking the package linux-backports-modules-3.2.0  Afterwards, reboot and let us know if that helped

Edit: If synaptic is not installed, use the ubuntu software center. Also,  sure be you have the backports repository enabled.  There should be an option for that in the software center that says something like software sources or repositories.

---

### Post by kerrry on 2012-05-13
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection  
 	Subsystem: Intel Corporation WiFi Link 5100 AGN  
 	Flags: bus master, fast devsel, latency 0, IRQ 45  
 	Memory at 96100000 (64-bit, non-prefetchable) [size=8K]  
 	Capabilities: <access denied>  
 	Kernel driver in use: iwlwifi  
 	Kernel modules: iwlwifi
i have a full connection and it let me connects to the modem and when i go to use the Firefox it comes up with server not found

---

### Post by kerrry on 2012-05-13
i am missing three files out of the software centre-internet-remote desktop viewer, knetAttach, open JDK Java 6 runtime.
i don't have a Ethernet cable and can't seem to copy the files from this computer to a usb

---

### Post by jtarin on 2012-05-13
Do you have a DSL connection besides your wireless connection you can use? You must have a hard-wired connection to get the drivers you need. If not you will have to use another computer to download your drivers and then transfer them to your computer.What problems are you having transferring files to USB?

---

### Post by kerrry on 2012-05-13
i have borrowed an Ethernet cabe for the time being and i am currently downloading the drivers i need. i thank everybody for helping me with these issues and cant wait to have a second computer operating with ubuntu

---

### Post by jtarin on 2012-05-13
You might mark the thread solved then if it is.

---

### Post by kerrry on 2012-05-13
I'm now using new computer to write this and am very impressed and love ubuntu and will definately spread the word about this free and reasonably easy system to install and use, just one update and away you go thank you so much to everyone involved can't recomend or commend highly enough.

---

