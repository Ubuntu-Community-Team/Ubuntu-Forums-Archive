---
title: "Trying to boot from external hard-drive (obviously it's not working)."
date: 2018-06-03
forum: New to Ubuntu
---

### Post by mike.apples92 on 2018-06-03
I should probably open by saying this is my first foray into the world of Linux.  So if I sound like an idiot, I apologize.   I've got literally no idea what I'm doing!

The download and install were smooth sailing.  I've got Ubuntu 18.04 installed onto an otherwise empty 500 gig partition in my external hard drive.  However, I can't seem to get it to boot.  Specifically, I get stuck in what looks like an old 1970s DOS command line, that's calling itself GRUB.  I googled a list of grub commands, and after using LS, I'm able to see my internal hard-drive (and all 5 partitions).  However that's the only drive I can see.

If I have to I can give up on booting from an external drive.  However I'd like to ask first if anyone knows 1:  Can it be done?  and 2:  If so how do I get GRUB to see my external drive?

---

### Post by TheFu on 2018-06-03
I haven't used USB to boot anything besides an install ISO in about a decade, so I don't have direct experience with what you are trying to accomplish. But here's some guesses.

Thanks to EFI booting, things aren't as easy as they used to be.  When you installed, did you choose EFI booting or "Legacy BIOS" booting?  Usually the BIOS can only do 1 at a time and recent Windows will use EFI.  But USB devices typically use Legacy.  Might that be the issue?  I'm not certain.

Perhaps someone else with direct experience will respond.  Would probably be helpful if you shared the exact model of computer/laptop, since some vendors don't follow the EFI specs, which break things for Linux too.

---

### Post by oldfred on 2018-06-03
I have multiple full installs on USB flash drives and one on an external SSD.
If BIOS relatively easy.
If UEFI bit more complex.

But in all cases you need to partition in advance. And since external drive better to use gpt partitioning as with Ubuntu you can use BIOS or UEFI and Windows will never boot full install from external drive so MBR not required.

This one has both bios_grub for BIOS boot and ESP - efi system partition for UEFI boot.
```
Disk /dev/sdd: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR=#ff0000]gpt[/COLOR]
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 1      20.5kB  500MB   500MB   fat32        esp_usb  boot, esp
 2      500MB   501MB   1049kB                        bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         data32   msftdata

```

With BIOS install and Something Else install option, you have a combo box at bottom of partitioning screen that says where to install grub2's boot loader. You need to select drive (not partition) that your flash drive is.

But with UEFI boot, grub ignores your selection and just installs the .efi boot files into the first ESP found, usually sda. That will let you boot install from flash drive, but only from system you used to install it. In my case I only have Ubuntu installs and it overwrites my default boot of internal install of Ubuntu. Or I quickly learned to backup my ESP on my sda drive.

And UEFI only boots external drives from ESP on external drive and from /EFI/Boot/bootx64.efi file. 
Same name is used by Windows installer and Ubuntu installer, but Ubuntu's installer version is a limited version of grub for only booting install media.

New installer with 18.04 now creates /EFI/Boot/bootx64.efi, older installs did not.
I copy all of /EFI/ubuntu to external drive's ESP and then copy again into /EFI/Boot folder and rename shimx64.efi to bootx64.efi. 

 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by mike.apples92 on 2018-06-03
[COLOR=#000000]*With BIOS install and Something Else install option, you have a combo box at bottom of partitioning screen that says where to install grub2's boot loader. You need to select drive (not partition) that your flash drive is.*

This seems to be my problem.  I did the Something Else install option, and I'm pretty sure I selected the partition rather than the drive.  I'll try a re-install and see if that works.

[/COLOR][I][COLOR=#000000]
[/COLOR][/I][COLOR=#000000]For my own edification: what is ESP (as in: *I copy all of /EFI/ubuntu to exteral drive's ESP*)?  I tried google first, but am quite skeptical that you're copying to the external drive's Elder Scrolls Plugin.


Thank you both for the help!


[/COLOR]

---

### Post by oldfred on 2018-06-03
If you have UEFI hardware and then UEFI installs, you have an ESP - efi system partition. That is FAT32 with boot flag.
If not UEFI or more than 5 years old then it is Probably BIOS only. All Windows 8 or later systems were required by Microsoft to be UEFI with Secure boot and that was 5 years ago. A few Windows 7 systems were UEFI, but did not have Secure Boot on.

I started using gpt partitioning long before it was standard on PCs. essentially when Windows required UEFI. It was a standard on Apple Mac much earlier, and had been available for years before that, but few systems used or support it.

---

