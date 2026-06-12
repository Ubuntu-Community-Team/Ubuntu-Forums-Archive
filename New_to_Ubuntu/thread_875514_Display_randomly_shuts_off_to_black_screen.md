---
title: "Display randomly shuts off to black screen"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Josephxfs on 2008-07-30
First time poster here.
Using Xubuntu 32-bit
when starting my system which is running a Wubi dual boot with Windows XP 32-bit,  I randomly get a blank screen with absolutely no display.  I've tried to get to the virtual terminal and still nothing happens.  I've found that this happens particularly when my computer takes a long time to boot(Ubuntu is currently located in the slowest part of my partition).  I've tried updating my xorg config with sudo dpkg-reconfigure -phigh xserver-xorg but no go.  I recently installed Compiz but then took it off because it seemed a little to slow on my PC. Afterwards I tried simply ctrl+Alt+backspace.  Still wouldn't respond. 
Systems specs:
HP 532w*upgraded ram over the years
Intel 845gl integrated graphics.
TriGem 129504 MOBO
Memtested 512MB PQI ddr1 mem with 64MB allocated to the onboard graphics
Wubi install of Xubuntu 32bit 8.04 hardy(sorry)
Windows XP 32bit
Grub boot manager(from Wubi).

Second question:
I know it is possible to run 2 Xservers with the start x -- :1 command.  However when I try it, one will almost always end up failing similarly to the above problem except I always am able to get back to my original Xserver(TTY7) and continue from there.  I would think that these two problems are probably linked, but you never know.

Third question:
Is there A way to start Ubuntu without the Xserver without going into safe mode or root?  I would like to set up A pure command line where I'm able to start x later on.  I've become sorta fond of the CLI Programs that allow me to browse the web, listen to music, and even view pictures.

---

### Post by Josephxfs on 2008-07-30
Sorry I forgot to mention I've also installed some KDE apps and have installed Gnome-core.  For the option of a gnome session.

---

