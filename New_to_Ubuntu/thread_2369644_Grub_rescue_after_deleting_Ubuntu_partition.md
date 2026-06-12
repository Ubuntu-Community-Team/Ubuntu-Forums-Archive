---
title: "Grub rescue after deleting Ubuntu partition"
date: 2017-08-25
forum: New to Ubuntu
---

### Post by aviv2211 on 2017-08-25
Hello guys,
I am posting a new thread because the other threads didn't help me. A year ago I installed Ubuntu accidentally and now I deleted the partition, and then when I restarted my computer this showed up:

"Error: no such partition.
Entering rescue mode...
Grub rescue>"
I have tried to enter the bios and change the boot settings so that it won't boot into grub but it didn't help.

Intel core I5-4440
Boot options:
HL-DT-ST DVDRAM GH24NSBO
HARD Disk: ST500DM002-1BD142
And then UEFI and USB...

I have windows 10 installed.
Please help me.
Thank you :)

---

### Post by oldfred on 2017-08-25
Is Windows 10 UEFI or BIOS?
If originally from computer vendor it must be UEFI, but if upgrade from Windows 7 it probably is BIOS.

If UEFI, you can in UEFI just change boot order to make Windows first. And/or you can use UEFI's boot menu often f10 or f12 (check manual) to choose the Windows boot entry.

But you may want to houseclean out the /EFI/ubuntu folder in the ESP - efi system partition and remove the ubuntu entry in UEFI. UEFI has NVRAM so it remembers entries.

       UEFI How To Remove Ubuntu From A Computer Dual Booting With Windows 10 (UEFI only)
How To Remove Ubuntu From A Computer Dual Booting With Windows 10
[http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html](http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html)
Delete /EFI/ubuntu folder from Windows
[http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/](http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/)
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)
[http://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720?noredirect=1#comment1369050_497720](http://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720?noredirect=1#comment1369050_497720)

If BIOS install you have to restore a Windows or Windows type boot loader to MBR. 
Best to use your Windows repair/recovery flash drive but you can use Boot-Repair or manually from Ubuntu live installer install a Windows type boot loader.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

