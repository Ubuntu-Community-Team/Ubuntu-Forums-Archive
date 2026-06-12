---
title: "Grub doesn't appear. Can't use my other O.S."
date: 2012-05-09
forum: New to Ubuntu
---

### Post by Moo321 on 2012-05-09
Install ubuntu 12.04 having windows 7, but when I reboot to enter win7 I get nothing and goes straight to ubuntu, I thought I could go back reinstalling but same thing happens, I can not get into windows 7.

---

### Post by wilee-nilee on 2012-05-09
First try running this command from the installed Ubuntu terminal.

```
sudo update-grub
```If windows does not appear in the terminal or the grub menu, download this script, extract it to your desk top and run this command. A results.txt will appear copy all the text, and in your reply click on the # for code tags and paste the text between.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by surfer on 2012-05-09
holding "shift" down during boot should show you the grub menu.

---

### Post by wilee-nilee on 2012-05-09
> **surfer said:**
> holding "shift" down during boot should show you the grub menu.

Sure, but a second OS would have grub showing already if it was in the menu. :)

---

### Post by Moo321 on 2012-05-09
What you mean for code tags, hm replace # for what? i don't really get it.

---

### Post by wilee-nilee on 2012-05-09
> **Moo321 said:**
> What you mean for code tags, hm replace # for what? i don't really get it.

So here is an image of what you see when you hit the response button. Click on the # see the arrow, and it creates the code tags other arrow, paste all the text from the results.txt between them. 
[ATTACH]217569[/ATTACH]

---

### Post by Moo321 on 2012-05-09
> **wilee-nilee said:**
> Sure, but a second OS would have grub showing already if it was in the menu. :)
I try that, but it screen get only blank nothing appear, and monitor says something about frequency, so i don't think that is, cuz i've run LInux MInt and nothing of this happen hm.

---

