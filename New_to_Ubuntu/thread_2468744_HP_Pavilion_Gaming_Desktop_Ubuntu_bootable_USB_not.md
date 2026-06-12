---
title: "HP Pavilion Gaming Desktop Ubuntu bootable USB not working"
date: 2021-11-09
forum: New to Ubuntu
---

### Post by yarkingulacti on 2021-11-09
[COLOR=#232629][FONT=-apple-system]I've been trying to replace [/FONT][/COLOR]Windows 10[COLOR=#232629][FONT=-apple-system] with [/FONT][/COLOR]Ubuntu 21.10[COLOR=#232629][FONT=-apple-system]. But I've encountered so many problems. Basically, I followed a bunch of online tutorials and found out that I needed to create a bootable USB disk, which I did in every possible way with [/FONT][/COLOR]Rufus[COLOR=#232629][FONT=-apple-system] on my [/FONT][/COLOR]Windows 10[COLOR=#232629][FONT=-apple-system] device. Then disabled [/FONT][/COLOR]Secure Boot[COLOR=#232629][FONT=-apple-system], which is the only option related to bootable medium issues listed in forums that I can disable/enable, and plugged in my USB stick, entered BIOS, changed the boot order, and selected [/FONT][/COLOR]Ubuntu[COLOR=#232629][FONT=-apple-system] from [/FONT][/COLOR]Grub[COLOR=#232629][FONT=-apple-system], nothing that worked as it supposed to be after that. In forums and blogs, after people select the [/FONT][/COLOR]Ubuntu[COLOR=#232629][FONT=-apple-system] option, their Ubuntu just proceeds to installation steps but mine is stuck at [/FONT][/COLOR][this]("https://imgur.com/a/Z3njjL7")[COLOR=#232629][FONT=-apple-system] screen. I hope I made myself clear, [here is my computer specs]("https://imgur.com/a/YVkTUJh")[/FONT][/COLOR][[COLOR=#232629][FONT=-apple-system].[/FONT][/COLOR]]("https://imgur.com/a/YVkTUJh")

---

### Post by ActionParsnip on 2021-11-09
Have you tried using a USB 2.0 port instead of USB 3.0 ?

---

### Post by ActionParsnip on 2021-11-09
Have you tried a different USB copying application? Did you at least MD5 test the ISO you downloaded so that you know it is complete and consistent (Or use Torrents to download the file)?

---

### Post by tea for one on 2021-11-09
According to your image, your USB stick is Toshiba Transmemory?

I purchased one of these a few years ago and it constantly failed as a bootable device.
I simply use it for storage now and it is remarkably slow.
Not all USB thumb drives behave identically.

I would use another USB stick?
Also, perhaps try a different USB port on your PC.

---

### Post by yarkingulacti on 2021-11-09
Yes, initially we tried with a fresh SanDisk 2.0 USB Flash disk.

> **ActionParsnip said:**
> Have you tried using a USB 2.0 port instead of USB 3.0 ?
Initially we tried with a fresh SanDisk 2.0 USB driver.

> **ActionParsnip said:**
> Have you tried a different USB copying application? Did you at least MD5 test the ISO you downloaded so that you know it is complete and consistent (Or use Torrents to download the file)?
Tried 6 of them already; Etcher, Rufus, Universal Image Bootlader, [FONT=Google Sans][COLOR=#202124]UNetBootin, Win32 Imager and Ubuntu's Startup Disk Creator from my other Ubuntu PC.[/COLOR][/FONT]

> **tea for one said:**
> According to your image, your USB stick is Toshiba Transmemory?

I purchased one of these a few years ago and it constantly failed as a bootable device.
I simply use it for storage now and it is remarkably slow.
Not all USB thumb drives behave identically.

I would use another USB stick?
Also, perhaps try a different USB port on your PC.
Tried another USB driver, still the same.

---

### Post by ActionParsnip on 2021-11-09
If you set the BIOS to failsafe default settings, does it help?

---

### Post by tea for one on 2021-11-09
> **yarkingulacti said:**
>  plugged in my USB stick, entered BIOS, changed the boot order, and selected Ubuntu from Grub 

As you reached the Grub menu for a live session, can you try [COLOR="#0000FF"]Ubuntu (safe graphics)[/COLOR]?

---

### Post by yarkingulacti on 2021-11-09
> **tea for one said:**
> As you reached the Grub menu for a live session, can you try [COLOR=#0000FF]Ubuntu (safe graphics)[/COLOR]?
Tried already, didn't worked.

---

### Post by tea for one on 2021-11-10
Not making much progress yet, but let's go back to basic settings.

Please confirm that all the following have been addressed:-

Verify the ISO

_UEFI settings_

Disable Secure Boot
Disable Fast Boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology)
Disable Optane memory and storage

_Windows 10_

Turn off Bitlocker 
Do not have any drives encrypted during Ubuntu installation process
Disable Fast Start Up i.e. Windows is not hibernating
Some Windows updates turn on hibernation automatically
Disable applications which manage Intel Optane memory & storage

---

### Post by ActionParsnip on 2021-11-11
If you can give the exact model then there may be a BIOS update
[https://support.hp.com/gb-en/drivers/selfservice/hp-pavilion-gaming-desktop-pc-tg01-2000a/2100367769](https://support.hp.com/gb-en/drivers/selfservice/hp-pavilion-gaming-desktop-pc-tg01-2000a/2100367769)

There is a BIOS from last month. May help the situation

---

### Post by ActionParsnip on 2021-11-11
Obviously if yours is not the HP Pavilion Gaming Desktop PC TG01-2000a and is slightly different then DO NOT use that BIOS and find the right one to use.

---

### Post by saraah34 on 2021-11-15
try different usb port

---

### Post by yancek on 2021-11-15
>  [COLOR=#232629][FONT=-apple-system]Basically, I followed a bunch of online tutorials [/FONT][/COLOR] 

Stick with one problem until it is resolved and then move on, this doesn't help.  Also, don' follow a bunch of online tutorials, any idiot can post anything online.  I would use an official documentation site fir Ubuntu.  The link below descries in detail dual booting windows 10 and Ubuntu UEFI.  You first need to verify that your drive(s) are GPT and your install is UEFI.  If you have windows 10 running, Go through the process described at the link below to install Ubuntu alongside windows 10 UEFI   It's simple enough to remove windows later if you want.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I see you also have an HP Pavilion.  When you cold boot the HP, you should be able to access the Boot Options and BIOS Firmware by tapping the Esc key until you see a screen with a number of messages, one of which is to use the F9 key which gives you Boot Options.  Selecting from this option is a one time change, it will not carry over on reboot.  If you have an EFI capable machine which can also boot in Legacy/CSM mde, you should see under UEFI options the name of the flash drive (Toshiba, Sandisk, Lexar, ...) and that is what you select to boot the flash drive.  The System Information page you show in your iage is not much use for booting.

If you do not have the Esc, F9 and F10 optiions and no reference to UEFI in the BIOS firmware, your hardware may not be UEFI capable.

---

