---
title: "Ibex - Login Process Hangs after Installation"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by kevdog on 2008-11-04
Just installed Ibex on my old junk Acer TravelMate 220 Laptop which previously ran Gutsy w/o problems.  I installed using the alternate CD -- I did verify MD5Sum prior to burning the disc, and did verify the disc after burning.

With installation from CD -- the LVM encryption option didn't work -- got an error about not being able to boot kernel.

Reinstalled with alternate CD, standard install with one partition/swp.  

Now when booting into Ibex, I type in login name and password, and then all I get is a cursor -- that I can move -- but nothing other than that.  I tried changing the session type from script, GNOME, FailSafe Gnome -- but results are all the same -- a blank screen with the brown background and cursor I can move.

I'd guess its probably the xorg.conf file -- anybody have any insights on how I can troubleshoot this -- super annoying for a supposedly improved distribution.

On booting into terminal -- which works -- in the /etc/X11/xorg.conf filee -- its blank -- there is nothing in it!!! Could this be correct??

---

### Post by kevdog on 2008-11-05
I'll share the solution -- was running Integrated Intel Video Chipset 830

Here is the problem as documented:
Hangs with desktop effects on Intel 830MG and 845G video cards
There is a bug in the Intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and will freeze the system. For new installations, please install using the safe graphics mode (press F4 in the startup screen) on these systems and disable desktop effects via System -> Preferences -> Appearance, clicking on “Visual effects” and choosing “None”.

I removed in safe-mode 
sudo apt-get remove compiz
sudo apt-get remove compiz-core
sudo shutdown -r now


Then everything was successful.  No compiz graphics however -- Doesn't really bother me since I'm not really all into eye candy anyway.

---