### Post by Moo321 on 2012-05-09
> **wilee-nilee said:**
> So here is an image of what you see when you hit the response button. Click on the # see the arrow, and it creates the code tags other arrow, paste all the text from the results.txt between them. 
[ATTACH]217569[/ATTACH]
```
.gnome2/                   Vídeos/
.gnome2_private/           .VirtualBox/
.gstreamer-0.10/           VirtualBox VMs/
.gtk-bookmarks             .Xauthority
.gvfs/                     .xsession-errors
>     # Get the embedded menu of
> 
.adobe/                    .ICEauthority
.bash_history              Imágenes/
.bash_logout               .linuxmint/
.cache/                    .local/
.config/                   .macromedia/
.dbus/                     .mozilla/
Descargas/                 Música/
.dmrc                      Plantillas/
Documentos/                .profile
Escritorio/                Público/
.esd_auth                  .pulse/
.gconf/                    .pulse-cookie
.gksu.lock                 .sudo_as_admin_successful
.gnome2/                   Vídeos/
.gnome2_private/           .VirtualBox/
.gstreamer-0.10/           VirtualBox VMs/
.gtk-bookmarks             .Xauthority
.gvfs/                     .xsession-errors
>     get_embedded_menu
> 
>     fa31) # Look at the f
>   case
>     fa31c0) #
> 
> 
.adobe/                    .ICEauthority
.bash_history              Imágenes/
.bash_logout               .linuxmint/
.cache/                    .local/
.config/                   .macromedia/
.dbus/                     .mozilla/
Descargas/                 Música/
.dmrc                      Plantillas/
Documentos/                .profile
Escritorio/                Público/
.esd_auth                  .pulse/
.gconf/                    .pulse-cookie
.gksu.lock                 .sudo_as_admin_successful
.gnome2/                   Vídeos/
.gnome2_private/           .VirtualBox/
.gstreamer-0.10/           VirtualBox VMs/
.gtk-bookmarks             .Xauthority
.gvfs/                     .xsession-errors
>    
> 
> 
> 
.adobe/                    .ICEauthority
.bash_history              Imágenes/
.bash_logout               .linuxmint/
.cache/                    .local/
.config/                   .macromedia/
.dbus/                     .mozilla/
Descargas/                 Música/
.dmrc                      Plantillas/
Documentos/                .profile
Escritorio/                Público/
.esd_auth                  .pulse/
.gconf/                    .pulse-cookie
.gksu.lock                 .sudo_as_admin_successful
.gnome2/                   Vídeos/
.gnome2_private/           .VirtualBox/
.gstreamer-0.10/           VirtualBox VMs/
.gtk-bookmarks             .Xauthority
.gvfs/                     .xsession-errors
> 
> 
.adobe/                    .ICEauthority
.bash_history              Imágenes/
.bash_logout               .linuxmint/
.cache/                    .local/
.config/                   .macromedia/
.dbus/                     .mozilla/
Descargas/                 Música/
.dmrc                      Plantillas/
Documentos/                .profile
Escritorio/                Público/
.esd_auth                  .pulse/
.gconf/                    .pulse-cookie
.gksu.lock                 .sudo_as_admin_successful
.gnome2/                   Vídeos/
.gnome2_private/           .VirtualBox/
.gstreamer-0.10/           VirtualBox VMs/
.gtk-bookmarks             .Xauthority
.gvfs/                     .xsession-errors
>     
> 
> 
.adobe/                    .ICEauthority
.bash_history              Imágenes/
.bash_logout               .linuxmint/
.cache/                    .local/
.config/                   .macromedia/
.dbus/                     .mozilla/
Descargas/                 Música/
.dmrc                      Plantillas/
Documentos/                .profile
Escritorio/                Público/
.esd_auth                  .pulse/
.gconf/                    .pulse-cookie
.gksu.lock                 .sudo_as_admin_successful
.gnome2/                   Vídeos/
.gnome2_private/           .VirtualBox/
.gstreamer-0.10/           VirtualBox VMs/
.gtk-bookmarks             .Xauthority
.gvfs/                     .xsession-errors
>     
> 
> 
> 
> 
> 
> 
> 
.adobe/                    .ICEauthority
.bash_history              Imágenes/
.bash_logout               .linuxmint/
.cache/                    .local/
.config/                   .macromedia/
.dbus/                     .mozilla/
Descargas/                 Música/
.dmrc                      Plantillas/
Documentos/                .profile
Escritorio/                Público/
.esd_auth                  .pulse/
.gconf/                    .pulse-cookie
.gksu.lock                 .sudo_as_admin_successful
.gnome2/                   Vídeos/
.gnome2_private/           .VirtualBox/
.gstreamer-0.10/           VirtualBox VMs/
.gtk-bookmarks             .Xauthority
.gvfs/                     .xsession-errors
>       83e1) BL
> 
> 
> 
>   e
>   
> 
> 
> 
> 
>   esac;;   
>     fabe) BL='No bo
>     faeb)
>     fafc) 
> 
> 
> 
> 
> 
> 
> 
> 
>   esac
> 
> 
> 
> 
> 
>   
> 
>   HDMBR[${HI}]=${BL};
> don
> 
> 
> 
> 
> 
> ## Store and D
> 
> 
> 
> 
>   echo "Computing
> 
>   FP=$((P
> 
> 
>   HDP
> 
> 
>  
> 
> 
> 
>   ReadPT ${HI} 0 4 ${Part
> 
>   ec
> 
> 
> 
>   Ch
> 
>   echo >> ${PartitionTable};
>   HDPT[${HI}
> 
>   case ${PTType} in
>     BootI
> 
> 
> 
>     ReadEMBR  ${HI}
> 
> 
> 
>        LastPartition[${HI
>      
> 
> 
>     fi;;
>       
> 
>     
> 
>     print
> 
> 
> 
> 
> 
> 
> 
>     else
>        FirstParti
> 
>   esac
> done
> 
> 
> 
> ## Loop
> 
> 
> 
> 
>  
> 
>     p
>   
> 
> 
> 
>     system=${SystemArray
> 
> 
> 
>       
>        par
>        # --sizel
>     else
>        
>        name=$(b
> 
>     fi
> 
> 
>      
>    
>  
>   done
> done
> 
> 
> 
> 
> 
> if [ x"$
>   dmraid -an 
> fi 
> 
> 
> 
> ## Sear
> #
> #   Only works if the "LVM
> 
> i
> 
> 
> 
>   for LVM in ${L
> 
>     LVM_Status=$(lvdispl
>     lv
>     name=${LVM:12};
>     mou
> 
>     start=0;
>     e
>     system='';
>     PI=
> 
>     Get_Par
>       
> 
>     [[ "${LV
> 
>   d
> 
> 
> 
> 
> ## Searc
> 
> # 
> 
> 
> 
>   #
> 
> 
>   # Assemble all
> 
>   
>   # All arra
> 
> 
>   for MD in ${MD_Array};
> 
>  
> 
> 
> 
>     fo
>  
> 
> 
> 
>  
> 
> 
>     moun
> 
> 
>     end=${MD_Size};
>     syst
> 
>      
> 
> 
> 
>     [[ "$
> 
>  
> 
> 
> 
> 
> 
> 
> fo
>  
>   FD_Si
>  
> 
> 
>   start=0
> 
> 
> 
> 
>   Get_Partition_Info
> 
> 
> 
>   
> 
> ## Dr
> 
> 
>  
> [ -e ${Partiti
> 
> 
> pri
> 
> 
> 
> echo >> "${Log}
> 
> for dev in $(blkid -o d
>   
> d
> 
> cat 
> 
> 
> 
> 
> if [ $(l
>    pri
> 
> 
> fi
>     
> 
> 
> ## Mou
> 
> printf '==========================
> 
> Moun
> 
> 
> 
> 
> #  orig
> 
> #  ne
> 
> 
> 
>   { su
> 
> 
> 
> 
> ## Writ
> 
> [ -e "${Log
> 
> 
> 
> 
> 
> 
> if [ -e ${Un
>    printf '==
>   
> 
> 
> 
> 
> 
> ## Ad
> 
> 
>    p
>    cat ${FakeHardDrives} >> "${Log}";
>    printf "\n\n" >> "$
> fi
> 
>   
> 
> ## 
> 
> 
> 
> 
> fi
> 
> 
> 
> ## 
> 
> ech
> 
> 
> 
> if [ ${stdout_outp
>    ## If --
>    cat "${Log}";
> 
> 
> 
> 
> 
>    if 
>       chown "${SUDO_UID}:${SUDO_GID}" "${LogFile}";
>    fi
> 
> 
> 
>    
> 
>    #   gzip a 
> 
> 
>    #   ./bootinf
> 
>    if [ ${gzip_output} -eq 1 ] ; the
> 
> 
>       if [ "${SUDO_
> 
> 
> 
> 
> 
> 
>    ##
>  
> 
> 
> 
> 
> 
> 
>    print
> fi
> 
> exit 0;


```

