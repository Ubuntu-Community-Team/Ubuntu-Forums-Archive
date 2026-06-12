---
title: "32-bit image workaround for UEFI: debootstrap?"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2013-09-13
[QUOTE=YannUbuntu]Original message at [launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1025555").

Potential work-around:

Disable secure boot, prepare usb-stick with 32bit grub-efi image installed, boot of that and perform manual - "debootstrap" based installation: manually partition, manually install grub-efi, debootstrap packages, attempt to boot.[/QUOTE]

How do you preform "debootstrap"? And how can you manually install grub-efi-ia32 in a live USB already made for BIOS-only machines (32-bit)?
Just curious, as I would like to have ubuntu 32-bit in one of my machines.:)

---

### Post by oldfred on 2013-09-13
You might want to read this:
 Don't ship 32-bit UEFI firmware on x86
    [http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)
Or you might be better off going and getting a beer. :)

---

### Post by Jonathan Precise on 2013-09-20
At 9/20/2013, Jonathan wrote:

| Update: I'm actually running ubuntu 12.04.3 LTS 32-bit on an EFI Virtual Machine!!!!!
| 
| =====Current-workaround=====
| Note: not tested in dual-boot!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
|
| Enable CSM. Install in BIOS mode (mounting the EFI partition as /boot/efi). Reboot. Manually install grub-efi. Reboot, select UEFI mode. Let grub and ubuntu boot!!!
|
| If dropped to EFI shell, enter "exit" (no quotes).
| Scenario 1: Ubuntu boots after "exit"!
| Scenario 2: You must boot from "EFI file". Select 'EFI'. Select 'ubuntu'. Select "grubia32.efi". Ubuntu boots!
| =========================
| -----------------------------------------
| =====Future-workaround=====
| 
| I shall make a remastered ISO to work with 32-bit/UEFI-only machines. For now, follow the workaround above.
| 
| ---OR---
| 
| Wait a few days for the ISO to be finished and published.
| ========================
| Bug [lpbug]1025555[/lpbug], comments 44 and 45.

---

