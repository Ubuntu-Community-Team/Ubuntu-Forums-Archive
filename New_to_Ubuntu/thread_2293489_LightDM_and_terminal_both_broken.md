---
title: "LightDM and terminal both broken"
date: 2015-09-05
forum: New to Ubuntu
---

### Post by LeCom on 2015-09-05
So I have a freshly installed Lubuntu 15.04 desktop as dual-boot with Windows, without any updates done. The live CD version (burned with 8x speed) works perfectly. However, the one I installed on my HDD crashes while booting. It shows the standart Lubuntu loading screen for a few seconds at first, and then switches to a console, showing this:

Starting version 219

[ OK ] Started Light Display Manager
[ OK ] Stopped crash report submission daemon
[ OK ] Started crash report submission daemon
Starting crash report submission daemon
[ OK ] Stopped crash report submission daemon
                                           [ FAILED ] Failed to start crash report submission daemon

Sometimes it also says something about a FIFO CPU underrun. I scanned the CD for errors and checked the MD5 of the downloaded .iso and everything is fine.

The recovery mode from the Advanced booting options seems to work. But if I select "continue booting", it shows the booting console, and strange graphical glitches (like horizontal/vertical half-transparent red lines) that change very quickly. The other booting mode does exactly the same as the standart booting mode.

 But now, I can't just reinstall LightDM because the tty terminals seem broken. When I log into any of them, they will show some text indicating that I logged in for 1/4 second or so, then clear the screen and ask me for login data again after 2-3 seconds.

  I'm using an x86 Dell laptop, with Intel hardware only. Windows wanted me to chkdsk C: after the installation, but works without any errors otherwise. GRUB2 works fine too.

Thanks in advance for any help.

---

