---
title: "Need help with screen resolution, please."
date: 2008-10-09
forum: New to Ubuntu
---

### Post by L Campbell on 2008-10-09
I have just installed 8.10 on my PC and am trying to change the screen resolution.

The fonts are way too large right now, so large in fact that the 'Monitor Resolution Screen' is too big for me to be able to access the 'Apply' 
button.

My resolution is at 720 x 480 and I want to get to 856 x 600 (I'd actually like larger numbers than that if possible)

I would appreciate it if you can tell me how to reduce the size of the  'Monitor Resolution Screen' to the point where I can click on 'Apply'.

TIA.

---

### Post by alpage2 on 2008-10-09
I haven't tried this, but how about closing the xorg server, editing the xorg.conf file to remove the unwanted screen resolutions, and restarting xorg?

Post again here if you don't know how to go about that.

Regards
Alan

---

### Post by bcom on 2008-10-09
Try this to reconfigure X.org:


1.  Boot into recovery mode
2.  At the prompt, type dpkg-reconfigure xserver-xorg
3.  Step your way through to the monitor configuration
4.  Try autodetect for the monitor
5.  Enter an identifier for your monitor
6.  Select from the list the resolutions you want to be available.  Highlight each entry you want by pressing the spacebar
7. You can choose "Simple" when asked to enter technical aspects of monitor
8.  Select your color depth and configuration file will be written to disk.

---

### Post by roger_1960 on 2008-10-09
Hi

If you still have problems:

In terminal type

sudo displayconfig-gtk

enter your password, then change the "model" and the resolution in the GUI until you have what you want.  You may have to log out and back in. (This edits xorg.conf without editing it manually)

---

