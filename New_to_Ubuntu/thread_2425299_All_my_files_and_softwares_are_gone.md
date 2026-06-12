---
title: "All my files and softwares are gone"
date: 2019-08-23
forum: New to Ubuntu
---

### Post by yaronshemeshnew on 2019-08-23
I dont know what I did but when I restarted the laptop The system didnt come up and I only saw the Ubuntu icon. So I decided to reinstall the Ubuntu and I think I deleted the files. How can I load the original system? How can I recover my files? I will show pictures of the options. I even sent the laptop to a technican to check if he can recover the files. I want to recover all the softwares I installed in the laptop and I dont know how to do it, including bash commands. I only was able to go to the pre boot system preformance check so I clicked continue and I did restore of the system and I installed Ubnutu 18.04 alongside Ubuntu 18.04.03 and when I restarted it I saw a black screen with few sentances: Ubuntu Advanced options for Ubuntu system setup Restore OS to factory state. Thank you very much for your support. Have a great day.

---

### Post by Frogs Hair on 2019-08-23
Please indicate what type of computer you have and whether it come with Ubuntu installed. Ubuntu is not Windows and has no system restore option and a factory reset could only apply if the system came with Ubuntu and has a recovery partition, but this would not restore any of your own files.
> [COLOR=#000000]I even sent the laptop to a technican to check if he can recover the files.[/COLOR] What did the tech tell you about file recovery ?

---

### Post by oldfred on 2019-08-23
If you reinstall, did you overwrite old install or install side by side?
If you overwrite & reformatted system, most if not all your data is gone. You should then just restore from your backups.

If you installed side by side, your data is still there, but your issue may just have been file corruption and fsck would be all that was required.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yaronshemeshnew on 2019-08-24
I have Dell inspiron 15 3000 i7.
It came with the system installed. I used the factory reset because I saw the pre bios screen. Im trying to upload the images.
Can you send me your email?
I reinstalled the partion a
sideby
side in two version. Thats the only option I had.
How can I only if I did overwrite or not?
I read the link you published and thats exactly what I needed. 
I didnt know how to use it and now I see. 
Do I have to do all of the steps?
The laptop its in the techincian and Im worried. He told me he will check if he can restore the data from the Hard Drive. He will let me know. 
I think he wont be able to recouver it and thats a software issue.

---

### Post by yaronshemeshnew on 2019-08-24
If I will do boot repair the system will show up?
The system still exists in the computer but Im not able to log in to it. 
I hope hee tech guy wont touch the system.
I think I just need to run the commands in bash. 
Do I need to do the FSCK instructions and the boot repair tutrial?

---

### Post by oldfred on 2019-08-24
Just run the report that Boot-Repair creates & post the link.
Occasionally the auto fix causes more issues, so best someone reviews it first.

Pre-installed Dell have a script & special grub entry for recovery, so you need good backups.
But if upgrading then you in effect stop being the Dell install & are then just another Ubuntu install on a Dell.

---

### Post by yaronshemeshnew on 2019-08-24
Ok I did it and the link is:

[http://paste.ubuntu.com/p/hY3vHbkf2c/](http://paste.ubuntu.com/p/hY3vHbkf2c/)

What is the next step?

Thank you very much.

---

### Post by oldfred on 2019-08-24
Boot-Repair has not been totally updated to show all details on the new NVMe drives.

Did you boot from install in p4, report seems to say that.
But report is not showing any grub.cfg in either p3 or p4, just the grub files needed to create a grub.cfg. 
And if able to boot, you must have a grub.cfg, so is report just not showing it?

See if from terminal this works.  If it does post that in code tags. (# in Forum's advanced editor)

cat /boot/grub/grub.cfg

You also have both p3 & p4 labeled the same. Change one just so not same. It may be reason for some mount issues.

```
/dev/nvme0n1p3: [COLOR=#ff0000]LABEL="UBUNTU"[/COLOR] UUID="df0da40a-01d2-4405-bff6-892d2d41959b" TYPE="ext4" PARTUUID="97b397d0-9297-46f2-9f7d-9a1a64e36b89"
/dev/nvme0n1p4: [COLOR=#0000ff]LABEL="UBUNTU"[/COLOR] UUID="d248473d-c469-415e-a0ba-998bf9311d10" TYPE="ext4" PARTUUID="4ecb7eda-b269-44da-b49a-fa4d457ee1a5"

```

If in your system, you can use Disks to change labels. Or use gparted from Ubuntu flash drive. It may only let you change the one that is not mounted. So if booted in p4, change p3 to ubuntu_dell or whatever you like.

---

### Post by yaronshemeshnew on 2019-08-24
I ran the command and I got this:

```
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
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root  d248473d-c469-415e-a0ba-998bf9311d10
else
  search --no-floppy --fs-uuid --set=root d248473d-c469-415e-a0ba-998bf9311d10
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
        set vt_handoff=vt.handoff=1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-d248473d-c469-415e-a0ba-998bf9311d10' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  d248473d-c469-415e-a0ba-998bf9311d10
    else
      search --no-floppy --fs-uuid --set=root d248473d-c469-415e-a0ba-998bf9311d10
    fi
    linux    /boot/vmlinuz-4.15.0-1024-oem.efi.signed root=UUID=d248473d-c469-415e-a0ba-998bf9311d10 ro mem_sleep_default=deep usbcore.quirks=2386:3119:k  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.15.0-1024-oem
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-d248473d-c469-415e-a0ba-998bf9311d10' {
    menuentry 'Ubuntu, with Linux 4.15.0-1024-oem' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-1024-oem-advanced-d248473d-c469-415e-a0ba-998bf9311d10' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  d248473d-c469-415e-a0ba-998bf9311d10
        else
          search --no-floppy --fs-uuid --set=root d248473d-c469-415e-a0ba-998bf9311d10
        fi
        echo    'Loading Linux 4.15.0-1024-oem ...'
        linux    /boot/vmlinuz-4.15.0-1024-oem.efi.signed root=UUID=d248473d-c469-415e-a0ba-998bf9311d10 ro mem_sleep_default=deep usbcore.quirks=2386:3119:k  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-1024-oem
    }
    menuentry 'Ubuntu, with Linux 4.15.0-1024-oem (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-1024-oem-recovery-d248473d-c469-415e-a0ba-998bf9311d10' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  d248473d-c469-415e-a0ba-998bf9311d10
        else
          search --no-floppy --fs-uuid --set=root d248473d-c469-415e-a0ba-998bf9311d10
        fi
        echo    'Loading Linux 4.15.0-1024-oem ...'
        linux    /boot/vmlinuz-4.15.0-1024-oem.efi.signed root=UUID=d248473d-c469-415e-a0ba-998bf9311d10 ro recovery nomodeset mem_sleep_default=deep usbcore.quirks=2386:3119:k 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-1024-oem
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 18.04.3 LTS (18.04) (on /dev/nvme0n1p3)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-df0da40a-01d2-4405-bff6-892d2d41959b' {
    insmod part_gpt
    insmod ext2
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  df0da40a-01d2-4405-bff6-892d2d41959b
    else
      search --no-floppy --fs-uuid --set=root df0da40a-01d2-4405-bff6-892d2d41959b
    fi
    linux /boot/vmlinuz-4.15.0-1050-oem root=UUID=df0da40a-01d2-4405-bff6-892d2d41959b ro mem_sleep_default=deep usbcore.quirks=2386:3119:k quiet splash $vt_handoff
    initrd /boot/initrd.img-4.15.0-1050-oem
}
submenu 'Advanced options for Ubuntu 18.04.3 LTS (18.04) (on /dev/nvme0n1p3)' $menuentry_id_option 'osprober-gnulinux-advanced-df0da40a-01d2-4405-bff6-892d2d41959b' {
    menuentry 'Ubuntu (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.15.0-1050-oem--df0da40a-01d2-4405-bff6-892d2d41959b' {
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  df0da40a-01d2-4405-bff6-892d2d41959b
        else
          search --no-floppy --fs-uuid --set=root df0da40a-01d2-4405-bff6-892d2d41959b
        fi
        linux /boot/vmlinuz-4.15.0-1050-oem root=UUID=df0da40a-01d2-4405-bff6-892d2d41959b ro mem_sleep_default=deep usbcore.quirks=2386:3119:k quiet splash $vt_handoff
        initrd /boot/initrd.img-4.15.0-1050-oem
    }
    menuentry 'Ubuntu, with Linux 4.15.0-1050-oem (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.15.0-1050-oem--df0da40a-01d2-4405-bff6-892d2d41959b' {
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  df0da40a-01d2-4405-bff6-892d2d41959b
        else
          search --no-floppy --fs-uuid --set=root df0da40a-01d2-4405-bff6-892d2d41959b
        fi
        linux /boot/vmlinuz-4.15.0-1050-oem root=UUID=df0da40a-01d2-4405-bff6-892d2d41959b ro mem_sleep_default=deep usbcore.quirks=2386:3119:k quiet splash $vt_handoff
        initrd /boot/initrd.img-4.15.0-1050-oem
    }
    menuentry 'Ubuntu, with Linux 4.15.0-1050-oem (recovery mode) (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.15.0-1050-oem-root=UUID=df0da40a-01d2-4405-bff6-892d2d41959b ro recovery nomodeset mem_sleep_default=deep usbcore.quirks=2386:3119:k-df0da40a-01d2-4405-bff6-892d2d41959b' {
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  df0da40a-01d2-4405-bff6-892d2d41959b
        else
          search --no-floppy --fs-uuid --set=root df0da40a-01d2-4405-bff6-892d2d41959b
        fi
        linux /boot/vmlinuz-4.15.0-1050-oem root=UUID=df0da40a-01d2-4405-bff6-892d2d41959b ro recovery nomodeset mem_sleep_default=deep usbcore.quirks=2386:3119:k
        initrd /boot/initrd.img-4.15.0-1050-oem
    }
    menuentry 'Ubuntu, with Linux 4.15.0-1045-oem (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.15.0-1045-oem--df0da40a-01d2-4405-bff6-892d2d41959b' {
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  df0da40a-01d2-4405-bff6-892d2d41959b
        else
          search --no-floppy --fs-uuid --set=root df0da40a-01d2-4405-bff6-892d2d41959b
        fi
        linux /boot/vmlinuz-4.15.0-1045-oem root=UUID=df0da40a-01d2-4405-bff6-892d2d41959b ro mem_sleep_default=deep usbcore.quirks=2386:3119:k quiet splash $vt_handoff
        initrd /boot/initrd.img-4.15.0-1045-oem
    }
    menuentry 'Ubuntu, with Linux 4.15.0-1045-oem (recovery mode) (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.15.0-1045-oem-root=UUID=df0da40a-01d2-4405-bff6-892d2d41959b ro recovery nomodeset mem_sleep_default=deep usbcore.quirks=2386:3119:k-df0da40a-01d2-4405-bff6-892d2d41959b' {
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  df0da40a-01d2-4405-bff6-892d2d41959b
        else
          search --no-floppy --fs-uuid --set=root df0da40a-01d2-4405-bff6-892d2d41959b
        fi
        linux /boot/vmlinuz-4.15.0-1045-oem root=UUID=df0da40a-01d2-4405-bff6-892d2d41959b ro recovery nomodeset mem_sleep_default=deep usbcore.quirks=2386:3119:k
        initrd /boot/initrd.img-4.15.0-1045-oem
    }
    menuentry 'Ubuntu, with Linux 4.15.0-1024-oem (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.15.0-1024-oem.efi.signed--df0da40a-01d2-4405-bff6-892d2d41959b' {
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  df0da40a-01d2-4405-bff6-892d2d41959b
        else
          search --no-floppy --fs-uuid --set=root df0da40a-01d2-4405-bff6-892d2d41959b
        fi
        linux /boot/vmlinuz-4.15.0-1024-oem.efi.signed root=UUID=df0da40a-01d2-4405-bff6-892d2d41959b ro mem_sleep_default=deep usbcore.quirks=2386:3119:k quiet splash $vt_handoff
        initrd /boot/initrd.img-4.15.0-1024-oem
    }
    menuentry 'Ubuntu, with Linux 4.15.0-1024-oem (recovery mode) (on /dev/nvme0n1p3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.15.0-1024-oem.efi.signed-root=UUID=df0da40a-01d2-4405-bff6-892d2d41959b ro recovery nomodeset mem_sleep_default=deep usbcore.quirks=2386:3119:k-df0da40a-01d2-4405-bff6-892d2d41959b' {
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  df0da40a-01d2-4405-bff6-892d2d41959b
        else
          search --no-floppy --fs-uuid --set=root df0da40a-01d2-4405-bff6-892d2d41959b
        fi
        linux /boot/vmlinuz-4.15.0-1024-oem.efi.signed root=UUID=df0da40a-01d2-4405-bff6-892d2d41959b ro recovery nomodeset mem_sleep_default=deep usbcore.quirks=2386:3119:k
        initrd /boot/initrd.img-4.15.0-1024-oem
    }
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


### BEGIN /etc/grub.d/99_dell_recovery ###
menuentry "Restore OS to factory state" {
        search --no-floppy --hint '(hd0,gpt2)' --set --fs-uuid 7E4E-9349
        set uuid_options="uuid=7E4E-9349"
        if [ -s /factory/common.cfg ]; then
            source /factory/common.cfg
        else
            set options="boot=casper automatic-ubiquity noprompt quiet splash nomodeset"
        fi
        if [ -s /factory/post-rts-gfx.cfg ]; then
            source /factory/post-rts-gfx.cfg
        fi
        if [ -s /factory/post-rts-wlan.cfg ]; then
            source /factory/post-rts-wlan.cfg
        fi
        #Support starting from a loopback mount (Only support ubuntu.iso for filename)
        if [ -f /ubuntu.iso ]; then
            loopback loop /ubuntu.iso
            set root=(loop)
            set options="iso-scan/filename=/ubuntu.iso $options"
        fi
        if [ -n "${lang}" ]; then
            set options="locale=$lang $options"
        fi
        if [ -s /factory/dual_enable ]; then
            set options="dell-recovery/dual_boot=true $options"
        fi 


        linux   /casper/vmlinuz.efi dell-recovery/recovery_type=hdd $uuid_options $options
    initrd    /casper/initrd.lz
}
### END /etc/grub.d/99_dell_recovery ###

```

How can I change the name?

---

### Post by oldfred on 2019-08-24
You can use Disks to change labels.

Good, not sure why Boot-Repair's report did not show the grub menu.
Menu shows that you can also boot the install on p3.

Is the install on p3, your original install? Report showed it had more data than install in p4.
If you change label, can you click on that partition and mount it? Does it then show your data.
If so before anything else back up your data to another flash drive or external drive or some other device.

---

### Post by yaronshemeshnew on 2019-08-24
I installed the Ubuntu side by side, maybe that is why.

I can send you the images I pictured so you can understand more.

---

### Post by yaronshemeshnew on 2019-08-24
Do I need to follow this guide?

[https://www.tecmint.com/change-modify-linux-disk-partition-label-names/](https://www.tecmint.com/change-modify-linux-disk-partition-label-names/)

To be honest, I don't know what to do and what i'm doing. I'm a totally beginner in Ubuntu.  
Can I click on the recommended repair and it will solve the issue?

Thank you.

---

### Post by oldfred on 2019-08-24
Your link also shows using Disks which I find the easier gui way.
The command line ways also work.

Know nothing about R-Linux.
Need to know if from your install after you relabel it, will it mount. You may then just need to use new install to copy data from old install.

---

### Post by yaronshemeshnew on 2019-08-24
I mounted the partition3 but I still see it's not mounted.

And for the dok also, I don't have access to it.

---

### Post by oldfred on 2019-08-24
Make sure it then is unmounted and run fsck on it.

Not as familiar with NVMe drives, but think you need to replace /dev/sdb1 in example with /dev/nvme0n1p3, your parted output should show the device correctly.


            To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by yaronshemeshnew on 2019-08-24
I checked the partition 2 (Microsoft Reserved) and partition3  and they need to be repaired.
The partition 4 is busy..
Can I fix them from Disks using Repair FIle System buttin?
Thank you very much

---

### Post by oldfred on 2019-08-24
The fsck is only for ext4 formatted partitions.
If you need to repair Windows NTFS you have to use chkdsk from Windows. And You have to boot into repair console or check something to have it run chkdsk on reboot. 

And the Microsoft reserved is an unformatted partition. You cannot repair it.
And you can only run fsck on unmounted partitions, so cannot run on p4 as you have booted into it. You can use live installer or boot recovery mode & run before mounting partition. But I think someone said it defaults to mounted now. Have not used it, so do not know.

Can from grub menu you boot your install in p3 as shown in grub menu? Or what error messages.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) &

---

