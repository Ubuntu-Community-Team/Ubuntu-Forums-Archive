---
title: "Boot Repair - EFI Mode"
date: 2015-03-03
forum: New to Ubuntu
---

### Post by Khyatti_Gupta on 2015-03-03
Hi,

I am trying to install Ubuntu 14.04 alongside Windows 8. I followed this tutorial - [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) . Till step 7 everything worked fine, then when I run Boot-Repair, this error comes up - *[COLOR=#000080]"The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will enable this feature. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode."[/COLOR]*

The pastebin url is - [http://paste.ubuntu.com/10514342/](http://paste.ubuntu.com/10514342/)

Please give your suggestions. I am booting from LiveUSB + UEFI mode + 50 GB space for the 3 partitions (in total - 25 GB for / + 8 GB for swap area + 17 GB for /home ) + Secure Boot disabled + Intel Rapid Smart Technology disabled. 

Thanks

---

### Post by grahammechanical on 2015-03-03
Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.[FONT=inherit][/FONT][FONT=inherit][/FONT]
[/LIST]
I am copying this from the Boot Repair report of another user. It shows something that is missing in your Boot Repair report.

> File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /EFI/Toshiba/Boot/bootmgfw.efi 
                       /EFI/Toshiba/Boot/bootmgr.efi 
                       /EFI/Toshiba/Boot/memtest.efi




Do you see the difference? It is

>                        /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 

You have in sda1 EFI boot files for Microsoft but you do not have EFI boot files for Ubuntu. I conclude that Windows 8 is installed in EFI mode but Ubuntu is installed in legacy mode. That, in my opinion after studying many posts like this, is the cause of the problem.

> 
[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[/LIST]


You can either let Boot Repair fix try to things or you can re-install Ubuntu in EFI mode.

Regards.

---

### Post by oldfred on 2015-03-03
While best to have both systems in same boot mode, you should be able to boot Ubuntu in BIOS mode with Windows in UEFI mode.
But you may have to change boot mode in UEFI from UEFI to CSM/BIOS each time and can only boot from UEFI boot menu or possibly one time boot key. But not from grub menu. 
UEFI and BIOS are not compatible and you have to totally reboot to switch modes.

Boot-Repair's advanced mode has an option to totally uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI). But you need to boot installer in UEFI mode.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
    [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Khyatti_Gupta on 2015-03-04
Thanks!!

I changed the pendrive and then the option of Install Ubuntu alongside Windows appeared. This worked for me.

---

### Post by Khyatti_Gupta on 2015-03-04
[COLOR=#000000]Thanks!![/COLOR]

[COLOR=#000000]I changed the pendrive and then the option of Install Ubuntu alongside Windows appeared. This worked for me.[/COLOR]

---

