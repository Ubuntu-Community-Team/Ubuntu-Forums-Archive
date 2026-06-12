---
title: "Blank Screen - newbi"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Quarkrad on 2008-10-03
Apologies for this question - complete novice to linux/Ubuntu.  I have this problem- and it is the same on two different hard drives.   Downloaded Ubuntu from web and made boot CD.   Can install Ubuntu from CD (at the moment installing on complete HD (having trouble with file system trying to install on specific partition manually).  My problem is having installed every other time I boot the screen goes blank after the initial screen tat shows Ubuntu and the horizontal load window.  what happens is that the monitor goes blank and instead of continuing to boot into the 'pinkish' screen that eventually goes to the desktop I just get a blank screen.  no matter of key pressing does anything.  Strange - it seems to happen every other boot.    
I get the same thing if I put the Ubuntu boot CD and restart the pc - first time it will go blank and freeze after the initial horizontal (orange blocks) load.  I have to restart the pc ad than it will boot to the Desktop.  I wondered if it could be my old graphics card (ATI Radeon 8500DV) - I tried installing the linux driver but this appears to be 'quiet a challenge' for a newbi.  Any ideas on what I could try would be welcome.

---

### Post by DArtagnon on 2008-10-03
I'm not an expert by any means, but I had the same problem with my Radeon 9800. It also affected my ability to watch videos.  I couldn't get it fixed with gutsy, but hardy has been helpful.

To fix it, when the computer is booting up it will say "loading GRUB, press esc" or something similar.  If you press escape it will give you a list of boot alternatives; choose "recovery mode".

You'll get to a screen that has a few options.. "Resume normal" "drop to root" "fix Xserver" etc.  Choose the one that says Fix X, then resume normal.

That has worked for me so that every time I boot I can get to the desktop and watch videos in totem and Mplayer.

---

