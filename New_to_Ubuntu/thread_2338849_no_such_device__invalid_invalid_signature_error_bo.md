---
title: "no such device / invalid invalid signature error booting from Ubuntu16.4LTS to W8"
date: 2016-10-02
forum: New to Ubuntu
---

### Post by 20GT on 2016-10-02
I'm a complete noob and when I search this error everything has something about grub in it?
I know nothing about grub and my error does not mention grub 


when booting Ubuntu16.4LTS to windows 8
error no such device 9016A0A716A09030
setting petition to 0x83
error invalid signature

I haven't tried changing the boot order in the bios yet.
I do not have the Windows install or repair CD appropriate to my version of Windows 8.

could someone advise me in laymans terms how to fix this?
Thanks

---

### Post by oldos2er on 2016-10-02
Is your system UEFI? Have you disabled Secure Boot, and Windows fast boot? > when booting Ubuntu16.4LTS to windows 8 Not sure what you mean by that. Do you have Ubuntu actually installed, or are you booting from a live medium to install it?

The error looks like it's coming from a DOS/Win boot loader rather than grub, but I can't say for sure.

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by 20GT on 2016-10-02
Sorry I guess I should have explained it further. I have them both set up on different disc Ubuntu boots first and asks at the pink screen if I want to boot Windows 8. 

It's been working good for months and all of a sudden it just stopped last night. 

Not sure what UEIF is. I believe fastboot is disabled. I was able to see the windows drive and I mounted it read only so that it wouldn't mess with it. 

That was when I first set it up it's been working good until now

---

### Post by oldos2er on 2016-10-02
> Not sure what UEIF is That's why I included the links.

Thanks for giving more details, every little bit helps. [s]If possible could you boot Ubuntu from a live USB or DVD (the one you installed from would work) and run the [boot info script]("http://bootinfoscript.sourceforge.net/"), and provide us with the RESULTS.txt file?[/s] See oldfred's post.

---

### Post by oldfred on 2016-10-02
@oldos2er
The original bootinfoscript does not seem to be maintained anymore.
There is a fork here that has been updated to include corrections for newest grub2.
 Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript) 

