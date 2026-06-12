---
title: "New Ubuntu Install, Dual-Boot, GPT, UEFI, no Windows in Grub2"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by ULAMSS5 on 2014-04-06
I just installed Ubuntu onto my GPT SSD, following which I had boot problems which were solved using LiveCD and boot-repair.

However, now Windows is not sowing in Grub2. 

boot-repair paste: [http://paste.ubuntu.com/7211888/](http://paste.ubuntu.com/7211888/)

os-prober shows 2 linux images and 2 "initrd" images, and nothing else. Updating grub doesn't change anything either.

Can anyone help me diagnose and solve this?

---

### Post by oldfred on 2014-04-06
You are not showing any Windows boot files in sda3. But if partition needs chkdsk or is hibernated Linux tools will not be able to open it and see the boot files.

It also looks like you have Ubuntu installed in BIOS boot with grub in the protective MBR.
And you show two efi partitions for UEFI boot, but you only can have one.
Was sda7 a bios_grub partition? Ubuntu/grub needs a unformatted 1 or 2MB partition with the bios_grub flag to boot in BIOS mode. Remove boot flag from sda7 with gparted. If you want MBR boot change to unformatted and add bios_grub flag.
Both Windows and Ubuntu need an efi partition (one per hard drive) to boot in UEFI mode.
And you show no efi boot files for either Windows or grub in your efi partition.

Windows only boots from gpt partitioned drives with UEFI.
Ubuntu will boot from gpt partitioned drives with BIOS if you have a bios_grub partition or with UEFI if you have an efi partition.

Boot-Repair can convert a BIOS install of Ubuntu to UEFI if efi partition exists and drive is gpt partitioned. Or it can convert an UEFI install to BIOS boot if bios_grub partition exists. It uninstalls grub-pc(BIOS) and installs grub-efi(UEFI).

But your must boot both Windows & Ubuntu installers in the same boot mode as you want it to instal. Or if flash drive booted with UEFI then it will install in UEFI or if booted with BIOS/Legacy/CSM it will install inBIOS mode.
But BIOS requires MBR partitioning for Windows, UEFI requries gpt partitioning for both Windows & Ubuntu.

---

