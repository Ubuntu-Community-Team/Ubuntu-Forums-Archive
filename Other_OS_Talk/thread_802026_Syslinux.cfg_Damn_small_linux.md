---
title: "Syslinux.cfg Damn small linux"
date: 2008-05-21
forum: Other OS Talk
---

### Post by reyhan on 2008-05-21
i want to convert the Syslinux.cfg to grub menu boot
but i confused:confused::confused::confused:

```
DEFAULT linux24
APPEND ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 initrd=minirt24.gz nomce noapic qemu quiet BOOT_IMAGE=knoppix frugal
TIMEOUT 300

PROMPT 1
DISPLAY boot.msg
F1 boot.msg
F2 f2
F3 f3
LABEL dsl
KERNEL linux24
APPEND ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 initrd=minirt24.gz nomce noapic qemu quiet BOOT_IMAGE=knoppix frugal
LABEL knoppix-txt
KERNEL linux24
APPEND ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=normal initrd=minirt24.gz nomce noapic qemu quiet BOOT_IMAGE=knoppix frugal
LABEL expert
KERNEL linux24
APPEND ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 initrd=minirt24.gz nomce noapic BOOT_IMAGE=expert frugal
LABEL fb1280x1024
KERNEL linux24
APPEND ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=794 xmodule=fbdev initrd=minirt24.gz nomce noapic qemu quiet BOOT_IMAGE=knoppix frugal
LABEL fb1024x768
KERNEL linux24
APPEND ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 xmodule=fbdev initrd=minirt24.gz nomce noapic qemu quiet BOOT_IMAGE=knoppix frugal
LABEL fb800x600
KERNEL linux24
APPEND ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=788 xmodule=fbdev initrd=minirt24.gz nomce noapic qemu quiet BOOT_IMAGE=knoppix frugal
LABEL failsafe
KERNEL linux24
APPEND ramdisk_size=100000 init=/etc/init lang=us vga=normal atapicd nosound noapic noacpi acpi=off noscsi noapm nousb nopcmcia nofirewire noagp nomce nodhcp xmodule=vesa initrd=minirt24.gz BOOT_IMAGE=knoppix frugal
LABEL userdef
KERNEL linux24
APPEND ###############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################
```

---

### Post by kerry_s on 2008-05-21
what? grub is a different program, you can't just change 1 program into another. you have to install grub if you want grub.

---

