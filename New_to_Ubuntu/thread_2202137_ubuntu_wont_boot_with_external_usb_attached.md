---
title: "ubuntu wont boot with external usb attached"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by jpbarroso on 2014-01-27
Hi! I've ubuntu 13.10 and win8 in dual boot in a laptop.
If 1TB external usb3.0 drive is attached before switch on the computer, ubuntu doen't boot. Grub menu appears and win8 has no problem, but ubuntu reamins in black screen... (i don't know if it hangs or is looking usb drive)
I've checked boot options and all is ok, boot order is correct,  usb boot is disabled...
Any suggestions? 
thanks!

---

### Post by sudodus on 2014-01-27
This is strange.

- What is the boot order in BIOS/UEFI?
- What is on the usb3.0 drive? A bootloader, so that the computer boots to it rather than the the internal drive?
- How did you install Ubuntu?

---

### Post by oldfred on 2014-01-27
I might check log files, particularly dmesg.

 gksudo gedit /var/log/dmesg

It does seem like a mount issue on USB, but sometimes UEFI/BIOS and USB3 ports have issues.

---

### Post by jpbarroso on 2014-01-30
Thanks for the support, I was wrong, it mustn't be an ubuntu issue, perhaps a lenovo-uefi issue.
If i plug hd on usb2.0 -> no problem, if i plug on usb3.0 -> black screen with lenovo logo, before grub. But in bios i have "usb boot" disabled, so strange.

---

