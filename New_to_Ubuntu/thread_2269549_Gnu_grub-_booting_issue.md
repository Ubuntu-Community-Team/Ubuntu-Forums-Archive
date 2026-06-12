---
title: "Gnu grub- booting issue"
date: 2015-03-16
forum: New to Ubuntu
---

### Post by alexaron17 on 2015-03-16
Hi all

I have a MSI GS60 laptop. Today I installed Ubuntu version 14.04 LTS alongside Windows 8 to dual boot. After prolonged use, I decided that I did not like the OS. I thought that Windows was cluttered anyway, so I decided to restore my computer as if I had just bought it.

I left the room for a bit to let the process complete and when I came back I found a terminal like screen with the text,

```
GNU GRUB version 2.02~beta-9ubuntu 1
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.
```

Now whenever I boot up my computer, it switches on to this screen. I have absolutely no idea what to do and how to fix this and return to Windows. I posted here first as I know how reliable this forum is.

Please help ASAP, or direct me to another place I may be able to receive assistance. I'm desperate. It is starting to stress and worry me greatly.

Regards
Alex

---

### Post by oldfred on 2015-03-16
From Ubuntu live installer, add Boot-Repair and post link to the Summary report it gives.
Boot-Repair can only fix very minor Windows issues, you need a Windows repair cd or flash drive for almost all Windows issues. But report will tell us details.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If Windows was pre-installed in UEFI mode, you should just be able to choose Windows in UEFI boot menu or perhaps one time boot key, often f10 or 12, but varies.

---

### Post by alexaron17 on 2015-03-16
What is Ubuntu Live Installer? Is that just the normal way to install Ubuntu? (Copy ISO to flash and boot flash)
sorry, really not good with this whole concept
i also had a thought, if I reinstalled Ubuntu could I recover Windows from there?

---

### Post by oldfred on 2015-03-16
Can you directly boot Windows from UEFI menu?
Did you create a Windows repairCD or flash drive when Windows was working?
Always best to have full backups and repairCD or flash drives for the current version of every operating system you have installed.

The live installer is the Desktop Ubuntu ISO installed to a flash drive or DVD.  
       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by alexaron17 on 2015-03-16
I cannot boot Windows from this menu. It says my pc needs to be repaired and gives me options to enter UEFI Firmware Settings.
I think that I may have a repair flash drive. Someone else told me to do this [http://windows.micro...t-refresh-media]("http://windows.microsoft.com/en-CA/windows-8/create-reset-refresh-media") however when i booted from the flash drive it gave me the same screen.
I am downloading booot repair disk from the link you gave, should i try it?
I also still have Ubuntu on a flash if i need to install it, however, i believe that if i do it will remove Windows completely.

---

### Post by oldfred on 2015-03-16
If you still have the Ubuntu flash drive that you used to install, boot it in live mode. Then follow instructions to install Boot-Repair to that. If you reboot, you have to install it again, as live installer does not save changes, but otherwise works as regular Ubuntu.

The only other thread that mentioned MSI as a brand.
 MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)

Some brands require you to make several UEFI setting changes. Some even require a password (never lose that) to let you boot anything other than Windows on hard drive. Some let you specifically authorized other systems. And some just boot Windows, but we have work arounds.

---

### Post by alexaron17 on 2015-03-17
Right - here is some proper information.

MSI GS60 Ghost 2PC Gaming laptop
Nvidia Geforce GTX 860M GPU