Also Boot-Repair now uses the updated fork as part of its Summary Report. 
      
 [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by oldos2er on 2016-10-02
Thanks, oldfred!

---

### Post by 20GT on 2016-10-02
I'm a little befuddled, remember noob and laymans terms

so you want me to run 
```
 sudo ./bootinfoscript <outputfile>
``` 

And post it here?

---

### Post by 20GT on 2016-10-02
ok i get it I'm looking for rufus 2.11 that can run on ubuntu to make the USB stick

there is no rufus for ubuntu  have to use unetbootin 
[SIZE=3][FONT=arial]unetbootin does not see my USB to write to it, I formatted it to FAT32 like it wanted, still no luck.
If its not one thing its another making USB on a windows computer right now
 [/FONT][/SIZE]

---

### Post by oldfred on 2016-10-02
I believe rufus is just a standard Windows program to convert an ISO to a bootable USB flash drive.

 Usb installer from Windows - pendrive may not work with UEFI
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)
You can use Win32 Disk Imager to install Ubuntu to a USB pendrive from Windows.
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by 20GT on 2016-10-02
yes that may be but my windows was not reachable to install it so i went to my neighbors house and made the USB stick.
but as my luck is my bios does not have an option to boot from usb 
isn't there anyother way to get this information you need 
can i load ./bootinfoscript on this OS and run it? 
will this work? [https://sourceforge.net/projects/bootinfoscript/files/latest/download](https://sourceforge.net/projects/bootinfoscript/files/latest/download)

---

### Post by 20GT on 2016-10-02
ok its running

---

### Post by oldfred on 2016-10-02
If your system originally came with Windows 8, it will boot from flash drive.
But installer has to correctly convert ISO to flash drive. ISO has to be correctly downloaded.
Some installers or some flash drives or some USB ports work and others do not. Sometimes you just have to experiment.
Some also require you to specifically turn on allow boot from USB ports in UEFI, especially if secure boot is on as allowing another system to boot may not be secure.

Only systems before about 2006 may or may not boot from USB ports.

---

### Post by 20GT on 2016-10-02
here's the log information for the original question
```
steve@ubuntu16-4lts:~/temp$ sudo ./bootinfoscript log.txt
[sudo] password for steve: 


Boot Info Script 0.61      [1 April 2012]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.


                  Boot Info Script 0.61      [1 April 2012]








============================= Boot Info Summary: ===============================




 => No known boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.




sdb1: __________________________________________________________________________




    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        




sdc1: __________________________________________________________________________




    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab




sdc2: __________________________________________________________________________




    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 




sdc5: __________________________________________________________________________




    File system:       swap
    Boot sector type:  -
    Boot sector info: 




sdd1: __________________________________________________________________________




    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 16392 of /dev/sdd1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys




============================ Drive/Partition Info: =============================




Drive: sda _____________________________________________________________________




Partition  Boot  Start Sector    End Sector  # of Sectors  Id System




Invalid MBR Signature found.








Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos




Partition  Boot  Start Sector    End Sector  # of Sectors  Id System




/dev/sdb1               2,048   976,766,975   976,764,928   7 NTFS / exFAT / HPFS








Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 74.5 GiB, 80000000000 bytes, 156250000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos




Partition  Boot  Start Sector    End Sector  # of Sectors  Id System




/dev/sdc1    *          2,048   150,042,623   150,040,576  83 Linux
/dev/sdc2         150,044,670   156,248,063     6,203,394   5 Extended
/dev/sdc5         150,044,672   156,248,063     6,203,392  82 Linux swap / Solaris








Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 3.8 GiB, 4007657472 bytes, 7827456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos




Partition  Boot  Start Sector    End Sector  # of Sectors  Id System




/dev/sdd1    *          2,048     7,827,455     7,825,408   c W95 FAT32 (LBA)








"blkid" output: ________________________________________________________________




Device           UUID                                   TYPE       LABEL




/dev/sdb1        7EC02439C023F5D5                       ntfs       Local Disk
/dev/sdc1        28bc5276-6db0-4ad8-8252-f716d0c7d1ee   ext4       
/dev/sdc5        ca688fc8-21eb-43ac-a43c-07e12cb3bae5   swap       
/dev/sdd1        949A-76E9                              vfat       UBUNTU 16_0
/dev/sr0         142B1A4420554446                       udf        Sep 28 2016




================================ Mount points: =================================




Device           Mount_Point              Type       Options




/dev/sdb1        /media/steve/Local Disk  fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sdc1        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdd1        /media/steve/UBUNTU 16_0 vfat       (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)








=========================== sdc1/boot/grub/grub.cfg: ===========================




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
insmod part_msdos
insmod ext2
set root='hd2,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
else
  search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
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
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
    else
      search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
    fi
    linux    /boot/vmlinuz-4.4.0-36-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-36-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
    menuentry 'Ubuntu, with Linux 4.4.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-36-generic-advanced-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-36-generic ...'
        linux    /boot/vmlinuz-4.4.0-36-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-36-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-36-generic-init-upstart-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-36-generic ...'
        linux    /boot/vmlinuz-4.4.0-36-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-36-generic-recovery-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-36-generic ...'
        linux    /boot/vmlinuz-4.4.0-36-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-34-generic-advanced-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-34-generic ...'
        linux    /boot/vmlinuz-4.4.0-34-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-34-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-34-generic-init-upstart-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-34-generic ...'
        linux    /boot/vmlinuz-4.4.0-34-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-34-generic-recovery-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-34-generic ...'
        linux    /boot/vmlinuz-4.4.0-34-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-advanced-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-31-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-init-upstart-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-recovery-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-28-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-28-generic-advanced-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-28-generic ...'
        linux    /boot/vmlinuz-4.4.0-28-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-28-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-28-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-28-generic-init-upstart-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-28-generic ...'
        linux    /boot/vmlinuz-4.4.0-28-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-28-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-28-generic-recovery-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-28-generic ...'
        linux    /boot/vmlinuz-4.4.0-28-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-28-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-24-generic-advanced-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-24-generic ...'
        linux    /boot/vmlinuz-4.4.0-24-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-24-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-24-generic-init-upstart-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-24-generic ...'
        linux    /boot/vmlinuz-4.4.0-24-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-24-generic-recovery-28bc5276-6db0-4ad8-8252-f716d0c7d1ee' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        else
          search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
        fi
        echo    'Loading Linux 4.4.0-24-generic ...'
        linux    /boot/vmlinuz-4.4.0-24-generic root=UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-24-generic
    }
}




### END /etc/grub.d/10_linux ###




### BEGIN /etc/grub.d/20_linux_xen ###




### END /etc/grub.d/20_linux_xen ###




### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
    else
      search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  28bc5276-6db0-4ad8-8252-f716d0c7d1ee
    else
      search --no-floppy --fs-uuid --set=root 28bc5276-6db0-4ad8-8252-f716d0c7d1ee
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###




### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 8 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-9016A0A716A09030' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9016A0A716A09030
    else
      search --no-floppy --fs-uuid --set=root 9016A0A716A09030
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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




=============================== sdc1/etc/fstab: ================================




--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=28bc5276-6db0-4ad8-8252-f716d0c7d1ee /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca688fc8-21eb-43ac-a43c-07e12cb3bae5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/disk/by-uuid/9016A0A716A09030 /mnt/9016A0A716A09030 auto nosuid,nodev,nofail,x-gvfs-show,noauto,ro 0 0
--------------------------------------------------------------------------------




=================== sdc1: Location of files loaded by Grub: ====================




           GiB - GB             File                                 Fragment(s)








=========================== sdd1/boot/grub/grub.cfg: ===========================




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




============================== sdd1/syslinux.cfg: ==============================




--------------------------------------------------------------------------------
DEFAULT loadconfig




LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------




=================== sdd1: Location of files loaded by Grub: ====================




           GiB - GB             File                                 Fragment(s)








================= sdd1: Location of files loaded by Syslinux: ==================




           GiB - GB             File                                 Fragment(s)








======================== Unknown MBRs/Boot Sectors/etc: ========================




Unknown MBR on /dev/sda












=============================== StdErr Messages: ===============================




hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
cat: /tmp/BootInfo-u82VZQlP/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-u82VZQlP/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-u82VZQlP/Tmp_Log: No such file or directory









```

---

### Post by oldfred on 2016-10-02
Your sdb & sdc are MBR partitioned. But sda does not show at all.
Post this:
sudo gdisk -l /dev/sda

You used older bootinfoscript not new fork, so cannot tell if grub installed correctly in MBR of sdc.

If in BIOS you choose to boot sdc does it work?

May be better to run the more detailed Boot-Repair Summary report.

---

### Post by 20GT on 2016-10-02
> 

May be better to run the more detailed Boot-Repair Summary report.

more detailed Boot-Repair Summary report?????


I'm lost! how do I copy just the script needed from [https://github.com/arvidjaar/bootinfoscript/blob/master/bootinfoscript](https://github.com/arvidjaar/bootinfoscript/blob/master/bootinfoscript) I keep getting everything else on the page

```

steve@ubuntu16-4lts:~/temp$ sudo gdisk -l /dev/sda
[sudo] password for steve: 
GPT fdisk (gdisk) version 1.0.1


Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present


Creating new GPT entries.
Disk /dev/sda: 321672960 sectors, 153.4 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 30D6E6DF-6F86-4CA0-B187-7F6B1AC6E14D
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 321672926
Partitions will be aligned on 2048-sector boundaries
Total free space is 321672893 sectors (153.4 GiB)


Number  Start (sector)    End (sector)  Size       Code  Name

```

I don't understand why we are messing with the USB still, wasn't the sole purpose of that  to run a script contained on it?
If I can get the correct script from Github will that be OK is [this ]("https://github.com/arvidjaar/bootinfoscript/blob/master/bootinfoscript")the correct script

---

### Post by 20GT on 2016-10-02
why is this so complicated? is there a newer script than [https://github.com/arvidjaar/bootinf...bootinfoscript](https://github.com/arvidjaar/bootinf...bootinfoscript)



```

steve@ubuntu16-4lts:~/temp$ sudo ./bootinfoscript log.txt
[sudo] password for steve: 


Boot Info Script 0.74      [06 February 2016]


"mawk v1.3.3" has known bugs.
Install "mawk v1.3.4" or newer from http://invisible-island.net/mawk/ or use "gawk" instead.


Please install the missing program(s) and run Boot Info Script again.

```

---

### Post by 20GT on 2016-10-02
I can't seem to post the contents of the file so heres a link to it [http://www.funsun321.com/log.txt](http://www.funsun321.com/log.txt)

---

### Post by oldfred on 2016-10-02
Neither gdisk nor the updated bootinfoscript show anything about sda.

Try testdisk. It can scan for old partitions. But if you changed partitions multiple times it may find all those old partitions and you have to choose a set that does not overlap with an older partition. If you knew partitions layout that would be helpful. Why I run bootinfoscript as part of my backup, so I have current partition details.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by 20GT on 2016-10-02
> **oldfred said:**
> Neither gdisk nor the updated bootinfoscript show anything about sda.

Try testdisk. It can scan for old partitions. But if you changed partitions multiple times it may find all those old partitions and you have to choose a set that does not overlap with an older partition. If you knew partitions layout that would be helpful. Why I run bootinfoscript as part of my 

do you mean this [URL="http://www.cgsecurity.org/wiki/TestDisk_Download"]testdisk
[/URL]
is that's what meant by
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error

i was hoping this was want you needed
```
menuentry 'Windows 8 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-9016A0A716A09030' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9016A0A716A09030
	else
	  search --no-floppy --fs-uuid --set=root 9016A0A716A09030
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
```

---

### Post by oldfred on 2016-10-02
Testdisk is in the repository. Easier to install than download.

From Ubuntu live installer:
sudo apt-get install testdisk
sudo testdisk

Then follow details on testdisk's site.

---

### Post by 20GT on 2016-10-03
> **oldfred said:**
> May be better to run the more detailed Boot-Repair Summary report.

Thanks for all your help 

Before testdisk how do I run the more detailed Boot-Repair Summary report.

---

### Post by 20GT on 2016-10-03
What did does "settings partition type to 0x83"

[IMG]http://s11.postimg.org/7ljn8d1k3/20161002_082156_1.jpg[/IMG]

---

### Post by oldfred on 2016-10-03
83 is Linux, 07 is NTFS. The script showed a grub entry to boot Windows from sda1, It looked more like a BIOS boot entry rather than the usual UEFI boot for Windows 8.
Is your Windows 8 an upgrade from Windows 7 which then would be BIOS. Or did you install it yourself?

I expect testdisk to find NTFS partition(s). But Windows 7 typically used all 4 primary (MBR) partitions on a drive.

---

### Post by 20GT on 2016-10-03
Windows 8 fresh installed myself

---

### Post by oldfred on 2016-10-03
May be BIOS/MBR or UEFI/gpt as installer installs in mode you boot install media.
If older system then BIOS/MBR as old hardware does not have UEFI.

---

### Post by 20GT on 2016-10-03
> **oldfred said:**
> May be BIOS/MBR or UEFI/gpt as installer installs in mode you boot install media.
If older system then BIOS/MBR as old hardware does not have UEFI.

what does that mean???

Has ubuntu done anything to my windows drive? 
If I make windows my main boot drive again, (so it boots to windows instead of dealing with ubuntu) and fix the MBR should it load? Online it looks like the MBR can be repaired as an easy thing with the right programs?

---

### Post by 20GT on 2016-10-03
Can anyone decipher which drive the Windows 8 is on from this log [http://funsun321.com/log.txt](http://funsun321.com/log.txt)

or this

```
steve@ubuntu16-4lts:~/temp$ sudo gdisk -l /dev/sda[sudo] password for steve: 
GPT fdisk (gdisk) version 1.0.1




Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present




Creating new GPT entries.
Disk /dev/sda: 321672960 sectors, 153.4 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 30D6E6DF-6F86-4CA0-B187-7F6B1AC6E14D
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 321672926
Partitions will be aligned on 2048-sector boundaries
Total free space is 321672893 sectors (153.4 GiB)

```

[SIZE=4]is that talking about the windows8 drive?[/SIZE]

---

### Post by oldfred on 2016-10-03
If you had Windows it must have been on sda, but sda is showing major corruption.
Have you tried testdisk to see if it shows your Windows partitions?

---

### Post by 20GT on 2016-10-03
It's not if I had windows. Yes I had windows on a separate drive.

I'm taking it to a computer shop. Thanks for all your time and help.

---

### Post by 20GT on 2016-10-03
> **oldfred said:**
> If you had Windows it must have been on sda

what does ***on sda*** mean?

---

### Post by 20GT on 2016-10-03
Has Ubuntu, with the settings change to 0x83 interfered with fixing the MBR, if I were to remove the Ubuntu drive and boot from the Windows drive?

---

### Post by oldfred on 2016-10-03
Not related.
The software could not find any partitions, so just assumed Linux standard type (which was an incorrect assumption).
MBR has both software to start boot process and list of the 4 primary partitions. Those are two separate things in MBR.

---

### Post by 20GT on 2016-10-03
thanks

---

### Post by 20GT on 2016-10-04
If the data on the drive is still in good condition is there something I can remove so Ubuntu thinks it just another storage drive and let me access the info? I realize this would be completely deactivating windows permanently

---

### Post by oldfred on 2016-10-04
Did you try testdisk? It also has a deeper search to look for files.
And testdisk includes photorec which just scans drive for anything that looks like a file by type, but does not recover name, so you have to manually sort and rename.

       [URL="https://help.ubuntu.com/community/DataRecovery"]https://help.ubuntu.com/community/DataRecovery

[/URL]
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam. 

[URL="https://help.ubuntu.com/community/DataRecovery"]
[/URL]

---

### Post by 20GT on 2016-10-04
It's at the computer shop now they are going to look for data consistency if it's there they'll let me know

---

### Post by oldfred on 2016-10-04
Often computer shop just reinstalls Windows and you lose all your data. And they do not know about Linux, so may or may not corrupt any Linux installs.

You do have good backups?

---

### Post by 20GT on 2016-10-13
[Continued with Murphys Law in effect]("https://ubuntuforums.org/showthread.php?t=2339696") ](*,)

---

