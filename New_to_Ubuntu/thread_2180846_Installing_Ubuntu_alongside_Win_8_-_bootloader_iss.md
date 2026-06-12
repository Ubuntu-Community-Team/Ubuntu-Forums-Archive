---
title: "Installing Ubuntu alongside Win 8 - bootloader issue"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by cAAseMe on 2013-10-14
Hello,

I am a complete beginner to Ubuntu, installing it on my new laptop for the first time. I've gotten version 12.04.3 LTS and used this guide to install it: [http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

Now i followed that guide to the letter up until #9. At this point, i have installed Ubuntu, however it won't load as every time i restart my PC it automatically loads Windows 8.

I have tried running the boot repair utility as described in step #9 of the guide however it won't open. I get an error that says "E: Unable to locate package boot-repair"

So what can I do at this point?

Thanks

---

### Post by fantab on 2013-10-15
You have to install **[BOOT-REPAIR]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu")** first. Have you done that?
Most of the times the '**Recommended Repair**' should do.
Post the **Bootinfo Summary** that Boot-Repair generates, here. (Just post a live link).

---

### Post by barrings on 2013-10-15
Hello,
Another thing to do is install a program called grub-customizer.  I assume that during install GRUB was installed, and for some reason which is quite frankly beyond me Windows said "default to me".  Grub-custiomizer can be installed with sudo ```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
 sudo apt-get update
 sudo apt-get install grub-customizerapt-get install grub-customizer
``` Enter each of these commands separately.

