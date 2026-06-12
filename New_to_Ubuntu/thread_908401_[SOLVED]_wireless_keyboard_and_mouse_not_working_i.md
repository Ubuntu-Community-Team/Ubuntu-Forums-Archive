---
title: "[SOLVED] wireless keyboard and mouse not working in boat loader (GRUB)"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by kachamanandrao on 2008-09-02
I have wireless key board and mouse. I am unable to select the choice of operating system of boot loader of ubuntu linux using the wireless keyboard? wireless keyboard and mouse works only after booting into either linux / windows! please let me know if any one has solution for making wireless keyboard/mouse work while selecting operating system?

---

### Post by Titan8990 on 2008-09-02
Can you use the wireless keyboard/mouse to change BIOS options?

Do you have USB keyboard/mouse support enabled in your BIOS?

---

### Post by lucho64 on 2008-09-02
I have the same setup, a wireless mouse/keyboard. Mine works though. I don't think that grub knows anything about keyboards that the bios does not tell it. Does it have one of those USB "base station" things? I assume it looks to the bios as just another USB keyboard. I would go to the bios and look for any option to enable the USB keyboard during boot (USB legacy support seems to be the keyword to look for)

---

### Post by kachamanandrao on 2008-09-02
> **Titan8990 said:**
> Can you use the wireless keyboard/mouse to change BIOS options?

Do you have USB keyboard/mouse support enabled in your BIOS?
your suggession worked. I just enabled usb controll in bios. and key board started working in grub menu.
Thanks a lot !

---

### Post by kachamanandrao on 2008-09-02
> **kachamanandrao said:**
> your suggession worked. I just enabled usb controll in bios. and key board started working in grub menu.
Thanks a lot !

Exactly, enabling usb legacy has worked. Thanks to both titan8990 and lucho64

---

