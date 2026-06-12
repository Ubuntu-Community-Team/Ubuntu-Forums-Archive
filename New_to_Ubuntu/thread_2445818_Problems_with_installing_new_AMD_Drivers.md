---
title: "Problems with installing new AMD Drivers"
date: 2020-06-19
forum: New to Ubuntu
---

### Post by llamarr on 2020-06-19
Hello! Yesterday I was playing some games and it seems my drivers had decided to stop working. I deleted the old drivers and tried installing new drivers from AMD's site but while setting them up i''m still told to uninstall the old drivers before installing. Using the "Uninstall" option given doesn't seem to work and just says "command not found" and so when I try to uninstall it by deleting the old files everything is owned by root and even if I make myself owner i'm only able to view them and not able to delete it. I also want to upgrade to 20.04 but to do that I need to get the newest updates and those updates want to update the drivers but seems since I deleted the old ones it just shows and error and decided not to update anything. 
Graphics Card: 50th Anniversary 5700xt

---

### Post by dino99 on 2020-06-20
Amd drivers are already built into the kernel; you does not need to download/install it from Amd site    [https://www.reddit.com/r/linux_gaming/comments/ha777j/ubuntu_driver_install/](https://www.reddit.com/r/linux_gaming/comments/ha777j/ubuntu_driver_install/)

If you have installed something, never delete it but purge it to avoid settings/links ghosts

---

### Post by Impavidus on 2020-06-20
AMD drivers are built-in if you use at least kernel 5.3, like on Ubuntu 19.10, 20.04 or 18.04 with HWE. If you use Ubuntu 18.04 without HWE, you're still on kernel 4.15, where you can use AMD's proprietary drivers. 16.04 can even use kernel 4.4. Typically you install those proprietary drivers using the "Additional drivers" tool, but it looks like you did something different.

Driver related files on your system are expected to be owned by root. That doesn't actually affect you ability to remove them, as that's governed by the permissions on the directory. Messing with those is not recommended and removing the files is not the clean way to remove the drivers anyway.

May I suggest a clean install of 20.04? In my experience upgrades work quite reliably, but if you have to fix things before you can attempt the upgrade, I wouldn't bother. A fresh install is easy.

---

### Post by Autodave on 2020-06-20
+1 w/Impavidus: do yourself a favor and save your blood pressure: do a clean install of 20.04.  Make sure that you back up everything first!!

---

