---
title: "Cannot remove Ubuntu 12.10 (64 bit)"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by Pavonis on 2012-12-10
After spending a couple of days trying to install a 64 bit system, I discovered that some proprietary software I must use only works in 32 bit Ubuntu. So I have to downgrade.

But after 64-bit  12.10 Ubuntu was installed, the computer no longer detects the USB or the DVD drive in the boot manager! Arggh!!! It had been working when I had Windows, a broken 12.04, and no OS at all. I have a HP Pavilion dm1 laptop.

It's okay if my computer is completely wiped clean and all data lost. I just need a 32-bit install.

---

### Post by oldfred on 2012-12-10
Do you have to do what this user did?

[http://distrowatch.com/weekly.php?issue=20121126#qa](http://distrowatch.com/weekly.php?issue=20121126#qa)

> In short, to get to the point where we can attempt to boot an  alternative operating system we need to know our way through six steps:         
[LIST]
[*]Boot machine while pressing F10
[*]Find Secure Boot in the menu tree, ignore warnings
[*]Disable Secure Boot feature
[*]Enable legacy boot options
[*]Enable specific legacy devices, such as USB devices
[*]Save and reboot while holding down F9
[/LIST]
          Also in UEFI/BIOS you have to disable fast boot or quick boot that seems to turn off access to any other device to make boot faster. But then you only can boot Windows.

---

### Post by Pavonis on 2012-12-11
Thank you.

Merely enabling legacy boot is looking very promising...

---

### Post by Pavonis on 2012-12-11
Okay, I enabled legacy support and then F9ed to a boot manager with my external drive. Now the 32-bit system is installing :P.

---

### Post by mlentink on 2012-12-11
> **Pavonis said:**
> I have a HP Pavilion dm1 laptop.

Me too. But I've never been able to find the DVD-drive on mine... ;-)

---