---

### Post by wilee-nilee on 2012-05-09
Look closer at my original link for downloading the bootscript and the command to make the results.txt. What ever you have posted is not it we are looking for, this is what it looks like.

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for /boot/burg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/grub/core.img /boot/burg/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 246784360 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/grub/core.img /boot/burg/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    83,015,679    83,013,632   7 NTFS / exFAT / HPFS
/dev/sda2          83,015,680   128,903,167    45,887,488   7 NTFS / exFAT / HPFS
/dev/sda3         128,905,214   312,580,095   183,674,882   5 Extended
/dev/sda5         128,905,216   212,791,295    83,886,080  83 Linux
/dev/sda6         212,793,344   308,172,799    95,379,456  83 Linux
/dev/sda7         308,174,848   312,580,095     4,405,248  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        2C9E5EA29E5E647C                       ntfs       W7
/dev/sda2        1B1572C979F9A663                       ntfs       
/dev/sda5        4389e17c-0b25-4dd4-9541-fdc4b42cc5b4   ext4       Oneiric
/dev/sda6        65360192-feba-4980-ab32-53c24945f664   ext4       sda6
/dev/sda7        6f2e78d5-fc58-43f5-8253-08b743adaa57   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set=root 4389e17c-0b25-4dd4-9541-fdc4b42cc5b4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 4389e17c-0b25-4dd4-9541-fdc4b42cc5b4
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4389e17c-0b25-4dd4-9541-fdc4b42cc5b4
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=4389e17c-0b25-4dd4-9541-fdc4b42cc5b4 ro   
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4389e17c-0b25-4dd4-9541-fdc4b42cc5b4
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=4389e17c-0b25-4dd4-9541-fdc4b42cc5b4 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 2C9E5EA29E5E647C
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 65360192-feba-4980-ab32-53c24945f664
    linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65360192-feba-4980-ab32-53c24945f664 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 65360192-feba-4980-ab32-53c24945f664
    linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65360192-feba-4980-ab32-53c24945f664 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-23-generic-pae
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

