---
title: "Unable to boot windows from GRUB after installing ubuntu"
date: 2015-09-24
forum: New to Ubuntu
---

### Post by Redknap on 2015-09-24
Hi,

Totally new with ubuntu/linux and I need some help. I have Windows 10 installed on my laptop and decided to give ubuntu a try so I installed it alongside windows, following the instructions from this website: [http://www.linuxandubuntu.com/home/dual-boot-ubuntu-15-04-14-10-and-windows-10-8-1-8-step-by-step-tutorial-with-screenshots](http://www.linuxandubuntu.com/home/dual-boot-ubuntu-15-04-14-10-and-windows-10-8-1-8-step-by-step-tutorial-with-screenshots)

 Installation was successful and I am able to get into Ubuntu but I am having problem to load to Windows from the GRUB menu. keep getting the error fail to load image.

I tried changing the boot options from UEFI to boot to my HDD as first options instead of ubuntu. This way, I am able to load into Windows but it doesn't work from the GRUB menu. Reversed the boot order in BIOS but still getting the same result. In order to boot from Windows or Ubuntu, I have to rearrange the boot order from BIOS, which is very inconvenient.

After some googling, I ran boot-repair as suggested. After repairing, there's more options listed in the GRUB menu but none of it can load to Windows. I am still getting the same error. Here is the URL that was generated after I ran boot-repair: [http://paste.ubuntu.com/12541208/](http://paste.ubuntu.com/12541208/)

Appreciate if someone can help me get this fixed. Changing the boot order everytime I want to swap between OS is not convenient.

---

### Post by oldfred on 2015-09-24
Grub only boots working Windows.

Did you leave Windows hibernated. Its fast boot setting is always on hibernation, that must be off.
Or it always needs chkdsk after a resize. Did you use Windows to resize the NTFS partition and immediately reboot so it could run chkdsk?

Can you use UEFI boot tab and directly boot Windows, or use one time boot key often f10 or f12, see manual. You may have to get into Windows internal repair console with f8.
But best to always have a Windows repair flash drive, so you can repair it. And keep Ubuntu live installer so you can repair it, if needed.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[URL="http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8"]http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8

[/URL]
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)

[URL="http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8"]
[/URL]

---

### Post by Redknap on 2015-09-24
> **oldfred said:**
> Grub only boots working Windows.

Did you leave Windows hibernated. Its fast boot setting is always on hibernation, that must be off.
Or it always needs chkdsk after a resize. Did you use Windows to resize the NTFS partition and immediately reboot so it could run chkdsk?

Can you use UEFI boot tab and directly boot Windows, or use one time boot key often f10 or f12, see manual. You may have to get into Windows internal repair console with f8.
But best to always have a Windows repair flash drive, so you can repair it. And keep Ubuntu live installer so you can repair it, if needed.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[URL="http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8"]http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8

[/URL]
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)

[URL="http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8"]
[/URL]


Sorry for not mentioning clearly that my Windows is working. I am able to load it from UEFI but not from grub.


Fyi, 
-I didn't leave it to hibernate.
-I resized the partition using gparted from the ubuntu live usb I've prepared before installing ubuntu. after resizing, I rebooted to load Windows and everything's good.

At the moment, in order for me to boot to Windows, I have to set in UEFI boot menu to windows boot manager as the first option. That is the only way for me to load to Windows. If i want to boot to ubuntu, I will swap it to ubuntu, which will then load Grub.
[ATTACH=CONFIG]264628[/ATTACH]

Grub is showing these:
[ATTACH=CONFIG]264627[/ATTACH]

and whatever i choose from the list that has the word windows, it will return with the error "cannot load image"(refer below pictures). No problem loading the others though.
[ATTACH=CONFIG]264626[/ATTACH][ATTACH=CONFIG]264629[/ATTACH][ATTACH=CONFIG]264630[/ATTACH]

I have disabled the fast startup but it doesnt solve the problem. Anything else that I can try?

---

### Post by oldfred on 2015-09-24
Do you have secure boot on?
I do not think grub boots Windows if secure boot is on.

       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)
Windows will not chain load from grub -
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,96800,32000,7c043777b8608641,87,f6)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi

---

### Post by Redknap on 2015-09-24
> **oldfred said:**
> Do you have secure boot on?
I do not think grub boots Windows if secure boot is on.

       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)
Windows will not chain load from grub -
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,96800,32000,7c043777b8608641,87,f6)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi


Thank you! tested the workaround by disabling secure boot and I am able to load windows via grub.

---

