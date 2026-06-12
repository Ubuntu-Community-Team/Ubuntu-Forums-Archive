---
title: "Blank screen where grub should be."
date: 2012-01-07
forum: New to Ubuntu
---

### Post by /z@ch on 2012-01-07
Hello. I'm having some trouble seeing grub on boot. Some background: I've been dual-booting Ubuntu 11.10(upgraded from 11.04) & Win7 on my barebone pc connected to a 32-inch LG TV via VGA. Everything was running smoothly until I decided to do a fresh install of Oneiric. Now when I boot I see the BIOS screen, then the TV displays an "Invalid Format" error, and then I can see the Ubuntu log in screen. This also happens when I am shutting down or restarting my computer, I no longer see a screen where it's asking processes to shut down.

Any help would be appreciated.
Thanks!

---

### Post by 2F4U on 2012-01-07
Does that mean that you can boot into Ubuntu, but not in Windows because you don't see the grub menu?
If you can boot into Ubuntu, then check the file /etc/default/grub whether it contains something like this

GRUB_HIDDEN_TIMEOUT=0

If yes, change the value of zero to something other than zero and execute

sudo update-grub

afterwards to make the change permanent.

---

### Post by /z@ch on 2012-01-07
I tried that, but to no avail. I did some looking around and found a similar problem on AskUbuntu. Someone suggested uncommenting the "GRUB_GFXMODE" line. I did that and it seems to have worked. It's at 640x480. I don't know if that's the optimal resolution but everything seems to fit on screen, so I guess my problem is solved. Thanks for your help!

---

