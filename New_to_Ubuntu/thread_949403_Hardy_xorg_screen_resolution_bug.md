---
title: "Hardy xorg screen resolution bug?"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by jharadie on 2008-10-16
I have a secondary machine, Microtel 1.6G CPU, 1.5RAM, SiS chipset, that I want to make headless.  I did a fresh install of 8.04 alternate (because of the locales problem), temporarily using a Microtek 710S LCD monitor.  The only install glitch was Ubuntu wanted a screen res of 1280x1024, which the monitor didn't like; as soon as I lowered to 1024x768 everything was fine.  Installed all the updates, activated Vino.  Coming in from my main machine -with the secondary machine monitor still turned on- worked.  Rebooted the secondary machine, turning off the monitor.  When I came in again, screen res was 960x600 and I was not allowed higher.

I've searched the forums and tried all kinds of things: dpkg-reconfigure -phigh xserver-xorg, displayconfig-gtk, manually entering info into xorg.conf, and trying a few things I found in "Fix Video Resolution Howto" with no luck.  When I come into the secondary machine (via Vino) with the monitor turned on, I get my desired 1024x768 screen.  But when I come in with the monitor turned off, it's 960x600 and nowhere to go but down.

One interesting note: the xorg.conf keeps re-writing itself to the generic install version, changes don't seem to stick.  This despite sudo.

For all I know I'm doing something wrong.  If so, please tell me so I can fix it.  However, please understand that I really need this machine to be headless for multiple reasons, cannot afford a new vid card (not sure that would make a difference).

If it's a bug that's fixed in 8.04.1 alternate, I'll download and fresh install that.  If the fix is in 8.10, I can wait.  If it's me, feel free to laugh all you want while telling me how to fix it. :)

I've noticed a lot of posts about screen res problems, usually involving nvidia cards (which I can't afford).  These posts make me wonder if it's a bug.

Otherwise, it's back to 7.10.  *sigh*

Thanks.

(I'm waiting to upgrade my main machine until I get the secondary machine running.  Main machine is Microtel 2.6G CPU, 2G RAM, and I don't anticipate as many problems in upgrading.)

---

