---
title: "Boot from disk image"
date: 2020-03-18
forum: New to Ubuntu
---

### Post by syn0ptic on 2020-03-18
Hi there and sorry if I placed my post into a wrong forum!

I installed a fresh Ubuntu and captured the whole drive with ```
[COLOR=#000000]sudo dd if=/dev/sda of=/dev/sdb/image.img[/COLOR]
``` after it I placed it into ```
/boot/images/[COLOR=#000000]image.img[/COLOR]
``` I wanna make GRUB2 to boot from this image like Windows does with "native boot" technology from VHDX.

I copied memdisk into /boot with ```
cp /usr/lib/syslinux/memdisk /boot/
```
Created new file 50_memdisk ```
/etc/grub.d/50_memdisk
``` with such content:
```
#!/bin/sh
set -e
IMAGES=/boot/images
. /usr/lib/grub/grub-mkconfig_lib
if test -e /boot/memdisk ; then
 MEMDISKPATH=$( make_system_path_relative_to_its_root "/boot/memdisk" )
 echo "Found memdisk: $MEMDISKPATH" >&2
 find $IMAGES -name "*.img" | sort | 
 while read image ; do
 IMAGEPATH=$( make_system_path_relative_to_its_root "$image" )
 echo "Found floppy image: $IMAGEPATH" >&2
 cat << EOF
menuentry "Bootable floppy: $(basename $IMAGEPATH | sed s/.img//)" {
EOF
 prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/"
 cat << EOF
 linux16 $MEMDISKPATH bigraw
 initrd16 $IMAGEPATH
}
EOF
 done
fi
```

then I run ```

chmod +x /etc/grub.d/50_memdisk
update-grub
```



But Grub2 while the boot process is returning "out of memory"

What do I do wrong?

THANK YOU!

---

### Post by TheFu on 2020-03-18
How big is image.img?
How much RAM does the system have?

---

### Post by syn0ptic on 2020-03-19
> **TheFu said:**
> How big is image.img?
How much RAM does the system have?
I anticipated this question. 16Gb RAM 60Gb hard drive image.
But is it possible to boot it somehow without increasing RAM amount? Maybe I can extract the only files needed for Ubuntu boot process and compress them into separate IMG<16Gb /sda, boot from it and mount the rest as the another device /sdb?
Or is it possible to boot from live ISO having separate image (IMG or ISO) which stores all system changes including installed applications and /home etc? Mb it can be done with OverlayFS or smth?

---

### Post by TheFu on 2020-03-19
> **syn0ptic said:**
> I anticipated this question. 16Gb RAM 60Gb hard drive image.
1) But is it possible to boot it somehow without increasing RAM amount? 
2) Maybe I can extract the only files needed for Ubuntu boot process and compress them into separate IMG<16Gb /sda, boot from it and mount the rest as the another device /sdb?
3) Or is it possible to boot from live ISO having separate image (IMG or ISO) which stores all system changes including installed applications and /home etc? 
4) Mb it can be done with OverlayFS or smth?

1. Yes.  Do a proper  install or follow existing solutions for qemu.
2. Perhaps. idk.
3. See 2.
4. See 3.

QEMU - boot iso: [https://en.wikibooks.org/wiki/QEMU/Images](https://en.wikibooks.org/wiki/QEMU/Images)
Images and ISOs are read-only.  If you'd like stuff saved between boots, then you'll need to make that happen.  Other distros like tinycore are
a) smaller 16MB for a GUi
b) designed to have addons easily added to a master image

Just booted a tinycore:
```
$ qemu-system-x86_64 ./TinyCore-current.iso
```
it was slower than using KVM.  Booting under KVM is less than 2 sec, worst case.  At shutdown, tinycore asks what you'd like to save.

---

### Post by syn0ptic on 2020-03-24
> **TheFu said:**
> 1. Yes. Do a proper install or follow existing solutions for qemu.
2. Perhaps. idk.
3. See 2.
4. See 3.

QEMU - boot iso: [https://en.wikibooks.org/wiki/QEMU/Images](https://en.wikibooks.org/wiki/QEMU/Images)
Images and ISOs are read-only. If you'd like stuff saved between boots, then you'll need to make that happen. Other distros like tinycore are
a) smaller 16MB for a GUi
b) designed to have addons easily added to a master image

Just booted a tinycore:
```
$ qemu-system-x86_64 ./TinyCore-current.iso
```
it was slower than using KVM. Booting under KVM is less than 2 sec, worst case. At shutdown, tinycore asks what you'd like to save.
Correct me if I'm mistaken but you're suggesting some kind of hypervisor. My goal is to boot a real system from the disk image or virtual drive like Windows native boot from vhd\vhdx. I found some [discussion]("http://reboot.pro/topic/20603-linux-from-vhd-how-to/page-5#entry213229") about possibility of Linux boot from VHD, but I'm total noob in Linux and can't define which post I can assume as the guide.

---

### Post by TheFu on 2020-03-24
> **syn0ptic said:**
> Correct me if I'm mistaken but you're suggesting some kind of hypervisor. My goal is to boot a real system from the disk image or virtual drive like Windows native boot from vhd\vhdx. I found some [discussion]("http://reboot.pro/topic/20603-linux-from-vhd-how-to/page-5#entry213229") about possibility of Linux boot from VHD, but I'm total noob in Linux and can't define which post I can assume as the guide.

qemu is an emulator, slower than a hypervisor. That doesn't matter.  You seem to want to avoid that answer.

A few other ideas:
[LIST]
[*][https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
[*][https://www.supergrubdisk.org/super-grub2-disk/](https://www.supergrubdisk.org/super-grub2-disk/)
[/LIST]

I've not used either.

An EFI manager should be able to boot stuff too. Just have to get the EFI vs BIOS boot correct.

No way would I use vhd or vhdx files. Stick with formats that Linux knows. Seems there are corruption problems with those formats and linux tool to access them are buggy. Linux boot systems aren't going to know how to unpack files inside those containers.

---

### Post by syn0ptic on 2020-03-25
> **TheFu said:**
> qemu is an emulator, slower than a hypervisor. That doesn't matter. You seem to want to avoid that answer.

A few other ideas:
[LIST]
[*][https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
[*][https://www.supergrubdisk.org/super-grub2-disk/](https://www.supergrubdisk.org/super-grub2-disk/)
[/LIST]

I've not used either.

An EFI manager should be able to boot stuff too. Just have to get the EFI vs BIOS boot correct.

No way would I use vhd or vhdx files. Stick with formats that Linux knows. Seems there are corruption problems with those formats and linux tool to access them are buggy. Linux boot systems aren't going to know how to unpack files inside those containers.

OK this two links are all about boot from ISO - this is not a problem. The problem is how to save system changes after reboot?

---

### Post by TheFu on 2020-03-25
> **syn0ptic said:**
> OK this two links are all about boot from ISO - this is not a problem. The problem is how to save system changes after reboot?

SG2B supports booting an OS from almost any type of media, not just ISO files.  If you load SG2B onto a flash using dd, then boot that, then tell it to boot from the HDD, it might work, assuming the fstab and other settings have been corrected for the new image location.  Documentation for SB2B is sorely lacking, unfortunately.

---