Then to run it, type: ```
sudo grub-customizer  
```  (The sudo part of these commands is kind of like "run as administrator" in Windows Vista and higher.  It gives administrator privileges to the program.  Once it runs, you want the General Settings Tab and there you will see the "Default Entry-predefined entry" combobox.  This combobox works on entry number, so use the first page to determine where Ubuntu comes.  E.g. If it's the third entry, pick "Entry 3".

barrings

---

### Post by barrings on 2013-10-15
Hello,
This sounds like a fairly annoying fault.  

Another thing to do is install a program called grub-customizer.  I assume that during install GRUB was installed, and for some reason which is quite frankly beyond me Windows said "default to me".  Grub-custiomizer can be installed with sudo ```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
 sudo apt-get update
 sudo apt-get install grub-customizerapt-get install grub-customizer
``` Enter each of these commands separately.

Then to run it, type: ```
sudo grub-customizer  
```  (The sudo (pronounced "soo-do") part of these commands stands for "super-user do" and is kind of like "run as administrator" in Windows Vista and higher.  It gives administrator privileges to the program.  Forget it, and the terminal will spit out a message saying something to the effect of "Cannot run program.  Are you root?" ("Root" being the administrator user name.))

Once it runs, you want the General Settings Tab and there you will see the "Default Entry-predefined entry" combobox.  This combobox works on entry number, so use the first page to determine where Ubuntu comes.  E.g. If it's the third entry  in the list, pick "Entry 3".  

I hope that helps.

barrings

---

### Post by fantab on 2013-10-15
Personally, I wouldn't recommend Grub-Customizer. IMO it creates more issues than it solves. Customizing GRUB is very easy... [READ HERE]("http://ubuntuforums.org/showthread.php?t=2076205").

---

### Post by oldfred on 2013-10-15
You can install Boot-Repair to any working Ubuntu, to the live installer, or download it as a Linux repairCD. It also has a full remix of 13.04 that is just 13.04, but includes Boot-Repair, so from live installer you do not have to reinstall each time you reboot.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

I agree with fantab. While Grub-Customizer is a gui and makes it easy to change settings, the manual grub editing changes are not that difficult. 
I used to recommend it but now do not as we have seen users with issues where Grub-Customizer has renamed all the grub2 scripts and had issues.

---

### Post by barrings on 2013-10-16
Hello,
The only reason I suggested Grub-customizer is that I have used and liked startup-manager but it has been replaced in Synaptic  (or whatever it's successor is, I hear Synaptic has been superseded) by grub-customizer, a change I take it is not good.  I have never used the software, so I had to learn all over again.  I have realised I made a mistake and for that I am sorry.  I was not trying to recommend it by any means, but I find that a gui is far more user-friendly than a terminal command.

barrings

---

### Post by jeehyun on 2013-10-16
I think you installed boot loader on other parition or you has hdd formatted as gpt not mbr.

---

### Post by oldfred on 2013-10-16
Ubuntu does not autoinstall synaptic anymore, but offers Software Center. They converted to that so they could also offer and sell software, games & music.
But you still can install synaptic as it is on of the first things I install.I have it in my 13.10 install, so still available.

Grub-Customizer does make it easier for those who like a gui and are afraid of editing files. But some of the more advanced changes are changes to the scripts and it renames the scripts. Then a new install of grub, or a major update to grub creates the original grub script files and the renamed ones. Then you have duplicate menu entries.

---

### Post by cAAseMe on 2013-10-16
Hi guys,

I did what fantab suggested and it seems to have worked. Now when i restart my laptop it gives me the choice between Ubuntu and Windows 8, as well as their recovery modes and a few other options. Both Ubuntu and Win 8 load normally. 

However at the end of Boot Repair it said this: "Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file"
Sorry if this sounds like a dumb question but where and how do you do this? I tried entering it as a command line upon restarting the laptop (when it gives the choice between Ubuntu and Win8) but it couldn't recognize the command.

Here's my Ubuntu pastebin following boot repair if it helps: [http://paste.ubuntu.com/6248575/](http://paste.ubuntu.com/6248575/)

Also when booting Ubuntu my wireless LAN seems to be hard blocked for some reason.

Thanks.

---

### Post by oldfred on 2013-10-16
From the UEFI menu it will only show ubuntu, but that will be the Ubuntu folder in the efi partition with the grub efi boot file.
It looks like you booted Ubuntu & Boot-Repair in BIOS/CSM mode. You need to boot in UEFI mode.

If you can boot Ubuntu directly you do not need the file rename that was done. Some UEFI only boot Windows and Boot-Repair creates a work around to rename the Windows efi file to actually be grub2's shim file that has the Microsoft key, but boots grub. Then from grub menu you boot the backup Windows file.

from line 934
 Save and rename /mnt/boot-sav/sda8/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (/mnt/boot-sav/sda8/boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi)

If you can directly boot ubuntu entry from UEFI menu, you can unrename.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by cAAseMe on 2013-10-17
> **oldfred said:**
> From the UEFI menu it will only show ubuntu, but that will be the Ubuntu folder in the efi partition with the grub efi boot file.
It looks like you booted Ubuntu & Boot-Repair in BIOS/CSM mode. You need to boot in UEFI mode.

Yeah that's what I did initially. Since my computer automatically booted Win 8, i had to launch Ubuntu through its install CD and run the boot-repair from there. How can I launch Ubuntu in UEFI mode? I don't see it as an option in the OS selection menu.

> **oldfred said:**
> If you can boot Ubuntu directly you do not need the file rename that was done. Some UEFI only boot Windows and Boot-Repair creates a work around to rename the Windows efi file to actually be grub2's shim file that has the Microsoft key, but boots grub. Then from grub menu you boot the backup Windows file.

from line 934
 Save and rename /mnt/boot-sav/sda8/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (/mnt/boot-sav/sda8/boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi)

If you can directly boot ubuntu entry from UEFI menu, you can unrename.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Sorry for the stupid question but how do I find these files? First time that i'm installing an OS so i really have no idea where all of this is stored and how to access it.

---

### Post by oldfred on 2013-10-17
And with the file rename that Boot-Repair ran, you should boot grub from a Windows entry. If you un-rename then you should boot an ubuntu entry. Boot-Repair flagged your UEFI as one of the buggy one's that only boots Windows. Not sure how it knows??
But if true you have to have the renamed files to boot. Then when UEFI thinks it is booting Windows it really boots to grub menu and you can select Windows from that.

But if secure boot is on, it only shows secure boot options. And you do not show the signed kernel & grub installed.

How you boot installer is how it installs. And there actually are three options. UEFI with secure boot, UEFI (no secure boot) and BIOS which cannot have secure boot. Ubuntu installer works all three ways depending on what settings in UEFI/BIOS and which boot option you use.

---

