---
title: "USB-FDD; need to format as USB-HDD"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by rook3 on 2014-05-27
64 gig USB(fd0,msdos) detects as USB-FDD. Want USB-HDD detected(Since my mobo has "quirks").

Fat32, I tried formatting via unetbootin and also gparted, boot/lsa flags.

Makebootfat: 
Can't figure out how to makebootfat(Supposedly you can make the USB support zip/flash/HDD standards all at once, even). I'm sure I'm getting the commandline options wrong or something. 

Do I need boot sector images? I just want it to detect as HDD.  

Do I need a directory image? I don't really want crap on the flash. 

Bootice: 
Don't know that bootice(recommended by yumi/pendrivelinux) is safe. 
-----------------------------------
Thanks for the help :-) This has been a problem for a good while, took me until now to realize that a detected USB-HDD should work on my BIOS, even with the quirks.

---

### Post by Luke M on 2014-05-27
Your problem isn't clear to me. What is "detecting" your USB? Is the problem that your BIOS won't let you boot from USB? What are you trying to put on the USB - the ubuntu installer, or ubuntu itself, or something else?

---

### Post by rook3 on 2014-05-28
Ubuntu, YUMI(Really my ultimate goal), knoppix, kali... I wish for the USB to be properly detected by my board, it doesn't really matter what goes on it. 

The bios can't boot USB-FDD(Which the USB is detected as), but can boot USB-HDD, and it should be possible to format it as such from what i've read. I'm not sure how to do it with [FONT=times new roman]makebootfat[/FONT], but it's supposed to be possible :) It's already flagged "bootable", and already formatted as FAT32 via [FONT=times new roman]gparted[/FONT]- but that isn't enough. [FONT=times new roman][FONT=arial]As stated[/FONT], Unetbootin [FONT=arial]did not work.[/FONT] Yumi.gambas[/FONT] isn't working. When formatted via unetbootin, the image boots properly on other systems, and is detected by this booted system(Ubuntu). But will not boott on this system.

I don't believe it can boot on this board unless it is formatted to the USB-HDD protocol. 

Succinctly:
The problem is that a USB is being detected as USB-FDD by the BIOS, preventing boot; I want a USB thumbdrive formatted/detected by the BIOS under the USB-HDD protocol. Otherwise it will throw boot errors. 

Sorry if I wasn't clear enough, I'm just now starting to figure some of this stuff out.

---

### Post by Luke M on 2014-05-28
Have you tried Plop Boot Manager? It allows you to boot from USB even if the BIOS doesn't support it.

[http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)

---

### Post by Vladlenin5000 on 2014-05-28
Succinctly, there's no USB-HDD specific format. If your BIOS doesn't work with your flash unit made with Unebootin or others, either update it, use PloP as previously suggested or ditch that old machine and get a new one.

---

### Post by mcduck on 2014-05-28
+1 to above. There is no such thing as "USB-FDD" or "USB-HDD"* formatting*. Those are different ways how the BIOS detects the USB drive, so they are related to the device itself and BIOS. The filesystem used has nothing to do with it, and therefore formatting can't help you. If your BIOS doesn't give you the options needed to boot from the device, the only ways to fix it would be changing the firmware of the device to emulate USB-HDD instead (unlikely to be doable in any easy way) or pick up a different USB drive.

---

### Post by matt_symes on 2014-05-28
Hi

+1 to the last two posters.

You never mentioned the make and model of the machine and what BIOS version is installed if whether you have looked for a BIOS update or not.

Don't hold your breath that a BIOS update would fix it though.

Kind regards

---

### Post by oldfred on 2014-05-28
There are some issues by brand:
 Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.

My older Gigabyte has all the USB-HDD, USB-FDD etc choices, none of which work. But I always see my correctly configured bootable flash drives as another hard drive in the list of hard drives. And I have used FAT32, NTFS and Linux formats all using grub2 to boot.

---

### Post by rook3 on 2014-05-29
GA-78lmt-s2p

@Oldfred- 
What you've stated may have been my issue. If it was, thanks a ton :-) I  knew being detected as HDD was key based on other users, for some  reason it was being detected as FDD. No idea why it's configured properly  now and it wasn't before.

Not sure what the heck changed. Also not sure if this will help  anyone else in the future with similar issues; marking this as solved,  but I'll keep subscribed if someone with similar problem needs any  info/testing from my end.

Formatted(yet again), I tried makebootfat with --mbrfat and other  options (yet again), threw super  grub boot on, and then went from there... it's being recognized as  USB-HDD now. 

@Other folks- 
Egads. Sorry for the lack of information and thanks a ton for the responses. USB-HDD/FDD/ZIP/ETC. drives are all supposed to work fine, gigabyte is evidently really quirky for USB boots.

---

