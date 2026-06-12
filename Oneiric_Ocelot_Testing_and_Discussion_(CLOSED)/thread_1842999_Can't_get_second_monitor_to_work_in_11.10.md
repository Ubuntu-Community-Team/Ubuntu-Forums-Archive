---
title: "Can't get second monitor to work in 11.10"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by bikewrecker on 2011-09-12
I'm using Ubuntu11.10 and I can't get my second monitor to work. I have a GTX 260 video card.

I've tried going into the "Display Settings" in the power menu, but it only shows one monitor named "Unknown" and the "Detect Displays" button does nothing. I've downloaded aRandR and Multiple Screens Apps, but neither of them can see my second monitor either. The only program that can see my second monitor is the NVIDIA X Server Settings

I have tried messing with my "NVIDIA X Server Settings" menu but every time I try to apply my settings I get the error "The current settings cannot be completely applied due to one or more of the following reasons: 
>The location of an X screen has changed. 
>The location type of an X screen has changed.
>the color depth of an X screen has changed
>An X screen has been added or removed.
>Xinerama is being enabled/disabled.

For all the requested settings to take effect, you must save the configuration to the X config file and restart the X server."

I then click the "Apply What Is Possible" button then I click the "Save to X Configuration File" and I get the error 

"Failed to parse existing X config file '/etc/X11/xorg.conf'!" 

I then hit ok and it brings up a menu on where to save the xorg.conf file. If I try to let it save at the same place it doesn't work so i change it to /etc/X11/xorg.conf_backup

At this point i open my terminal and type 
"$ cd ../..
$ cd etc/X11
$ cp xorg.conf_backup xorg.conf
$ sudo reboot "since ubuntu11.10 doesn't have a restart setting in the power menu"
After I restart my computer, my second monitor has changed. Now it is just a white screen and every time I put my mouse over it, my mouse turns into a black "X". I can't do anything with this monitor at all.

---

### Post by cariboo on 2011-09-12
I have two monitors working on a 9400GT, they should both work with either the nouveau drivers or nvidia-current. I selected twinview from the nvidia-settings applet, set the resolution on the second monitor to 1280X1024, and click the apply button. I get a corrupted display on both monitors for a couple of seconds, then it clears up, I then save xorg.conf.

I've had the white screen problem, but completely removing xorg.conf and rebooting solves the problem.

There is a restart function, when you click the shutdown selection in the power button menu.

---

### Post by bikewrecker on 2011-09-13
Ok, I guess my problem was that I had them set as separate screens because I thought that twinview would just show the same thing on both screens.

Thank you so much for your help! I really appreciate it!

---

