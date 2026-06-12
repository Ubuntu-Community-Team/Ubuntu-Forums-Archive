---
title: "Can't get reboot to work"
date: 2024-01-23
forum: New to Ubuntu
---

### Post by mdsmith1 on 2024-01-23
I have downloaded the Ubamtu .iso file. 

I have downloaded unitbootin windows and have rebooted my machine (Windows 11).

By using F12, I have been able to interrupt the boot process and get the Boot Manager to come up.  Its a DOS screen with up and down arrows that I think will allow me to select the Boot Drive. (which is D:) but the DOS Boot Manager screen is dead.  My keyboard arrows are not able to do anything. 

When I press ESC for default, it takes me to drive C: which I don't want.

Mike

---

### Post by oldfred on 2024-01-23
What brand, model computer? What video card/chip?

Did you create USB flash drive correctly as it has to be seen as bootable to be in UEFI boot menu.
Some systems also have another security setting on USB, to allow boot from USB. Check UEFI settings.

[https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview)
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)
Install:
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

---

### Post by MAFoElffen on 2024-01-25
That is still in the BIOS Boot Menu. Was that from a cold boot? 

If so, then that is a BIOS Image issue.

---

