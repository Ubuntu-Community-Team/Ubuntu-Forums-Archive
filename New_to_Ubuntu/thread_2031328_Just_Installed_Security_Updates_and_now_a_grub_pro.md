---
title: "Just Installed Security Updates and now a grub problem what's wrong?"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by dynosis on 2012-07-21
i just installed security updates including upgrading firefox to 14.01. all is well except for grub, i can't boot into updated generic kernel 3.0.0.23
please help? thank you

```
insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root f069f1c3-5098-46c2-83fe-495e402b2e27
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
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
menuentry 'Ubuntu, with Linux 3.0.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root f069f1c3-5098-46c2-83fe-495e402b2e27
    linux    /boot/vmlinuz-3.0.0-23-generic root=UUID=f069f1c3-5098-46c2-83fe-495e402b2e27 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root f069f1c3-5098-46c2-83fe-495e402b2e27
    echo    'Loading Linux 3.0.0-23-generic ...'
    linux    /boot/vmlinuz-3.0.0-23-generic root=UUID=f069f1c3-5098-46c2-83fe-495e402b2e27 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-23-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root f069f1c3-5098-46c2-83fe-495e402b2e27
    linux    /boot/vmlinuz-3.0.0-22-generic root=UUID=f069f1c3-5098-46c2-83fe-495e402b2e27 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-22-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root f069f1c3-5098-46c2-83fe-495e402b2e27
    echo    'Loading Linux 3.0.0-22-generic ...'
    linux    /boot/vmlinuz-3.0.0-22-generic root=UUID=f069f1c3-5098-46c2-83fe-495e402b2e27 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-22-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root f069f1c3-5098-46c2-83fe-495e402b2e27
    linux    /boot/vmlinuz-3.0.0-21-generic root=UUID=f069f1c3-5098-46c2-83fe-495e402b2e27 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-21-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root f069f1c3-5098-46c2-83fe-495e402b2e27
    echo    'Loading Linux 3.0.0-21-generic ...'
    linux    /boot/vmlinuz-3.0.0-21-generic root=UUID=f069f1c3-5098-46c2-83fe-495e402b2e27 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-21-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root f069f1c3-5098-46c2-83fe-495e402b2e27
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=f069f1c3-5098-46c2-83fe-495e402b2e27 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root f069f1c3-5098-46c2-83fe-495e402b2e27
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=f069f1c3-5098-46c2-83fe-495e402b2e27 ro recovery nomodeset 
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root f069f1c3-5098-46c2-83fe-495e402b2e27
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root f069f1c3-5098-46c2-83fe-495e402b2e27
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 24C4A1E3C4A1B806
    chainloader +1
}
menuentry "linux (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root eebc7e44-5f04-4441-bcf9-b1f76c525de4
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=eebc7e44-5f04-4441-bcf9-b1f76c525de4 nokmsboot logo.nologo quiet resume=UUID=ba5a05e2-2229-4e4c-93b3-7d5c9478a33c splash=silent vga=788
    initrd (hd0,1)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root eebc7e44-5f04-4441-bcf9-b1f76c525de4
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=eebc7e44-5f04-4441-bcf9-b1f76c525de4 nokmsboot resume=UUID=ba5a05e2-2229-4e4c-93b3-7d5c9478a33c
    initrd (hd0,1)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root eebc7e44-5f04-4441-bcf9-b1f76c525de4
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=eebc7e44-5f04-4441-bcf9-b1f76c525de4 nokmsboot failsafe
    initrd (hd0,1)/boot/initrd.img
}
menuentry "linux (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root bcdb9132-8efb-4dcc-968c-1412cb3af379
    linux /boot/vmlinuz root=/dev/sda5 ro vga = normal append = "
}
menuentry "linux-tui (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root bcdb9132-8efb-4dcc-968c-1412cb3af379
    linux /boot/vmlinuz root=/dev/sda5 ro append = "2 
}
menuentry "linux-gui (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root bcdb9132-8efb-4dcc-968c-1412cb3af379
    linux /boot/vmlinuz root=/dev/sda5 ro append = "4 
}
menuentry "3.2.16 (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root bcdb9132-8efb-4dcc-968c-1412cb3af379
    linux /boot/vmlinuz-3.2.16 root=/dev/sda5 ro append = "
}
menuentry "3.3.4 (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root bcdb9132-8efb-4dcc-968c-1412cb3af379
    linux /boot/vmlinuz-3.3.4 root=/dev/sda5 ro append = "
}
menuentry "Slackware Linux (Slackware 13.37.0) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root bcdb9132-8efb-4dcc-968c-1412cb3af379
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd
}
menuentry "Slackware Linux (Slackware 13.37.0) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root bcdb9132-8efb-4dcc-968c-1412cb3af379
    linux /boot/vmlinuz root=/dev/sda5
    initrd /boot/initrd
}
menuentry "Slackware Linux (Slackware 13.37.0) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root bcdb9132-8efb-4dcc-968c-1412cb3af379
    linux /boot/vmlinuz-3.0.8 root=/dev/sda5
}
menuentry "Slackware Linux (Slackware 13.37.0) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root bcdb9132-8efb-4dcc-968c-1412cb3af379
    linux /boot/vmlinuz-3.2.16 root=/dev/sda5
}
menuentry "Slackware Linux (Slackware 13.37.0) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root bcdb9132-8efb-4dcc-968c-1412cb3af379
    linux /boot/vmlinuz-3.3.4 root=/dev/sda5
}
menuentry "MEPIS at sda6, newest kernel (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6e3a0244-59c7-4447-b577-ef93c2987cde
    linux /boot/vmlinuz root=/dev/sda6 nomce quiet splash vga=788 nomodeset nouveau.modeset=0
    initrd /boot/initrd.img
}
menuentry "MEPIS at sda6, kernel 2.6.36-1-mepis-smp (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6e3a0244-59c7-4447-b577-ef93c2987cde
    linux /boot/vmlinuz-2.6.36-1-mepis-smp root=/dev/sda6 nomce quiet splash vga=788 nomodeset nouveau.modeset=0
    initrd /boot/initrd.img-2.6.36-1-mepis-smp
}
menuentry "MEPIS 11.0 (upgradable from Debian Squeeze) (11.0) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6e3a0244-59c7-4447-b577-ef93c2987cde
    linux /boot/vmlinuz root=/dev/sda5 nomodeset nouveau.modeset=0
    initrd /boot/initrd
}
menuentry "linux (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6e3a0244-59c7-4447-b577-ef93c2987cde
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=9278a018-c9d9-4f72-a0c3-758652ae0cac quiet nokmsboot vmalloc=256M acpi=on resume=UUID=eacc0aee-782d-4425-9206-59051051dbbe splash=silent vga=788 nomodeset nouveau.modeset=0
    initrd (hd2,5)/boot/initrd.img
}
menuentry "MEMTEST (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6e3a0244-59c7-4447-b577-ef93c2987cde
    linux /boot/memtest86+.bin 
}
menuentry "Fuduntu 2012 (Punny Name Serious Distro) (3.4.4-1.fu2012.i686) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 87d4cdcd-8db9-4def-b045-0295bf63dfae
    linux /boot/vmlinuz-3.4.4-1.fu2012.i686 ro root=UUID=87d4cdcd-8db9-4def-b045-0295bf63dfae rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-3.4.4-1.fu2012.i686.img
}
menuentry "Fuduntu 2012 (Punny Name Serious Distro) (3.4.2-1.fu2012.i686) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 87d4cdcd-8db9-4def-b045-0295bf63dfae
    linux /boot/vmlinuz-3.4.2-1.fu2012.i686 ro root=UUID=87d4cdcd-8db9-4def-b045-0295bf63dfae rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-3.4.2-1.fu2012.i686.img
}
menuentry "Fuduntu 2012 (Punny Name Serious Distro) (3.2.18-2.fu2012.i686) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 87d4cdcd-8db9-4def-b045-0295bf63dfae
    linux /boot/vmlinuz-3.2.18-2.fu2012.i686 ro root=UUID=87d4cdcd-8db9-4def-b045-0295bf63dfae rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-3.2.18-2.fu2012.i686.img
}
menuentry "Ubuntu, with Linux 3.2.0-26-generic (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 041b9b15-e7a7-4f2f-bbdd-0d796b7fc0d7
    linux /boot/vmlinuz-3.2.0-26-generic root=UUID=041b9b15-e7a7-4f2f-bbdd-0d796b7fc0d7 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-26-generic
}
menuentry "Ubuntu, with Linux 3.2.0-26-generic (recovery mode) (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 041b9b15-e7a7-4f2f-bbdd-0d796b7fc0d7
    linux /boot/vmlinuz-3.2.0-26-generic root=UUID=041b9b15-e7a7-4f2f-bbdd-0d796b7fc0d7 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-26-generic
}
menuentry "Ubuntu, with Linux 3.2.0-25-generic (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 041b9b15-e7a7-4f2f-bbdd-0d796b7fc0d7
    linux /boot/vmlinuz-3.2.0-25-generic root=UUID=041b9b15-e7a7-4f2f-bbdd-0d796b7fc0d7 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-25-generic
}
menuentry "Ubuntu, with Linux 3.2.0-25-generic (recovery mode) (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 041b9b15-e7a7-4f2f-bbdd-0d796b7fc0d7
    linux /boot/vmlinuz-3.2.0-25-generic root=UUID=041b9b15-e7a7-4f2f-bbdd-0d796b7fc0d7 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-25-generic
}
menuentry "Ubuntu, with Linux 3.0.0-21-generic (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 041b9b15-e7a7-4f2f-bbdd-0d796b7fc0d7
    linux /boot/vmlinuz-3.0.0-21-generic root=UUID=041b9b15-e7a7-4f2f-bbdd-0d796b7fc0d7 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.0.0-21-generic
}
menuentry "Ubuntu, with Linux 3.0.0-21-generic (recovery mode) (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 041b9b15-e7a7-4f2f-bbdd-0d796b7fc0d7
    linux /boot/vmlinuz-3.0.0-21-generic root=UUID=041b9b15-e7a7-4f2f-bbdd-0d796b7fc0d7 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-21-generic
}
menuentry "linux (on /dev/sdc6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos6)'
    search --no-floppy --fs-uuid --set=root 9278a018-c9d9-4f72-a0c3-758652ae0cac
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=9278a018-c9d9-4f72-a0c3-758652ae0cac quiet nokmsboot vmalloc=256M acpi=on resume=UUID=eacc0aee-782d-4425-9206-59051051dbbe splash=silent vga=788
    initrd (hd2,5)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdc6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos6)'
    search --no-floppy --fs-uuid --set=root 9278a018-c9d9-4f72-a0c3-758652ae0cac
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=9278a018-c9d9-4f72-a0c3-758652ae0cac quiet nokmsboot vmalloc=256M acpi=on resume=UUID=eacc0aee-782d-4425-9206-59051051dbbe
    initrd (hd2,5)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdc6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos6)'
    search --no-floppy --fs-uuid --set=root 9278a018-c9d9-4f72-a0c3-758652ae0cac
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=9278a018-c9d9-4f72-a0c3-758652ae0cac quiet nokmsboot failsafe vmalloc=256M acpi=on
    initrd (hd2,5)/boot/initrd.img
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
dynosis@MS-6712:~$ 

```

