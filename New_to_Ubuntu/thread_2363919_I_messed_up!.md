---
title: "I messed up!"
date: 2017-06-16
forum: New to Ubuntu
---

### Post by waldxn on 2017-06-16
So I am VERY new to ubuntu. I made the bootable install usb for the newest ubuntu. I now cannot access Windows 10!!! I was trying to dual-boot my computer. I downloaded boot-repair, but I get this message:

The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will enable this feature. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode.

I don't know how to fix this at all. Please Help!!!!!

EDIT: I would prefer to remove Ubuntu completely, but I will need to boot to windows before that is an option.

---

### Post by oldos2er on 2017-06-16
What make/model of computer are you using? Usually to get into BIOS you need to hit F2 or F12, but it varies with different computers.

---

### Post by waldxn on 2017-06-16
I can get into the BIOS fine. The motherboard I am using is the Asus H110M-A/M.2

This is very stressful. I hope I can get helped.

---

### Post by oldfred on 2017-06-16
If a new system and UEFI, you can always directly boot Windows from UEFI's boot menu, often f10 or f12 but varies check your manual if you do not know. And if still issues, that is only related only to Windows and then you may need your Windows repair/recovery flash drive. Most Windows repairs cannot be done from Linux.

How you boot install/repair media UEFI or BIOS is then how it installs or repairs. New UEFI systems can boot in both newer UEFI or ancient BIOS boot modes. UEFI should show two options to boot flash drive UEFI:flash and flash (or BIOS) where flash is name/label/brand of flash drive.
But then to boot an install you have to have system set to boot in the same modes as you just installed. But if Windows 10 pre-installed it will be UEFI and then you never want to boot in the old BIOS mode.

---

### Post by waldxn on 2017-06-16
I cannot boot windows from the UEFI menu. I have downloaded the Windows 10 iso from the windows website and will attempt to boot from my usb after placing the iso onto it. I hope it works. I feel like I've pretty much bricked my computer.

---

