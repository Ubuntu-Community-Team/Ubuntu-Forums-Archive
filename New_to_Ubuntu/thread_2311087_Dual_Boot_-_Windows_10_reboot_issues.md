---
title: "Dual Boot - Windows 10 reboot issues"
date: 2016-01-24
forum: New to Ubuntu
---

### Post by dwilkens on 2016-01-24
Windows 10 - Ubuntu 15.10 dual: No Ubuntu after W10 shutdown, not restart

Problem:

If I do restart Win10 and start Ubuntu (instead of W10) the Grub starts Ubuntu 15.10 without issues. 

 If I shutdown Windows 10 instead, Ubuntu does not boot. Grub starts, then total failure. No visible reason. 

I can reproduce it as often as I like. 

Starting Windows 10 after that incident is fine! 

Starting Ubuntu does NOT work at all.... 

EXCEPT I shut down Windows-10 with a RESTART. 

Problem: 

Windows 10 - Ubuntu 15.10 dual boot gets f***ed up by Windows 10. No Ubuntu after W10 shutdown. 

Why?? 

SOLUTION / The answer is: The Windows 10 shutdown is NO shutdown. It is a hibernation state. The boot sector gets poisoned by Windows-10 after entering the Hibernation state and shutting down the hardware. 

So Grub / Ubuntu can not handle it, the boot sect is malformed.

Solution: 

Go to Windows 10 settings and disable the Fast Boot option in the Energy settings. 

In German it is "Schnellstart aktivieren (empfohlen)". NO NOT CHECK!!! This option kills Ubuntu boot! 

Sie finden diese Einstellung in Windows-10 Energieoptionen / Systemeinstellungen / Einstellungen fuer das Herunterfahren als ersten Punkt. 

Then it works fine. 

Applies to earlier Windows 8 and 7 too.

---

### Post by pfeiffep on 2016-01-24
@dwilkins please start your own thread for answers

---

### Post by oldfred on 2016-01-24
Moved to own thread.

What hardware, brand/model, video card/chip?
Is Secure boot off?
Is Fast start up off in Windows?
Is Fast boot off in UEFI?

Post this to see details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

