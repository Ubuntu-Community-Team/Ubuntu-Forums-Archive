---
title: "Installing W7 with already installed xubuntu how to grub"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by FillWebs on 2013-04-21
Hi,

I have I'm enough skilled with unix/linux systems but i never had a experience with grub - only when it was preinstalled and i was not touching it, so bare with me.


Currently I'm running xubuntu on my laptop and i want to keep it, but i also want to install W7 next to it. I already prepared some unallocated space, better let the W7 format it to ntfs then linux. And i have my W7 installation prepared on USB drive.

But i know when i start to install it it will not install next to the linux but it will rewrite the bootloader so then the xubuntu will be still installed but i wont be able to load it since W7 will be loading by default.

Can you please give me easy guide how to setup my box befer or after the W7 installation that i will be able to access my xubuntu again. Also note that currently i don't have grub or lilo installed.


Thank you very much

---

### Post by Cheesemill on 2013-04-21
After you've install Windows you need to boot from a Ubuntu Live CD and run boot-repair.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by rushikesh988 on 2013-04-21
I had the same problem this link helped me
[Recovering Ubuntu After Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

