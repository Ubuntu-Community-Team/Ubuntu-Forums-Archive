---
title: "The kernel does not see file system"
date: 2018-05-24
forum: New to Ubuntu
---

### Post by kinofan on 2018-05-24
Hello. Ubuntu lts 16.04 (server)

**Problem**: The kernel does not see the file system. 

I'm really dont know what do. When I bought the server occurred error 'segmentation fault'. Hope for your help. Thanks

**After boot server responded: **
ALERT! UUID=cafd8c1a-4c92.... does not exist. Dropping to shell!

**blkid**** output:**

/dev/md2: UUID="cafd8c1a-4c92.... TYPE="ext4"

---

### Post by TheFu on 2018-05-24
Welcome to the forums.

Please copy/paste text, not images.  Save our bandwidth.  Also, I can't read the text in the images.

If it is a new server, I'd just install a fresh copy of ubuntu server 16.04 and be done.  Plus you'll know the installation choices that way.   If not, I'd boot from 16.04 flash media and perform troubleshooting using that.  First is to get my data onto backup media.  Then I'd reinstall grub.  Really need to see the **boot-info.sh** output to understand more about this system.

---

### Post by kinofan on 2018-05-24
> **TheFu said:**
> Welcome to the forums.

Please copy/paste text, not images. Save our bandwidth. Also, I can't read the text in the images.

If it is a new server, I'd just install a fresh copy of ubuntu server 16.04 and be done. Plus you'll know the installation choices that way. If not, I'd boot from 16.04 flash media and perform troubleshooting using that. First is to get my data onto backup media. Then I'd reinstall grub. Really need to see the **boot-info.sh** output to understand more about this system.

Ok, sorry. I'm updated post. 
It's not a fresh copy

---