I first ran the boot-repair as a live disk twice and received these two links: [http://paste.ubuntu.com/10610747](http://paste.ubuntu.com/10610747)     [http://paste.ubuntu.com/10610777](http://paste.ubuntu.com/10610777)
I then ran the boot-repair in Ubuntu Live mode and received this link:  [http://paste.ubuntu.com/10615295/](http://paste.ubuntu.com/10615295/)

I hope that this information can help us get to the bottom of this.

---

### Post by oldfred on 2015-03-17
You have an UEFI system and both Windows and Ubuntu UEFI boot files.
But you have a Windows boot loader in the protective MBR for an old BIOS boot. Make sure you do not have UEFI set for CSM/BIOS boot as it will try to use the MBR boot loader and not work.

You need to always boot in UEFI mode and always boot live installer for flash drive in UEFI mode. UEFI should offer two options to boot flash drive. Usually one is clearly UEFI -name of flash drive, but the other is just the name of flash drive and will boot in CSM mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Windows will only boot in UEFI mode. And it looks like it should just work.

You may want to remove the ubuntu folder from the efi partition first, then delete any ubuntu entries in UEFI. If you do not delete folder first it will add entries back into UEFI.
If you UEFI does not let you edit and remove entries, you can use efibootmgr from Ubuntu live installer booted in UEFI mode.

      
 Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by alexaron17 on 2015-03-17
Okay, please could you give me a step by step process on what I need to do?

---

### Post by oldfred on 2015-03-17
Every UEFI is different, I do not know your system, but what every changes you made to change boot to BIOS you need to undo to boot in UEFI and in boot device menu in UEFI choose Windows.
Once you get Windows working again then you can do the house clean of old Ubuntu entries. The only details I have are posted above. You do know how to delete a folder?

---

### Post by alexaron17 on 2015-03-17
I opened Linux Live with flash which did have label UEFI. I then used efibootmanager and deleted all Ubuntu options there. Now, when i switch on my computer and go to boot options, I am greeted with the following options:

UEFI: IP4 Qualcomm Atheros PCIe Network Controller - when i boot with this it tries to take me to GNU Grub screen but then boots to Windows menu (see below)
UEFI: IP6 Qualcomm Atheros PCIe Network Controller - when i boot with this it tries to take me to GNU Grub screen but then boots to Windows menu (see below)
Windows Boot Manager: (PO: TISHIBA THNSNJ128G8NU) - when i boot with this it displays the following: 

[COLOR=#282828][FONT=Roboto]Recovery[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]Your pc needs to be repaired[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]The boot configuration data for your pc is missing or contains errors[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]File: \EFI\Microsoft\Boot\BCD[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]Error code 0x000000f[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]You will need to use the recovery tools on your installation media. If you don't have any installation media (like a disc or USB device), contact your system administrator or PC manufacturer.[/FONT][/COLOR]
[COLOR=#282828][FONT=Roboto]Press ESC for UEFI Firmware Settings

ubuntu [/FONT][/COLOR](PO: TISHIBA THNSNJ128G8NU): when i boot with this it says "Invalid signature detected. Check Secure Boot Policy in Setup



I assume that the Ubuntu option is just a default thing because of the constant use of Ubuntu live, as all Ubuntu options were removed in efibootmanager.
What is the next thing to do and how do I do it?

---

### Post by oldfred on 2015-03-17
Unless you delete the ubuntu folder in the efi partition, the UEFI will keep adding it to your UEFI menu and of course it will not work since you deleted all the Ubuntu partitions.

Your issue is with Windows. Did you make a Windows repair flash drive? Then you need to use it to make repairs, or if when booting Windows does f8 get you into a repair console?

       [URL="http://www.eightforums.com/"]http://www.eightforums.com/

[/URL]
 Windows 8 UEFI Repairs
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
[http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html](http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html)
Create Windows 8 Repair flash drive, must be FAT32 to boot in UEFI mode:
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

My last Windows install was XP back in 2006, and have not used XP for several years. :)


[URL="http://www.eightforums.com/"]
[/URL]

---

### Post by alexaron17 on 2015-03-17
So I now need to create a system repair flash drive and then follow UEFI repairs instructions?

Will this give me the correct repair drive? [http://windows.microsoft.com/en-ZA/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-ZA/windows-8/create-reset-refresh-media)

---

### Post by oldfred on 2015-03-17
Do not know if that is just for reinstalling or includes a repair console??

---

### Post by alexaron17 on 2015-03-17
It should do so. Busy creating installation media now, then will follow instructions. Will report back here when ready. (crossing fingers)

---

### Post by alexaron17 on 2015-03-18
I HAVE SUCCESSFULLY BOOTED INTO WINDOWS!
I am so relieved. Thank you for all your help. My final question - what must I do to get rid of Linux for good now so that this issue doesn't happen again?

---

### Post by oldfred on 2015-03-18
If you have followed the suggestions in post #8, then you should not have any references to Ubuntu. 
But even if you leave those, they do not work or will only give errors if you tried to use them and would not change Windows.

---

### Post by alexaron17 on 2015-03-18
Okay, thanks so much for all your help, Sir. I am very thankful. Sorry for the times I may have been irritating :p.

---

