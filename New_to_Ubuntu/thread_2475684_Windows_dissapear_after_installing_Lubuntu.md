---
title: "Windows dissapear after installing Lubuntu"
date: 2022-06-04
forum: New to Ubuntu
---

### Post by linuxbeginner2 on 2022-06-04
I have installed Lubuntu 22.04 LTS today and I realize that I cannot dual boot my Windows 10, but the data are not destroyed(like E: and F: ), I can see that after opening the Lubuntu file manager. I think the Windows is still on my machine, but I simply cannot access it. After some time searching I found [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). I do the instructions, then I get this link: [https://paste.ubuntu.com/p/gPDw46XSQy/](https://paste.ubuntu.com/p/gPDw46XSQy/). I want to boot Windows again, so, can I click the **Recommended repair** button on the **boot-repair**? Or there are another solution?
Btw, I even go to my BIOS Asus X302U laptop by pressing F2, and go to boot menu, but I don't see anything like Windows. Is it a sign that my Windows is removed?

---

### Post by ajgreeny on 2022-06-04
No, do not use the Default repair at the moment as that can occasionally cause more difficulties. Wait for others who know Boot-Repair better than me to give you answers before doing anything else.

Your problem seems to be that Windows 8 or 10 was installed, very unusually,  in legacy BIOS mode but your Lubuntu is in UEFI mode making dual booting nearly impossible.  If you upgraded to Win 8 or 10 from Win 7 which was normally installed in legacy BIOS mode, your new Windows would also be legacy BIOS.

However computers have a keyboard key that can be pressed at power-on in order to choose which boot device should have boot priority.  You should be able to find the key to use in the computer or motherboard manual.  

Other users here may also be able to help with this boot menu key if you let us know what model of computer you have, but often it is F8 or F11.

---

### Post by Impavidus on 2022-06-04
First of all, have you got excellent backups of all your personal files? You say you can still access your Windows partitions, so if you have no backups, this is the time to make them. Put the backups on an external drive, safely remove it (in the file manager right click on the drive, then click eject; exact words may be slightly different on Lubuntu) and unplug it.

This is weird. Your hard drive uses GPT partitioning, but Windows appears to be installed in legacy mode. For Windows there are only two possibilities: legacy mode on MBR drives or EFI mode on GPT drives. Ubuntu also allows legacy mode on GPT drives, which triggers the creation of a bios_grub partition. There is a partition of that type, but that is mounted (according to fstab) as the efi partition. bios_grub partitions can't be mounted. An efi partition is needed on systems in EFI mode, but the installer creates one anyway these days, even if you install in legacy mode.

I can't say for sure what could have happened during installation. Was this a computer with Windows 8+ preinstalled when you bought it from a retailer? In that case it must have been installed in EFI mode. If it was upgraded from Windows 7 or before, it was probably legacy mode. Can the hard drive partitioning have been changed from MBR to GPT? Seems unlikely without wiping the entire hard drive. Any chance you have changed your computer from legacy mode to EFI mode?

Dual booting Windows 8+ and Linux in legacy mode is fragile, in particular on a single drive. Best to keep both an Ubuntu live disk and a Windows repair disk at hand. Actually, best to keep them at hand anyway. Better use EFI mode, if you can, but you cannot convert an already installed operating system from one mode to the other.

Have you tried switching to legacy mode? I don't think Lubuntu will boot then. It's a long shot, as Windows doesn't look like it's properly installed in legacy mode, but worth a try as this won't do damage. Just switch back to EFI mode if it doesn't work. But first make sure you've got those backups.

Boot-Repair can do some basic Windows repairs, which may sometimes work, but it says that Windows is installed in legacy mode and that Boot-Repair's default repair can only do its job when Boot-Repair is booted in legacy mode too. It remains to be seen whether that will work.

Worst case scenario is that you have to reinstall both Windows and Lubuntu. Have you got a Windows install disk?

---

