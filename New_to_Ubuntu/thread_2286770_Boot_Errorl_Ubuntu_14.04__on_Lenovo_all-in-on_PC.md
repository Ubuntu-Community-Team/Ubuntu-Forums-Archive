---
title: "Boot Errorl Ubuntu 14.04  on Lenovo all-in-on PC"
date: 2015-07-14
forum: New to Ubuntu
---

### Post by nagendra4 on 2015-07-14
Hi

I installed Ubuntu 14.04 on a all in one Lenovo PC (it previously had Windows 7 home edition) . I installed Ubuntu only but when I restart I get the following error "Reboot and Select
proper boot device or insert boot media..'

Searching on the web I used 'try Ubuntu' from the USB tick and created this Pastebin  but I still get the same error. I saw some suggestions regarding deleting /dev/sda1 using gparted but I am not sure if I should do this 

I am an absolute novice so please pardon me if I am missing anything obvious. 



[http://paste.ubuntu.com/11875403/](http://paste.ubuntu.com/11875403/)

thanks

---

### Post by oldfred on 2015-07-14
Do you have secure boot on? Try turning it off in UEFI.
You absolutely need sda1 to boot.

You still have Windows folder in efi partition.

Some systems have modified UEFI to only boot the Windows entry by description.

If you cannot directly boot the ubuntu entry in UEFI or from one time boot key you can do this:
       sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Then boot "Windows" entry in UEFI which really is shim or secure boot version of grub.

Other work around like the copy of grub or shim and rename to  bootx64.efi or since not using Windows the rename to Windows bootmgfw.efi are other possible work arounds. Details in link in my signature.

---

### Post by nagendra4 on 2015-07-14
I don't see a secure boot option, I had Windows 7 home edition. I tried [COLOR=#000000]sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" and [/COLOR][COLOR=#000000]rebooted but did not work. I could not understand :"Then boot Windows" entry in UEFI which really is shim or secure boot version of grub." I can see Ubuntu installed when I select 'Try something else' using the usb installer. I saw some posts regarding copying and renaming files but Idid not understand. I have two folders efi and grub under boot, efi is empty and grub has 3 folders including x86_64-efi.
[/COLOR]
thanks

---

### Post by oldfred on 2015-07-14
Are you looking at files in live installer not your install?

Post this:
sudo efibootmgr -v

Compared to version in Summary report you should have a new entry that says "Windows Boot Manager" but refers to shimx64.efi. And if from UEFI you boot the Windows entry then grub should load.

---

### Post by nagendra4 on 2015-07-15
BootOrder: 0002,0000,0004,0006,0001,0005
Boot0000* ubuntu    HD(1,800,100000,ea391fb0-1851-4399-805d-3d65bc5787ba)File(\EFI\ubuntu\shimx64.efi)
Boot0001* ST1000DM003-1CH162    BIOS(2,0,00)AMBO
Boot0002* Windows Boot Manager    HD(1,800,100000,ea391fb0-1851-4399-805d-3d65bc5787ba)File(\EFI\ubuntu\shimx64.efi)
Boot0004* Windows Boot Manager    HD(1,800,100000,443393f7-fbbc-465d-811c-b2767140997d)File(\EFI\ubuntu\shimx64)
Boot0005* Generic Flash Disk 8.07    BIOS(2,0,00)AMBO
Boot0006* UEFI: Generic Flash Disk 8.07    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(1,0)HD(1,1d0,3d3e30,fda3aad3)AMBO

---

### Post by oldfred on 2015-07-15
It looks like 0002 & 0004 are duplicates and should boot, if vendor has modified UEFI to boot by description.
If UEFI from vendor was really correct then 0000 should also work.

And shim is the secure boot or signed versions of grub which should work if secure boot is on or not.
But better to have secure boot off. On my motherboard it does not say secure boot, but Windows or other.

---

