---
title: "Installed ubuntu to second hdd and now 1st hdd with windows won't boot normally"
date: 2016-12-08
forum: New to Ubuntu
---

### Post by RToz on 2016-12-08
I recently did a clean install of Windows 10 on a SSD hard drive, which worked fine.  Restarted and booted up fine.
However, after I did a clean install of ubuntu on a second hard drive, my Windows 10 won't boot up normally even when I set the SSD to boot first in BIOS. 

I get the message that Windows was not able to boot properly, and to insert my Windows installation CD.  I tried to repair Windows through the CD to no avail.  The only way I can boot Windows 10 is if I rearrange the boot priorities in BIOS so that my second HDD with ubuntu boots first.  From the Grub menu, I have the option to boot Windows 10.  Which works.

However, I most likely won't be using ubuntu very often, and Windows 10 will be my primary OS.  What's causing this issue? I also don't mind leaving the HDD priorities as is, as long as my computer can boot quickly to Windows (any tips on that? I know I can reduce the time the grub menu stays up, and I guess I can change the default option to Windows boot), but I'd rather know what's causing this issue.

Thanks!

---

### Post by oldfred on 2016-12-08
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

What brand/model system? and what video card/chip?

---

