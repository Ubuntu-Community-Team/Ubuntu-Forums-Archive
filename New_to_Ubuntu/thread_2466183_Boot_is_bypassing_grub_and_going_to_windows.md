---
title: "Boot is bypassing grub and going to windows"
date: 2021-08-21
forum: New to Ubuntu
---

### Post by psychohermit on 2021-08-21
Hi Folks, 

I have about a 7 year old HP laptop with ubuntu and windows 10 installed.

I messed up my EFI ( or whatever it's called)  boot settings and boot is bypassing grub and going straight to windows.  I was curious and downloaded kubuntu to have a look see at the live DVD.

If I press shift while rebooting windows it boots to the select device to boot.  Boot from usb fails because there is no bootable DVD installed and it goes to the grub boot menu.  What do I have to set in bios to make that the default behavior again.  Darn newfanfged computer has me buffaloed.  Thanks in advance to any support you can offer.

--glenn

---

### Post by tea for one on 2021-08-22
> **psychohermit said:**
> boot is bypassing grub and going straight to windows.
Possibly a Windows update turned on hibernation?

Try shutting down Windows without hibernation
Uncheck Fast Start Up in Power settings/Shutdown settings

---

### Post by jeremy31 on 2021-08-22
Go into BIOS/System Config page and see if there is an OS Boot Menu, put ubuntu at the top and press F10 twice, save settings and then exit BIOS menu

---

### Post by psychohermit on 2021-08-22
I didn't have any options for which partition to boot in bios.  I an act of desperation I loaded the defaults and that seems to have cured it.  Thanks everyone for the replies.

--glenn

---