---

### Post by NikTh on 2012-07-21
Hi , 
can you boot from another kernel ? (e.g 
3.0.0-21-generic) 

If yes boot from there and open a terminal and run these commands 
```
sudo update-initramfs -u -k 3.0.0-23-generic
sudo update-grub
```If you cannot boot from any kernel , then boot form a live CD / Usb and install an automatic tool which help you to repair boot.
Take a look at here --> [_**[COLOR=Black]Boot-Repair[/COLOR]**_]("http://ubuntuforums.org/showthread.php?t=1769482")

Thanks

---

### Post by dynosis on 2012-07-21
thank you for your reply i am doing what you said as i write will reboot and let you know

---

### Post by dynosis on 2012-07-21
i copy paste what you wrote and rebooted . did not work i see all previous versions ,just 3.0.023 can't boot into it? only boot into 3.0.0.22 any further suggestions i would appreciate

---

### Post by NikTh on 2012-07-21
Hi , 
boot from a working kernel (like 3.0.0.22) , open a terminal and give the results of this command
```
sudo update-initramfs -c -v -k 3.0.0-23-generic
```[B]Put the results inside [CODE] tags , by highlighting the text and click # symbol , on top of message pane.
[/B] 
Thanks

---

### Post by dynosis on 2012-07-21
```
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/skge.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/depca.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/smsc9420.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/ni52.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/smc-mca.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/sc92031.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/hp100.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/defxx.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/sunhme.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/ixgb/ixgb.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/ixgbevf/ixgbevf.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/lp486e.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/yellowfin.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/cs89x0.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/qla3xxx.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/ns83820.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/chelsio/cxgb.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/ixgbe/ixgbe.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/stmmac/stmmac.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/3c523.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/tehuti.ko
Adding binary /lib/firmware/3.0.0-23-generic/tehuti/bdx.bin
Adding firmware tehuti/bdx.bin
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/3c501.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/skfp/skfp.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/3c59x.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/smc-ultra.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/netxen/netxen_nic.ko
Adding binary /lib/firmware/phanfw.bin
Adding firmware phanfw.bin
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/epic100.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/enic/enic.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/de620.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/de600.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/acenic.ko
Adding binary /lib/firmware/3.0.0-23-generic/acenic/tg2.bin
Adding firmware acenic/tg2.bin
Adding binary /lib/firmware/3.0.0-23-generic/acenic/tg1.bin
Adding firmware acenic/tg1.bin
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/ks8851.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/3c527.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/rrunner.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/eql.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/via-velocity.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/vmxnet3/vmxnet3.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/smc9194.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/pcnet32.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/cxgb4/cxgb4.ko
Adding binary /lib/firmware/cxgb4/t4fw.bin
Adding firmware cxgb4/t4fw.bin
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/i2c/algos/i2c-algo-bit.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mtd/mtd.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/sfc/sfc.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/eth16i.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/ks8842.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/niu.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/ppp_deflate.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/r6040.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/bsd_comp.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/uio/uio.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/cnic.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/bnx2.ko
Adding binary /lib/firmware/3.0.0-23-generic/bnx2/bnx2-rv2p-09ax-6.0.17.fw
Adding firmware bnx2/bnx2-rv2p-09ax-6.0.17.fw
Adding binary /lib/firmware/3.0.0-23-generic/bnx2/bnx2-rv2p-09-6.0.17.fw
Adding firmware bnx2/bnx2-rv2p-09-6.0.17.fw
Adding binary /lib/firmware/3.0.0-23-generic/bnx2/bnx2-mips-09-6.2.1a.fw
Adding firmware bnx2/bnx2-mips-09-6.2.1a.fw
Adding binary /lib/firmware/3.0.0-23-generic/bnx2/bnx2-rv2p-06-6.0.15.fw
Adding firmware bnx2/bnx2-rv2p-06-6.0.15.fw
Adding binary /lib/firmware/3.0.0-23-generic/bnx2/bnx2-mips-06-6.2.1.fw
Adding firmware bnx2/bnx2-mips-06-6.2.1.fw
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/3c515.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ssb/ssb.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/b44.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/net/ipv4/gre.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/pptp.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/jme.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/sungem.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/atlx/atl2.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/atlx/atl1.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/ppp_mppe.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/3c509.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/3c503.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/veth.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/lance.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/sis900.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/atp.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/forcedeth.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/sis190.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/smc-ultra32.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/r8169.ko
Adding binary /lib/firmware/rtl_nic/rtl8105e-1.fw
Adding firmware rtl_nic/rtl8105e-1.fw
Adding binary /lib/firmware/rtl_nic/rtl8168e-2.fw
Adding firmware rtl_nic/rtl8168e-2.fw
Adding binary /lib/firmware/rtl_nic/rtl8168e-1.fw
Adding firmware rtl_nic/rtl8168e-1.fw
Adding binary /lib/firmware/rtl_nic/rtl8168d-2.fw
Adding firmware rtl_nic/rtl8168d-2.fw
Adding binary /lib/firmware/rtl_nic/rtl8168d-1.fw
Adding firmware rtl_nic/rtl8168d-1.fw
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/atl1c/atl1c.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/qlcnic/qlcnic.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/8139too.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/net/cassini.ko
Adding binary /lib/firmware/3.0.0-23-generic/sun/cassini.bin
Adding firmware sun/cassini.bin
Copying module directory kernel/drivers/scsi
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/scsi_tgt.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/scsi_transport_fc.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/bfa/bfa.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/scsi_transport_spi.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/g_NCR5380_mmio.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/initio.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/megaraid.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/BusLogic.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/53c700.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/sim710.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/g_NCR5380.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/in2000.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/ibmmca.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/scsi_debug.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/aha1542.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/imm.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/fd_mcs.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/libfc/libfc.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/fcoe/libfcoe.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/bnx2fc/bnx2fc.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/scsi_wait_scan.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/advansys.ko
Adding binary /lib/firmware/3.0.0-23-generic/advansys/38C1600.bin
Adding firmware advansys/38C1600.bin
Adding binary /lib/firmware/3.0.0-23-generic/advansys/38C0800.bin
Adding firmware advansys/38C0800.bin
Adding binary /lib/firmware/3.0.0-23-generic/advansys/3550.bin
Adding firmware advansys/3550.bin
Adding binary /lib/firmware/3.0.0-23-generic/advansys/mcode.bin
Adding firmware advansys/mcode.bin
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/st.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/libiscsi.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/scsi_transport_sas.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/libsas/libsas.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko
Adding binary /lib/firmware/aic94xx-seq.fw
Adding firmware aic94xx-seq.fw
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/fdomain.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/hptiop.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/ch.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/tmscsim.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/scsi_transport_srp.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/osst.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/eata.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/NCR_D700.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/libiscsi_tcp.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/cxgbi/libcxgbi.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/cxgbi/cxgb3i/cxgb3i.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/cxgbi/cxgb4i/cxgb4i.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/bnx2i/bnx2i.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/3w-xxxx.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/NCR_Q720_mod.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/iscsi_tcp.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/fnic/fnic.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/dc395x.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/pcmcia/pcmcia_core.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/pcmcia/pcmcia.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/qlogicfas408.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/atp870u.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/qla1280.ko
Adding binary /lib/firmware/3.0.0-23-generic/qlogic/12160.bin
Adding firmware qlogic/12160.bin
Adding binary /lib/firmware/3.0.0-23-generic/qlogic/1280.bin
Adding firmware qlogic/1280.bin
Adding binary /lib/firmware/3.0.0-23-generic/qlogic/1040.bin
Adding firmware qlogic/1040.bin
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/aha152x.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/ppa.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/lpfc/lpfc.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/sym53c416.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/3w-9xxx.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/qlogicfas.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/stex.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/hpsa.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/osd/libosd.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/osd/osd.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/vmw_pvscsi.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/ipr.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/t128.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/iscsi_boot_sysfs.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/be2iscsi/be2iscsi.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/pm8001/pm8001.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/mvsas/mvsas.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/isci/isci.ko
Adding binary /lib/firmware/3.0.0-23-generic/isci/isci_firmware.bin
Adding firmware isci/isci_firmware.bin
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/fcoe/fcoe.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/NCR53c406a.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/aha1740.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
Adding binary /lib/firmware/ql2500_fw.bin
Adding firmware ql2500_fw.bin
Adding binary /lib/firmware/ql2400_fw.bin
Adding firmware ql2400_fw.bin
Adding binary /lib/firmware/ql2322_fw.bin
Adding firmware ql2322_fw.bin
Adding binary /lib/firmware/ql2300_fw.bin
Adding firmware ql2300_fw.bin
Adding binary /lib/firmware/ql2200_fw.bin
Adding firmware ql2200_fw.bin
Adding binary /lib/firmware/ql2100_fw.bin
Adding firmware ql2100_fw.bin
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/dmx3191d.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/aacraid/aacraid.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/misc/enclosure.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/ses.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/ips.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/dtc.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/raid_class.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/wd7000.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/u14-34f.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/pas16.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/gdth.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/nsp32.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/mpt2sas/mpt2sas.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/ultrastor.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/device_handler/scsi_dh_hp_sw.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/device_handler/scsi_dh_rdac.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/device_handler/scsi_dh_emc.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/device_handler/scsi_dh_alua.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/libsrp.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/a100u2w.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/3w-sas.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/dpt_i2o.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/scsi/pmcraid.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/message/fusion/mptbase.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/message/fusion/mptscsih.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/message/fusion/mptfc.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/message/fusion/mptsas.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/message/fusion/mptspi.ko
Copying module directory kernel/drivers/block
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/nbd.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/paride.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/pf.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/pg.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/epat.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/bpck6.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/frpw.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/on26.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/epia.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/pt.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/friq.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/kbic.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/comm.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/bpck.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/pd.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/ktti.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/aten.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/fit3.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/on20.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/fit2.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/dstr.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/paride/pcd.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/DAC960.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/sx8.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/cpqarray.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/umem.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/lib/lru_cache.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/drbd/drbd.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/cciss.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/pktcdvd.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/virtio_blk.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/net/ceph/libceph.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/rbd.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/aoe/aoe.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/cryptoloop.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/floppy.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/block/osdblk.ko
Copying module directory kernel/drivers/ata
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_amd.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_platform.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_it8213.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_pdc2027x.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/sata_qstor.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_ninja32.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_ns87410.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_sil680.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_atp867x.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_cs5536.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/sata_sx4.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_oldpiix.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_ns87415.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_mpiix.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_sch.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_hpt37x.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_it821x.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/libahci.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/acard-ahci.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/sata_uli.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_sl82c105.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/sata_promise.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_artop.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_isapnp.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_qdi.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_pdc202xx_old.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/sata_mv.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/sata_sis.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_atiixp.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_opti.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_efar.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_rdc.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_cypress.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_jmicron.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/sata_sil24.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/sata_inic162x.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/ahci_platform.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_legacy.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_radisys.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_sc1200.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_hpt366.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_pcmcia.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/sata_sil.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_cmd640.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_arasan_cf.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_optidma.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_triflex.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/sata_svw.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_cs5535.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_cs5520.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/sata_vsc.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_marvell.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_ali.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_cs5530.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_hpt3x2n.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_rz1000.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_netcell.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_via.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_serverworks.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/sata_nv.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/ahci.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_hpt3x3.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/sata_via.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/ata/pata_cmd64x.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/message/i2o/i2o_core.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/message/i2o/i2o_block.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/firewire/firewire-core.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/firewire/firewire-ohci.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/firewire/firewire-sbp2.ko
Copying module directory kernel/drivers/mmc
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mmc/card/sdio_uart.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mmc/card/mmc_block.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mmc/host/via-sdmmc.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mmc/host/sdhci.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mmc/host/sdhci-pci.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/misc/tifm_core.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mmc/host/tifm_sd.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mmc/host/sdhci-of.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mmc/host/sdhci-platform.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mmc/host/wbsd.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mmc/host/ushc.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mmc/host/vub300.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/misc/cb710/cb710.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mmc/host/cb710-mmc.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/mmc/host/sdricoh_cs.ko
Copying module directory kernel/drivers/usb/storage
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/usb-storage.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/ums-alauda.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/ums-datafab.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/ums-sddr09.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/ums-onetouch.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/ums-freecom.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/ums-usbat.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/uas.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/ums-eneub6250.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/ums-realtek.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/ums-cypress.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/ums-isd200.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/ums-karma.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/ums-jumpshot.ko
Adding module /lib/modules/3.0.0-23-generic/kernel/drivers/usb/storage/ums-sddr55.ko
Adding binary /etc/initramfs-tools/conf.d/resume
Adding binary /usr/lib/initramfs-tools/bin/wait-for-root
Adding library /lib/i386-linux-gnu/libudev.so.0
Adding library /lib/i386-linux-gnu/libc.so.6
Adding library /lib/i386-linux-gnu/librt.so.1
Adding library /lib/ld-linux.so.2
Adding library /lib/i386-linux-gnu/libpthread.so.0
Adding binary /sbin/modprobe
Adding binary /sbin/rmmod
Adding binary /sbin/blkid
Adding library /lib/i386-linux-gnu/libblkid.so.1
Adding library /lib/i386-linux-gnu/libuuid.so.1
Calling hook compcache
Calling hook fixrtc
Adding binary /bin/date
Adding binary /sbin/hwclock
Adding binary /sbin/dumpe2fs
Adding library /lib/i386-linux-gnu/libext2fs.so.2
Adding library /lib/i386-linux-gnu/libcom_err.so.2
Adding library /lib/i386-linux-gnu/libe2p.so.2
Calling hook fuse_utils
Adding binary /sbin/mount.fuse
Calling hook klibc
Calling hook mountall
Calling hook thermal
Calling hook udev
Adding binary /usr/bin/pkill
Adding library /lib/libproc-3.2.8.so
Adding binary /sbin/udevd
Adding library /lib/i386-linux-gnu/libselinux.so.1
Adding library /lib/i386-linux-gnu/libdl.so.2
Adding binary /sbin/udevadm
Adding binary /lib/udev/firmware
Adding binary /lib/udev/ata_id
Adding binary /lib/udev/usb_id
Adding binary /sbin/blkid
Adding binary /lib/udev/scsi_id
Adding binary /lib/udev/path_id
Adding binary /lib/udev/input_id
Calling hook ntfs_3g
Adding binary /bin/ntfs-3g
Adding library /lib/libfuse.so.2
Adding library /lib/libntfs-3g.so.814
Calling hook console_setup
Calling hook kbd
Adding binary /bin/setfont
Adding binary /bin/kbd_mode
Adding binary /bin/loadkeys
Calling hook busybox
Adding binary /usr/lib/initramfs-tools/bin/busybox
Calling hook dmsetup
Adding binary /sbin/dmsetup
Adding library /lib/libdevmapper.so.1.02.1
Building cpio /boot/initrd.img-3.0.0-23-generic.new initramfs
dynosis@MS-6712:~$ 

```

