---
title: "Computer Freezes When Booting from USB"
date: 2017-08-18
forum: New to Ubuntu
---

### Post by j.weaver on 2017-08-18
I've attempted to boot Ubuntu 16.04 from a USB drive on my current laptop that is running Windows 10. I am able to successfully boot up Ubuntu on my older computer that runs Windows 8 with the same USB drive, and have not had any problems with it. When I attempt it on my newer computer, however, it freezes on the Ubuntu loading screen—always at the exact same time. What should I do?

---

### Post by Bucky Ball on 2017-08-18
Welcome. Do you have a wireless USB stick or any other device connected via USB and switched on? If so, pull them out and try again. This one is a preliminary and probably not the issue. Wireless usually doesn't cause a hold up, but can. A switched on USB hard drive can cause a bit of confusion, though. Best not to have it connected then anyway.

What is the make and model of your laptop? Does it have Win installed? In UEFI or BIOS mode? You will need to check this in the BIOS. The mode that is being used by Windows MUST be used when you boot the Ubuntu install USB. What mode was used when installing to the drive on the other machine? Same mode as the laptop Win install, if there is one?

How are you trying to boot that drive when you start the machine? You select it from the BIOS?

The more info you can give when posting the more help we can give you. See the pink link in first line of my signature. ;)

---

### Post by j.weaver on 2017-08-18
Thank you for your prompt response. I will try to provide you with the necessary information to the best of my ability.

> **Bucky Ball said:**
> Welcome. Do you have a wireless USB stick or any other device connected via USB and switched on? If so, pull them out and try again. This one is a preliminary and probably not the issue. Wireless usually doesn't cause a hold up, but can. A switched on USB hard drive can cause a bit of confusion, though. Best not to have it connected then anyway.
No, I don't have any wireless USB connections.

> What is the make and model of your laptop? Does it have Win installed? In UEFI or BIOS mode? You will need to check this in the BIOS. The mode that is being used by Windows MUST be used when you boot the Ubuntu install USB. What mode was used when installing to the drive on the other machine? Same mode as the laptop Win install, if there is one?

How are you trying to boot that drive when you start the machine? You select it from the BIOS?
My current laptop is a model GL552VW ASUSTeK laptop. My older laptop is a Hewlett-Packard 15 Notebook. Both are in UEFI mode as far as I can tell. In both of my laptops I just accessed the boot menu and chose to boot from a removable device.
 [ATTACH=CONFIG]276436[/ATTACH]

This worked all right for the older laptop, but for the newer one it always froze at this exact screen.
[ATTACH=CONFIG]276437[/ATTACH]

---

