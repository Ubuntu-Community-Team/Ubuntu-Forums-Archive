---
title: "Out of frequence"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by poscomp on 2008-08-14
I just loaded new drivers for my Nvidia GeForce 6200 video card. When I reboot my monitor says OUT OF FREQUENCE then I get a blank black screen. How do I fix this?

---

### Post by dca on 2008-08-14
You can try booting in to recovery mode and type at CLI:
 
*sudo dpkg-reconfigure xserver-xorg*
 
select the 'nv' driver instead of 'nvidia' and see if that at least gets you a GUI desktop where you can back-track and see what went wrong.
 
I'm sure someone else might have a better option for diagnosing/repairing nVidia w/o using what I suggest.

---

### Post by tahina on 2008-08-14
Can you get to tty1 by pressing ctrl-alt-F1 ? 

Then you could login in textmode and have a look at /etc/X11/xorg.conf (you might need to look into howto use the nano or vim editor first). Maybe it says in xorg.conf to use some frequency that doesn't fit you screen... 

Or you could change what driver to use (on some line in the xorg.conf change "nvidia" to "nv" which is the open source driver) so you can get into your system to uninstall or reinstall or choose a different driver (if there are more than one proprietary nvidia-driver available(?)).

If you can't login to textmode or learn nano or vi, you could perhaps use a live-CD to boot your computer and get into your hard drive to change some line about frequency or what driver is set in the xorg.conf.

edit: While I was typing, dca had a much simpler route :)  I'll be sure to remember that the next time my graphics are acting up.

---

### Post by mrtomservo on 2008-08-14
When I was running the nVidia drivers I would get resolution/out of freq problems every 3 or 4 versions.  Eventually I just came to the conclusion that i'd only update the proprietary drivers when I had a problem with the existing ones.  You might want to try keeping a record of which versions work and which ones don't, then with a bit of luck, you should be able to fall back on what worked before.  As Poscomp and Tahina stated, your first task is probably to reconfigure the xserver and at least get it up and running with the nv drivers.  From there i'd probably uninstall the nVidia drivers and install a lower version, working your way back until they work again.  All this providing you didn't change anything else other than your nVidia drivers. :)

---

