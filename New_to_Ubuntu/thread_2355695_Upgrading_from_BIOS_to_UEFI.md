---
title: "Upgrading from BIOS to UEFI"
date: 2017-03-15
forum: New to Ubuntu
---

### Post by blomstertj on 2017-03-15
I plan on upgrading my motherboard to that is a few years old to one that features UEFI.  My current motherboard doesn't support UEFI and is BIOS only.  I read somewhere that if you have UEFI Ubuntu installer creates an EFI directory and that grub-efi package is installed.

Will GRUB boot if I upgrade?  Will I have to reinstall GRUB?  Are there any other issues I may run into?

Thanks

---

### Post by grahammechanical on 2017-03-15
I am not sure of what you are going to do. Change the motherboard but keep the same hard drive that already has an install of Ubuntu/Linux?

Do not take me for an expert but I guess that Grub and Ubuntu will still load. I am guessing that the UEFI specification is backwards compatible with the BIOS specification.

With a BIOS motherboard we get MBR partitioning with its need for Extended and Logical partitions for more partitions than 4. With UEFI we get GPT partitioning which does not have the 4 Primary partition limit and so we do not need Extended and Logical Partitions.

I have a BIOS motherboard with 2 hard drives. One has MBR partitioning with Extended and Logical partitions. The other with GPT partitioning and more than 4 Primary partitions. Different versions of Ubuntu load from both drives. So, I know that GPT is backwards compatible with BIOS.

If we install Ubuntu on an UEFI/GPT partition drive it will create an efi_boot partition for Grub. If we install Ubuntu on a BIOS/GPT drive it will create a bios_boot partition for Grub. If we install Ubuntu on an BIOS/MBR partition drive Ubuntu will not create a boot partition. Although we can have one if we choose but we have to do the work.

Not having a UEFI motherboard I have not tried installing Ubuntu on a UEFI/MBR partitioned drive.

Regards

---

### Post by blomstertj on 2017-03-16
I'm going to be getting a new motherboard that uses UEFI and will continue using my current install. 

I was wondering if I did that, would I have to change anything. If everything worked great that would be nice.

---

### Post by mastablasta on 2017-03-16
UEFI is new bios. UEFI is fully supported by Linux. in fact Linux was the first OS to support it. UEFI in itself is not the issue.

The issue is secure boot option that was put there by Microsoft, when they started making UEFI motherboards. turning off secure boot (does the new motherboard have that option?) you should be able to continue to boot using MBR.

[URL="https://help.ubuntu.com/community/UEFI"][SIZE=2]https://help.ubuntu.com/community/UEFI
[/SIZE][/URL][SIZE=2][/SIZE]

---

