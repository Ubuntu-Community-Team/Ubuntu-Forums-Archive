---
title: "Ubuntu 8.04 does not start gui at startup (anymore)"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by brievenbus on 2008-08-10
situation:
Have dual boot Windows with Ubuntu 8.04 Desktop 32-bit.
I use dual screen on an old Matrox 450G graphics card.
Have Ubuntu setup to use two screens.
One of the VGA ports of the Matrox card died and now Ubuntu can't start the Gui anymore during startup.
It tries it several times and the reverts back to the command prompt telling me that it will try to start the gui again in 2 minutes (this failes of course).

how can I configure the grahics card from the command prompt to use single monitor on the still working VGA port.
(I do not really care that one port is not working anymore as this will become a server once I feel comfortable enough with Ubuntu)

Thanks!

Willem

---

### Post by cdtech on 2008-08-10
Boot into recovery mode and try the command:
```
sudo dpkg-reconfigure xserver-xorg
```
This will reset the xorg configuration file.

Hope this helps......

---

### Post by brievenbus on 2008-08-10
Thanks cdtech!

This did the trick.

brievenbus

---