---

### Post by dynosis on 2012-07-21
i hope i did above right . sorry if i didn't  but thanks a lot for helping me

---

### Post by dynosis on 2012-07-21
i thought this may help from grub.cfg:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-23-generic
Found initrd image: /boot/initrd.img-3.0.0-23-generic
Found linux image: /boot/vmlinuz-3.0.0-22-generic
Found initrd image: /boot/initrd.img-3.0.0-22-generic
Found linux image: /boot/vmlinuz-3.0.0-21-generic
Found initrd image: /boot/initrd.img-3.0.0-21-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Mandriva Linux 2011.0 (2011.0) on /dev/sda2
Found Slackware Linux (Slackware 13.37.0) on /dev/sda5
Found MEPIS 11.0 (upgradable from Debian Squeeze) (11.0) on /dev/sda6
Found Fuduntu 2012 (Punny Name Serious Distro) on /dev/sda7
Found Ubuntu 12.04 LTS (12.04) on /dev/sdc1
Found PCLinuxOS on /dev/sdc6
error: out of memory.
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 460
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
dynosis@MS-6712:~$ 

```

---

### Post by NikTh on 2012-07-21
> **dynosis said:**
> i hope i did above right . sorry if i didn't  but thanks a lot for helping me

Hi, 
yes you did this correct. I cannot see anything wrong with new initramfs generation. 
Try one more time to boot from the new kernel , and if stacks , hit "Esc" key to see some messages that might help us. 

What is your graphics card ? 
Open a terminal and give the results of this command 
```
lspci -nnk | grep -iA2 vga
```It is always a way , that you can re-install the kernel .. with this command 
```
sudo apt-get install --reinstall linux-image-3.0.0-23-generic linux-headers-3.0.0-23-generic
```if you want to give it a try. 

Also..
We can search it more , by examine some logs. 
You can open a terminal and give these commands 
```
gedit /var/log/dmesg.0 
gedit /var/log/Xorg.0.log
```So we can search for issues. 

Maybe its not the kernel . Maybe its  lightdm , or graphics , or Desktop Environment. 

Thanks

---

### Post by drs305 on 2012-07-21
The initrd generation appears to be completing without problems, however your GRUB update is not completing correctly and thus does not really update the GRUB menu. (See the last lines of the update-grub command you posted).

The bad news is that your original GRUB menu, which appears to be OK, should still be used and probably should boot the kernel.

What kind of errors are you getting when you boot -23? i.e. where is it failing and what is the error message you get?

Since you are getting a GRUB error which needs fixing at some point even if it's not the problem, please install Boot Repair, run it and then if things are still broken post a link to the boot info script it generates.

See my sig line for a Boot Repair link.

---

### Post by dynosis on 2012-07-21
did you check the grub.cfg output file? there are errors in there i did not have previously. just a suggestion. but i will try your suggestions and get back at you thanks

---

### Post by NikTh on 2012-07-21
> **dynosis said:**
> did you check the grub.cfg output file? there are errors in there i did not have previously. just a suggestion. but i will try your suggestions and get back at you thanks

Hi.. 
Yes you have right.. I didn't see that. Sorry. 

I thought that you already tried my suggestion at post #2 (with boot-repair) , if not , try it please. 

Thanks

---

### Post by dynosis on 2012-07-21
thank you very much for your help. it is something to do with my sda. it looks like sda8 got pushed before sda7 , this messed up beginning and ending sector/blocks. anyway thanks again. i think i will try to copy my ubuntu freeup disk and fix thr order od sda's. 
bye thanks again

---

### Post by dynosis on 2012-07-21
thank you very much for your help. it is something to do with my sda. it looks like sda8 got pushed before sda7 , this messed up beginning and ending sector/blocks. anyway thanks again. i think i will try to copy my ubuntu freeup disk and fix the order of the sda's. 
bye thanks again

---

