---
title: "Making an ISO with xorriso."
date: 2013-09-24
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2013-09-24
I got this [here]("https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Bootable_Media"): 

[QUOTE=The Arch Linux Wiki (modified)]xorriso -as mkisofs -iso-level 3 \
    -full-iso9660-filenames\
    -volid "ARCH_201212" \
    *-appid "Ubuntu-i386-UEFI"* \
    *-publisher "Canonical <http://www.ubuntu.com>"* \
    *-preparer "Jonathan Precise"* \
    **-eltorito-boot isolinux/isolinux.bin** \
    **-eltorito-catalog isolinux/boot.cat** \
    **-no-emul-boot -boot-load-size 4 -boot-info-table** \
    **-isohybrid-mbr "/mnt/iso/isolinux/isohdpfx.bin"** \
    -output "~/archiso.iso" "/mnt/iso/"[/QUOTE]

to remove UEFI support from the ISO. However, I want to do the opposite. The things in **bold** are the things I *think* I need to change to make this happen.

The question is what should I change it to?

---

### Post by scdbackup on 2013-09-24
Hi,[br][/br] the options you marked are for BIOS booting from CD and USB stick. You may well keep them.[br][/br] [br][/br] What you need is a FAT filesystem image file which you submit by options -e or --efi-boot.[br][/br] The content of that fileystem image is out of the scope of my knowledge. I only provide xorriso for packing it up.[br][/br] [br][/br] Lets have a look at debian-7.1.0-amd64-netinst.iso, file .disk/mkisofs : ```
 ... -b isolinux/isolinux.bin ... -eltorito-alt-boot -e boot/grub/efi.img -no-emul-boot -isohybrid-gpt-basdat ... boot1 CD1 
``` [br][/br] -eltorito-alt-boot ended the range of -b (which is for BIOS).[br][/br] -e submitted the FAT image boot/grub/efi.img for El Torito (EFI from CD/DVD).[br][/br] The FAT image file was brought into the ISO image as part of the file payload in ./boot1 or ./CD1.[br][/br] -isohybrid-gpt-basdat announced the FAT image in MBR and GPT for EFI from USB stick.[br][/br] See [http://www.gnu.org/software/xorriso/man_1_xorrisofs.html](http://www.gnu.org/software/xorriso/man_1_xorrisofs.html) [br][/br]  Have a nice day :)[br][/br] [br][/br] Thomas

---

### Post by Jonathan Precise on 2013-09-28
Thank you! will try that.

---

