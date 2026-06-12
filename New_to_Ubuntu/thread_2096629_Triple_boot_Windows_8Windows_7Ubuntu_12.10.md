---
title: "Triple boot: Windows 8/Windows 7/Ubuntu 12.10"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by silvius83 on 2012-12-20
Hola,

I just bought a new ASUS Vivobook X202E pre-installed with Windows 8. For warranty reasons, I can't uninstall Windows 8. I want Ubuntu, of course, and also Windows 7 because Windows 8 is still looking half-baked. So, I'm looking to do a triple boot with Windows 8, Windows 7 and Ubuntu 12.10. I've done some forum searches and Googling, but all the threads I have seen seem to start from Windows 7 pre-installed whereas I have Windows 8. Does anyone know the best way to do this? I guess I don't have to do Windows 7 if it's overly inconvenient or messy to do so. Thanks in advance for the help!

---

### Post by silvius83 on 2012-12-20
Here are a screenshot of my System and my partitions from Windows 8:

[IMG]http://i45.tinypic.com/2hdpauh.png[/IMG]

[IMG]http://i48.tinypic.com/11v40zr.png[/IMG]

I'm wondering if I set up two more partitions, install Windows 7, then Ubuntu 12.10, will GRUB grab them all for a single boot menu?

---

### Post by superDave972 on 2012-12-20
First, I would enter Windows 8 and bring up the Disk Management tool. In Windows 7 (not a typo - I mean Windows 7), you can find the Disk Management tool by right-clicking on My Computer, then clicking Manage. I imagine you can still locate the Disk Management Tool in a similar way in Windows 8.

Any way, once you have the Disk Management Tool open in W8, I would shrink the current partition. Using the Unallocated space, I would then create two more partitions - one partition for Windows 7 and one for Ubuntu. I would format the new partitions in FAT32. NTFS formatting can be used for the Windows partition, but the Ubuntu partition has to be FAT32.

Once you have your partitions set up, use image discs (.iso)to install your additional OS's. During each OS installation be sure to install the OS to the correct partition that you set up earlier.

---

### Post by superDave972 on 2012-12-20
OK, so I didn't see your images in your second post before I posted my first post. You have more partitions than I initially thought. Anyway, I think your best course of action would be to shrink the OS partition 50-100GB. Then, also shrink the Data partition another 50-100GB (or whatever disk size you want available for W7 and Ubuntu). Then, format the new Unallocated space for your new OS's.

I have ran several machines dual-booting W7 and different flavors of Linux (CentOS, Fedora, Ubuntu, Xubuntu) and I have never had an issue with GRUB displaying the different choices of Operating Systems. However, Red Hat flavors of Linux seem to default to their OS. They only give a choice if you interrupt the boot process.

---

### Post by oldfred on 2012-12-20
Not sure how 7 & 8 will work together. You need to install Windows 7 and Ubuntu in UEFI mode as 8 is UEFI.

With BIOS a second install of Windows always put its boot files into the first installs boot partition. Then it updated BCD to offer to boot both Windows. Grub then only sees Windows boot files in one Windows and offers to chain load to that one Windows and from Windows you choose to boot the version you want.

You could in BIOS change boot flags before installing and separate the installs so grub would see each. But with UEFI the boot files are in /efi partitions.

       /boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/BOOT/bootx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi

Also the BCD is it the EFI/Microsoft/Boot folder. You may be able to copy the bootmgrw.efi & BCD and create EFI/Microsoft8/Boot folder. From UEFI you would see windows, windows8 & ubuntu as boot options. Logically it should work, but have not seen anyone try. There is one UEFI system that does parse efi folder descriptions to make sure they work. That would then not work with that system.

 Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

Be sure to backup entire efi partition before installing anything and before attempting modifications.

---

