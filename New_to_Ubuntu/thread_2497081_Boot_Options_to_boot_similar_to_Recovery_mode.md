---
title: "Boot Options to boot similar to Recovery mode"
date: 2024-04-22
forum: New to Ubuntu
---

### Post by afoolishmoon on 2024-04-22
I have an issue where, due to some damage/corruption to my motherboard, Ubuntu will not boot. It gets frozen after displaying the attached text. I can successfully boot if I first launch Recovery (which appears to load drivers normally) then tell Recovery to try a normal boot. It's just annoying to do this every time I start the OS. I'll explain more about my motherboard damage at the end, but I don't think it's important, I just want to change my boot options to disable whatever checks recovery skips (ACPI? Others?). I'm only a hobbyist on Linux operating systems, so this is a little deeper than I've waded in before. I tried applying the *noacpi *boot option on a custom boot, but that alone did not seem to fix it... Or I did it wrong.


**QUESTION**
How do I change the default boot in GRUB to ignore as many checks as possible? Hopefully to make it like the Recovery boot.


**ERROR**
I'm attaching an image of the boot here, which reveals a lot of ACPI errors, but here's a transcription of some of the important items.


***[ 0.201605] ACPI BIOS Error (bug): Could not resolve symbol [\_SB_.PC00.TXHC.RHUB.SS01], AE_NOT_FOUND (20230331/dswload2-162)***
***[ 0.201619] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20230331/psobject-220)***
***...***
***/dev/sda2: recovering journal***
[I][B]/dev/sda1: clean, 291158/655360 files, 2414155/26214400 blocks
[/B][/I][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293673&stc=1[/IMG]


**ABOUT MY MOTHERBOARD**
Long story short, this laptop's motherboard has some serious issues. The onboard M.2 port is blown, won't recognize any drive. Most of the pripherals and USB ports also are blown. The BIOS won't update, seems to find the vendor's BIOS files "invalid." I suspect because it's half dead. I'm booting this laptop off of my one good port (USB 3.0) using Ubuntu on a low-profile usb drive. The laptop has fairly decent hardware that still works, which is why I haven't trashed it.

---

### Post by grahammechanical on 2024-04-22
Have you tried entering the BIOS/UEFI settings utility and disabling the hardware that you think is faulty? I do not think that those messages are coming from the Grub bootloader. The motherboard should run its own Power On Startup Test (POST). That action may produce error messages. Or those messages could be coming from the Linux kernel as it loads. By the time Linux is loading Grub has finished and exited from system memory.

Regards

---

### Post by afoolishmoon on 2024-04-22
Absolutely. I don't think the errors are from grub. I think they are more Ubuntu. But I want to skip the checks causing them.

Many of the components, such as the primary storage mount can't be disabled, but I've removed the M.2. I can disable the bad USB ports, but that also would kill the last working one.

Again, I reiterate: The system boots fine, IF I first boot into recovery. So there's got to be a way to skip the normal health checks and boot the OS like recovery mode does.

I'm just trying to save myself the pain of booting this way:
1. Boot and let it fail. Hard reset.
2. Catch the boot menu and boot to recovery.
3. Once recovery boots, tell it to boot normally (since all the drivers are already loaded this works)

---

### Post by afoolishmoon on 2024-04-23
I discovered the solution. Appears to work normally now. Putting what I did here for anyone else that has a lot of ACPI errors during boot, but can get into Recovery normally. The key appears to be using the **nomodeset** boot option.

**Edited the GRUB config:**
[I]sudo nano /etc/default/grub
[/I]
**Changed the* GRUB_CMDLINE_LINUX_DEFAULT *to have the below settings:***GRUB_CMDLINE_LINUX_DEFAULT="ro nomodeset"*

[B]Saved the changes to the file:
[/B]*Ctrl-X, Yes*

[B]Ran GRUB update:
[/B]*sudo update-grub*

---

