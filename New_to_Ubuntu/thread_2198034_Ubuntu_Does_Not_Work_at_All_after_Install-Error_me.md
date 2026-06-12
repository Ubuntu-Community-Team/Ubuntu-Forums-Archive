---
title: "Ubuntu Does Not Work at All after Install-Error messages."
date: 2014-01-06
forum: New to Ubuntu
---

### Post by mjcbreak1964 on 2014-01-06
I downloaded the Ubuntu 64-bit operating system last night (on an HP 2000 Notebook) and followed the instructions to format it onto a flash drive. I used the flash drive to install the operating system and then re-booted the computer. When I restarted the computer there were two icons: the one on top being 'Windows 8' and the bottom being 'Ubuntu.' When I click on Ubuntu, I get an error message with the code 0xc000000f and it cites the location [FONT=Courier New]\ubuntu\winboot\wubildr.mbr[/FONT] and says that the required file is corrupt. I tried to uninstall the operating system by going into the C drive and finding the Ubuntu folder for an uninstall file and used it, but I am guessing that I need to do more. At this point, I either want Ubuntu on my notebook in a working version or I want it removed completely! How can I do either one?    Thanks!

---

### Post by newb85 on 2014-01-06
It would appear that you installed Ubuntu using Wubi (the Windows Ubuntu installer) to install Ubuntu from within Windows.  Wubi doesn't work with the UEFI firmware used in Windows 8 machines.  Please remove the Wubi installation (using Add/Remove Software in Windows) and then reinstall Ubuntu by booting the machine from the flash drive you created.

---

### Post by hakuna_matata on 2014-01-06
> When I click on Ubuntu, I get an error message with the code 0xc000000f and it cites the location [FONT=Courier New]\ubuntu\winboot\wubildr.mbr[/FONT] and says that the required file is corrupt. 
This is a well-known error message. It means that the UEFI version of Windows Boot Manger is only able to load Windows. 
> I want it removed completely! 
[https://help.ubuntu.com/community/Wubi#Uninstall_from_Windows_8](https://help.ubuntu.com/community/Wubi#Uninstall_from_Windows_8)

Official solution: [http://www.ubuntu.com/download/desktop/windows-installer:](http://www.ubuntu.com/download/desktop/windows-installer:)
> Please use a [64-bit flavour]("http://www.ubuntu.com/download/desktop") of Ubuntu, installed directly to its own partition 
rather than using the Windows installer.

For testing purpose there are also unofficial solutions....

---

### Post by hakuna_matata on 2014-01-06
> **newb85 said:**
> Wubi doesn't work with the UEFI firmware used in Windows 8 machines.
Unfortunately, this error message is not only a Wubi bug. If you change [FONT=Courier New]\ubuntu\winboot\wubildr.mbr[/FONT] to \EFI\ubuntu\shimx64.efi of a working Ubuntu installation, same error message will appear.

---