=========================== sda5/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=ubuntu
set gfxmode=640x480
if [ -s $prefix/burgenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
    save_env gfxmode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -burg { command="set theme_name=burg" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 4389e17c-0b25-4dd4-9541-fdc4b42cc5b4
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Ubuntu GNU/Linux, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4389e17c-0b25-4dd4-9541-fdc4b42cc5b4
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=4389e17c-0b25-4dd4-9541-fdc4b42cc5b4 ro  ipv6.disable=1 quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu GNU/Linux, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4389e17c-0b25-4dd4-9541-fdc4b42cc5b4
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=4389e17c-0b25-4dd4-9541-fdc4b42cc5b4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2c9e5ea29e5e647c
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic-pae (on /dev/sda6)" --class ubuntu --class os --group group_/dev/sda6 {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 65360192-feba-4980-ab32-53c24945f664
    linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65360192-feba-4980-ab32-53c24945f664 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode) (on /dev/sda6)" --class ubuntu --class os --group group_/dev/sda6 {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 65360192-feba-4980-ab32-53c24945f664
    linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65360192-feba-4980-ab32-53c24945f664 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-23-generic-pae
}
### END /etc/burg.d/30_os-prober ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
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
/dev/sda5      /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda8 during installation
/dev/sda8 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/burg/burg.cfg                             1
               =                boot/burg/core.img                             1
               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  2
               =                vmlinuz                                        2

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
search --no-floppy --fs-uuid --set=root 65360192-feba-4980-ab32-53c24945f664
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 65360192-feba-4980-ab32-53c24945f664
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 65360192-feba-4980-ab32-53c24945f664
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65360192-feba-4980-ab32-53c24945f664 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 65360192-feba-4980-ab32-53c24945f664
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65360192-feba-4980-ab32-53c24945f664 ro recovery nomodeset 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 65360192-feba-4980-ab32-53c24945f664
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 65360192-feba-4980-ab32-53c24945f664
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 2C9E5EA29E5E647C
    chainloader +1
}
menuentry "Windows 8 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 122A568E278A81BD
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4389e17c-0b25-4dd4-9541-fdc4b42cc5b4
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=4389e17c-0b25-4dd4-9541-fdc4b42cc5b4 ro ipv6.disable=1 quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-23-generic
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4389e17c-0b25-4dd4-9541-fdc4b42cc5b4
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=4389e17c-0b25-4dd4-9541-fdc4b42cc5b4 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-23-generic
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

=========================== sda6/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=ubuntu
set gfxmode=640x480
if [ -s $prefix/burgenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
    save_env gfxmode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -burg { command="set theme_name=burg" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 65360192-feba-4980-ab32-53c24945f664
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Ubuntu GNU/Linux, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 65360192-feba-4980-ab32-53c24945f664
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65360192-feba-4980-ab32-53c24945f664 ro  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu GNU/Linux, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 65360192-feba-4980-ab32-53c24945f664
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65360192-feba-4980-ab32-53c24945f664 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2c9e5ea29e5e647c
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic (on /dev/sda5)" --class ubuntu --class os --group group_/dev/sda5 {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4389e17c-0b25-4dd4-9541-fdc4b42cc5b4
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=4389e17c-0b25-4dd4-9541-fdc4b42cc5b4 ro
    initrd /boot/initrd.img-3.2.0-23-generic
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic (recovery mode) (on /dev/sda5)" --class ubuntu --class os --group group_/dev/sda5 {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4389e17c-0b25-4dd4-9541-fdc4b42cc5b4
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=4389e17c-0b25-4dd4-9541-fdc4b42cc5b4 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-23-generic
}
### END /etc/burg.d/30_os-prober ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
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
/dev/sda6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
/dev/sda8 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/burg/burg.cfg                             1
               =                boot/burg/core.img                             1
               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           3
               =                boot/vmlinuz-3.2.0-23-generic-pae              2
               =                initrd.img                                     3
               =                vmlinuz                                        2

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by Moo321 on 2012-05-09
Well i try using the WIndows cd to delete but didnt work, it only appear grub terminal not found, i use the bootinfoscript and this show up
```
bash: syntax error near unexpected token `newline'
```

---

### Post by wilee-nilee on 2012-05-09
> **Moo321 said:**
> Well i try using the WIndows cd to delete but didnt work, it only appear grub terminal not found, i use the bootinfoscript and this show up
```
bash: syntax error near unexpected token `newline'
```

You have to run this script from a Ubuntu live cd or install. 

Are we having a communication problem here due to language or other issues?

Or is this Ubuntu installed from windows a wubi install

You state that you boot straight to Ubuntu, so I have given you a link to the bootscript, it needs to be extracted to the Ubuntu desktop and the command run.

Make sure you just copy and paste the command it has to be run exactly as it is.

---

