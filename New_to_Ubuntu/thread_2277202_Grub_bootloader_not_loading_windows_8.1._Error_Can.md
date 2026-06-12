---
title: "Grub bootloader not loading windows 8.1. Error: Cannot load image"
date: 2015-05-07
forum: New to Ubuntu
---

### Post by Pritam_Das on 2015-05-07
I just dual booted Ubuntu alongside pre-installed windows 8.1 in an acer Travelmate laptop. However when I first restarted after the installation, I was not prompted with grub bootloader and jumped directly to windows 8.1. I then searched a lot and found an answer where I had to use the boot-repair ([http://paste.ubuntu.com/11006086](http://paste.ubuntu.com/11006086)) from the command line which didn't seem to help. write this in command line:
```
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
``` 
This seemed to work and I got the grub bootloader. I can load ubuntu now but for some reason, whenever I tried to open my windows OS, it said something
 ```
/EndEntire
file path: *some random stuff* /EndEntire
error: cannot load image
```
I then restarted my computer and went into BIOS, I changed the Leagacy BIOS to UEFI (*Or the other way around, sorry, I don't remember which was the first option)* and voila I got into windows OS but again, it skipped the grub bootloader. So if I wanted to change OS, I have to change the type of boot my machine does. I would prefer to boot windows from the grub bootloader. Any help is highly appreciated. Thank you.

---

### Post by grahammechanical on 2015-05-07
If I understand things correctly, when Windows 8 comes pre-installed on a machine it is always installed in EFI mode. And that means that we must also install Ubuntu in EFI mode. Otherwise we get the situation that you describe.

I do not think that Windows 8 can run if we change the UEFI to legacy mode. It could be that you have installed Ubuntu in legacy mode. And when the UEFI is in legacy mode Ubuntu loads but Windows does not. And when the UEFI is in EFI mode Windows loads but Ubuntu does not.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> **Case when Ubuntu must be installed in UEFI mode**

 Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 
[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not. 
[/LIST]


Regards.

---

### Post by Pritam_Das on 2015-05-07
Thanks for the reply but it doesn't answer my query. How do I fix the error? Is there a way or I have to uninstall ubuntu and do a fresh reinstall? Thanks again

---

### Post by oldfred on 2015-05-07
If you installed Ubuntu in CSM/BIOS/Legacy boot mode, not UEFI you can use Boot-Repair to convert to UEFI. It really is just uninstalling grub-pc(BIOS) and installing grub-efi-amd64(UEFI).
Boot Ubuntu installer in UEFI mode, UEFI should offer two boot options. And the add in Boot-Repair and use advanced options to totally uninstall & reinstall grub.

DO NOT just reinstall Ubuntu without reading caution in my signature below. You may delete Windows. Of course you did a full backup of Windows before making major changes to system.

---