### Post by TheFu on 2018-05-24
Thanks, but we really need to see the boot-info.   [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by kinofan on 2018-05-24
> **TheFu said:**
> Thanks, but we really need to see the boot-info. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

```

                  Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and looks
    in partition 97 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and looks
    in partition 97 for .


sda1: __________________________________________________________________________


    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:


sda2: __________________________________________________________________________


    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:


sda3: __________________________________________________________________________


    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:


sdb1: __________________________________________________________________________


    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:


sdb2: __________________________________________________________________________


    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:


sdb3: __________________________________________________________________________


    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:


md/0: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info:


md/1: __________________________________________________________________________


    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files:        /grub/grub.cfg


md/2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 16.04.4 LTS
    Boot files:        /etc/fstab


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1               2,048    33,556,479    33,554,432  fd Linux raid autode$
/dev/sda2          33,556,480    34,605,055     1,048,576  fd Linux raid autode$
/dev/sda3          34,605,056 1,000,213,167   965,608,112  fd Linux raid autode$




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1               2,048    33,556,479    33,554,432  fd Linux raid autode$
/dev/sdb2          33,556,480    34,605,055     1,048,576  fd Linux raid autode$
/dev/sdb3          34,605,056 1,000,213,167   965,608,112  fd Linux raid autode$




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0       40c4ea95-0ecc-4c51-9f3e-e49d8f62f160   ext2
/dev/md0         ec827846-fd81-4071-a5b1-6207aef3c1e6   swap
/dev/md1         65eb84ee-19e6-4cf0-ba7e-91af1f813fcc   ext3
/dev/md2         cafd8c1a-4c92-49ed-95b0-91dbb74608c0   ext4
/dev/sda1        e9f6054a-1aef-6dbe-4a06-7a4a3672cf19   linux_raid_member rescu$
/dev/sda2        f01ca78d-4dc0-512b-1ee4-267a143b4376   linux_raid_member rescu$
/dev/sda3        b1b666d6-45b1-4309-d3bc-2023231caaab   linux_raid_member rescu$
/dev/sdb1        e9f6054a-1aef-6dbe-4a06-7a4a3672cf19   linux_raid_member rescu$
/dev/sdb2        f01ca78d-4dc0-512b-1ee4-267a143b4376   linux_raid_member rescu$
/dev/sdb3        b1b666d6-45b1-4309-d3bc-2023231caaab   linux_raid_member rescu$


================================ Mount points: =================================


Device           Mount_Point              Type       Options






============================= md/1/grub/grub.cfg: ==============================


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
function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  # GRUB lacks write support for diskfilter, so recordfail support is disabled.
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
insmod part_msdos
insmod part_msdos
insmod diskfilter
insmod mdraid1x
insmod ext2
set root='mduuid/b1b666d645b14309d3bc2023231caaab'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint='mduuid/b1b666d645b14309d3bc20$
else
  search --no-floppy --fs-uuid --set=root cafd8c1a-4c92-49ed-95b0-91dbb74608c0
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
    set timeout=2
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=2
  fi
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
set linux_gfx_mode=text
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $men$
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod part_msdos
        insmod diskfilter
        insmod mdraid1x
        insmod ext2
        set root='mduuid/f01ca78d4dc0512b1ee4267a143b4376'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint='mduuid/f01ca78d4dc051$
        else
          search --no-floppy --fs-uuid --set=root 65eb84ee-19e6-4cf0-ba7e-91af1$
        fi
        linux   /vmlinuz-4.13.0-41-generic root=UUID=cafd8c1a-4c92-49ed-95b0-91$
        initrd  /initrd.img-4.13.0-41-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-c$
        menuentry 'Ubuntu, with Linux 4.13.0-41-generic' --class ubuntu --class$
                recordfail
                gfxmode $linux_gfx_mode
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio;$
                insmod part_msdos
                insmod part_msdos
        insmod diskfilter
        insmod mdraid1x
        insmod ext2
        set root='mduuid/f01ca78d4dc0512b1ee4267a143b4376'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint='mduuid/f01ca78d4dc051$
        else
          search --no-floppy --fs-uuid --set=root 65eb84ee-19e6-4cf0-ba7e-91af1$
        fi
        linux   /vmlinuz-4.13.0-41-generic root=UUID=cafd8c1a-4c92-49ed-95b0-91$
        initrd  /initrd.img-4.13.0-41-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-c$
        menuentry 'Ubuntu, with Linux 4.13.0-41-generic' --class ubuntu --class$
                recordfail
                gfxmode $linux_gfx_mode
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio;$
                insmod part_msdos
                insmod part_msdos
                insmod diskfilter
                insmod mdraid1x
                insmod ext2
                set root='mduuid/f01ca78d4dc0512b1ee4267a143b4376'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint='mduuid/f01ca7$
                else
                  search --no-floppy --fs-uuid --set=root 65eb84ee-19e6-4cf0-ba$
                fi
                echo    'Loading Linux 4.13.0-41-generic ...'
                linux   /vmlinuz-4.13.0-41-generic root=UUID=cafd8c1a-4c92-49ed$
                echo    'Loading initial ramdisk ...'
                initrd  /initrd.img-4.13.0-41-generic
        }
        menuentry 'Ubuntu, with Linux 4.13.0-41-generic (recovery mode)' --clas$
                recordfail
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio;$
                insmod part_msdos
                insmod part_msdos
                insmod diskfilter
                insmod mdraid1x
                insmod ext2
                set root='mduuid/f01ca78d4dc0512b1ee4267a143b4376'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint='mduuid/f01ca78d4dc0512b1ee4267a143b4376'  65eb84ee-19e6$
                else
                  search --no-floppy --fs-uuid --set=root 65eb84ee-19e6-4cf0-ba7e-91af1f813fcc
                fi
                echo    'Loading Linux 4.13.0-41-generic ...'
                linux   /vmlinuz-4.13.0-41-generic root=UUID=cafd8c1a-4c92-49ed-95b0-91dbb74608c0 ro single nomodeset
                echo    'Loading initial ramdisk ...'
                initrd  /initrd.img-4.13.0-41-generic
        }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
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


=================== md/1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




=============================== md/2/etc/fstab: ================================


--------------------------------------------------------------------------------
proc /proc proc defaults 0 0
/dev/md/0 none swap sw 0 0
/dev/md/1 /boot ext3 defaults 0 0
/dev/md/2 / ext4 defaults 0 0
--------------------------------------------------------------------------------


=============================== StdErr Messages: ===============================


  No volume groups found
cat: /tmp/BootInfo-gWVUqHL0/Tmp_Log: No such file or directory
















```

---

### Post by TheFu on 2018-05-24
There's a bunch of incomplete stuff in the posted output.  If you edited it, please post the full output (the URL would be better). 

If you didn't edit it, looks like there's some funky stuff happening.  I'd wipe and reload the OS, then reload data from backups.  Look out for storage related failures. Something funky is happening.

---

### Post by kinofan on 2018-05-24
> **TheFu said:**
> There's a bunch of incomplete stuff in the posted output. If you edited it, please post the full output (the URL would be better). 

If you didn't edit it, looks like there's some funky stuff happening. I'd wipe and reload the OS, then reload data from backups. Look out for storage related failures. Something funky is happening.

one more:

[https://pastebin.com/X1iP84SK](https://pastebin.com/X1iP84SK)

```
                  Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .


sda1: __________________________________________________________________________


    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 


sda2: __________________________________________________________________________


    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 


sda3: __________________________________________________________________________


    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 


sdb2: __________________________________________________________________________


    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 


sdb3: __________________________________________________________________________


    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 


md/0: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


md/1: __________________________________________________________________________


    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg


md/2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.4 LTS
    Boot files:        /etc/fstab


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1               2,048    33,556,479    33,554,432  fd Linux raid autodetect
/dev/sda2          33,556,480    34,605,055     1,048,576  fd Linux raid autodetect
/dev/sda3          34,605,056 1,000,213,167   965,608,112  fd Linux raid autodetect




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1               2,048    33,556,479    33,554,432  fd Linux raid autodetect
/dev/sdb2          33,556,480    34,605,055     1,048,576  fd Linux raid autodetect
/dev/sdb3          34,605,056 1,000,213,167   965,608,112  fd Linux raid autodetect




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0       40c4ea95-0ecc-4c51-9f3e-e49d8f62f160   ext2       
/dev/md0         ec827846-fd81-4071-a5b1-6207aef3c1e6   swap       
/dev/md1         65eb84ee-19e6-4cf0-ba7e-91af1f813fcc   ext3       
/dev/md2         cafd8c1a-4c92-49ed-95b0-91dbb74608c0   ext4       
/dev/sda1        e9f6054a-1aef-6dbe-4a06-7a4a3672cf19   linux_raid_member rescue:0
/dev/sda2        f01ca78d-4dc0-512b-1ee4-267a143b4376   linux_raid_member rescue:1
/dev/sda3        b1b666d6-45b1-4309-d3bc-2023231caaab   linux_raid_member rescue:2
/dev/sdb1        e9f6054a-1aef-6dbe-4a06-7a4a3672cf19   linux_raid_member rescue:0
/dev/sdb2        f01ca78d-4dc0-512b-1ee4-267a143b4376   linux_raid_member rescue:1
/dev/sdb3        b1b666d6-45b1-4309-d3bc-2023231caaab   linux_raid_member rescue:2


================================ Mount points: =================================


Device           Mount_Point              Type       Options






============================= md/1/grub/grub.cfg: ==============================


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
  # GRUB lacks write support for diskfilter, so recordfail support is disabled.
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
insmod part_msdos
insmod part_msdos
insmod diskfilter
insmod mdraid1x
insmod ext2
set root='mduuid/b1b666d645b14309d3bc2023231caaab'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint='mduuid/b1b666d645b14309d3bc2023231caaab'  cafd8c1a-4c92-49ed-95b0-91dbb74608c0
else
  search --no-floppy --fs-uuid --set=root cafd8c1a-4c92-49ed-95b0-91dbb74608c0
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
    set timeout=2
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=2
  fi
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
set linux_gfx_mode=text
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-cafd8c1a-4c92-49ed-95b0-91dbb74608c0' {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod part_msdos
    insmod diskfilter
    insmod mdraid1x
    insmod ext2
    set root='mduuid/f01ca78d4dc0512b1ee4267a143b4376'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint='mduuid/f01ca78d4dc0512b1ee4267a143b4376'  65eb84ee-19e6-4cf0-ba7e-91af1f813fcc
    else
      search --no-floppy --fs-uuid --set=root 65eb84ee-19e6-4cf0-ba7e-91af1f813fcc
    fi
        linux    /vmlinuz-4.13.0-41-generic root=UUID=cafd8c1a-4c92-49ed-95b0-91dbb74608c0 ro  nomodeset consoleblank=0 net.ifnames=0
    initrd    /initrd.img-4.13.0-41-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-cafd8c1a-4c92-49ed-95b0-91dbb74608c0' {
    menuentry 'Ubuntu, with Linux 4.13.0-41-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-41-generic-advanced-cafd8c1a-4c92-49ed-95b0-91dbb74608c0' {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod part_msdos
        insmod diskfilter
        insmod mdraid1x
        insmod ext2
        set root='mduuid/f01ca78d4dc0512b1ee4267a143b4376'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint='mduuid/f01ca78d4dc0512b1ee4267a143b4376'  65eb84ee-19e6-4cf0-ba7e-91af1f813fcc
        else
          search --no-floppy --fs-uuid --set=root 65eb84ee-19e6-4cf0-ba7e-91af1f813fcc
        fi
        echo    'Loading Linux 4.13.0-41-generic ...'
            linux    /vmlinuz-4.13.0-41-generic root=UUID=cafd8c1a-4c92-49ed-95b0-91dbb74608c0 ro  nomodeset consoleblank=0 net.ifnames=0
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-4.13.0-41-generic
    }
    menuentry 'Ubuntu, with Linux 4.13.0-41-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-41-generic-recovery-cafd8c1a-4c92-49ed-95b0-91dbb74608c0' {
        recordfail
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod part_msdos
        insmod diskfilter
        insmod mdraid1x
        insmod ext2
        set root='mduuid/f01ca78d4dc0512b1ee4267a143b4376'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint='mduuid/f01ca78d4dc0512b1ee4267a143b4376'  65eb84ee-19e6-4cf0-ba7e-91af1f813fcc
        else
          search --no-floppy --fs-uuid --set=root 65eb84ee-19e6-4cf0-ba7e-91af1f813fcc
        fi
        echo    'Loading Linux 4.13.0-41-generic ...'
            linux    /vmlinuz-4.13.0-41-generic root=UUID=cafd8c1a-4c92-49ed-95b0-91dbb74608c0 ro single nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-4.13.0-41-generic
    }
    menuentry 'Ubuntu, with Linux 4.13.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-39-generic-advanced-cafd8c1a-4c92-49ed-95b0-91dbb74608c0' {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod part_msdos
        insmod diskfilter
        insmod mdraid1x
        insmod ext2
        set root='mduuid/f01ca78d4dc0512b1ee4267a143b4376'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint='mduuid/f01ca78d4dc0512b1ee4267a143b4376'  65eb84ee-19e6-4cf0-ba7e-91af1f813fcc
        else
          search --no-floppy --fs-uuid --set=root 65eb84ee-19e6-4cf0-ba7e-91af1f813fcc
        fi
        echo    'Loading Linux 4.13.0-39-generic ...'
            linux    /vmlinuz-4.13.0-39-generic root=UUID=cafd8c1a-4c92-49ed-95b0-91dbb74608c0 ro  nomodeset consoleblank=0 net.ifnames=0
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-4.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 4.13.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-39-generic-recovery-cafd8c1a-4c92-49ed-95b0-91dbb74608c0' {
        recordfail
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod part_msdos
        insmod diskfilter
        insmod mdraid1x
        insmod ext2
        set root='mduuid/f01ca78d4dc0512b1ee4267a143b4376'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint='mduuid/f01ca78d4dc0512b1ee4267a143b4376'  65eb84ee-19e6-4cf0-ba7e-91af1f813fcc
        else
          search --no-floppy --fs-uuid --set=root 65eb84ee-19e6-4cf0-ba7e-91af1f813fcc
        fi
        echo    'Loading Linux 4.13.0-39-generic ...'
            linux    /vmlinuz-4.13.0-39-generic root=UUID=cafd8c1a-4c92-49ed-95b0-91dbb74608c0 ro single nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-4.13.0-39-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
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


=================== md/1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




=============================== md/2/etc/fstab: ================================


--------------------------------------------------------------------------------
proc /proc proc defaults 0 0
/dev/md/0 none swap sw 0 0
/dev/md/1 /boot ext3 defaults 0 0
/dev/md/2 / ext4 defaults 0 0
--------------------------------------------------------------------------------


=============================== StdErr Messages: ===============================


  No volume groups found
cat: /tmp/BootInfo-nNfpGCNV/Tmp_Log: No such file or directory



```

Before the server was down and I could select one of all the additional options in GRUB that would continue to work (Maybe it will help)

---

### Post by TheFu on 2018-05-25
I've never seen output like that. Sorry can't help, if reinstalling grub and updating the initird doesn't handle it. 
That overview is:
* boot from alternate 16.04 media
* go into recovery shell
* manually mount all the different partitions and logical volumes. Might need to run fsck too.
* manually setup a chroot environment which uses the mounted storage as the OS (/proc, /dev, /boot, /, and maybe /boot/efi)
* update-initramfs - this assumes config files for the system are all correct and available; different options are needed
* update-grub - this tells grub to use the new settings, hopefully those will include mounting / and other storage that are on RAID
* reboot - the moment of truth
That's the overview. There are steps that get in the way like installing necessary packages, entering correct options, using the correct devices for each command.

If that doesn't fix it, time for a clear wipe, IMHO. Trying to fix a system that isn't available after a few days offline has negative returns. There's a point where a clean wipe makes more sense.  I've had to do this in a business when a server was rebooted and never came back up.  We got hardware support out ($300/hr) and he found nothing actually wrong.  It wasn't a server that I managed and the other admin hadn't made any backups and really wasn't much of an admin.  After a few days, my boss told me to stop trying to fix it and that it wasn't our problem. We did different work paid for by a different client and our identical server, which was properly maintained, worked perfectly.

Perhaps someone else will see this and help out.

---

### Post by kinofan on 2018-05-25
> **TheFu said:**
> I've never seen output like that. Sorry can't help, if reinstalling grub and updating the initird doesn't handle it. 
That overview is:
* boot from alternate 16.04 media
* go into recovery shell
* manually mount all the different partitions and logical volumes. Might need to run fsck too.
* manually setup a chroot environment which uses the mounted storage as the OS (/proc, /dev, /boot, /, and maybe /boot/efi)
* update-initramfs - this assumes config files for the system are all correct and available; different options are needed
* update-grub - this tells grub to use the new settings, hopefully those will include mounting / and other storage that are on RAID
* reboot - the moment of truth
That's the overview. There are steps that get in the way like installing necessary packages, entering correct options, using the correct devices for each command.

If that doesn't fix it, time for a clear wipe, IMHO. Trying to fix a system that isn't available after a few days offline has negative returns. There's a point where a clean wipe makes more sense. I've had to do this in a business when a server was rebooted and never came back up. We got hardware support out ($300/hr) and he found nothing actually wrong. It wasn't a server that I managed and the other admin hadn't made any backups and really wasn't much of an admin. After a few days, my boss told me to stop trying to fix it and that it wasn't our problem. We did different work paid for by a different client and our identical server which was properly maintained worked perfectly.

Perhaps someone else will see this and help out.

In any case, thanks for the help! I will try

---

