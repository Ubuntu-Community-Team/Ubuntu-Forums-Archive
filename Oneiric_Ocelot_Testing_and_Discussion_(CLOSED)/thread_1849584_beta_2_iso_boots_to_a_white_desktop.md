---
title: "beta 2 iso boots to a white desktop"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by haresear on 2011-09-24
Downloaded the ubuntu-11.10-beta2-desktop-i386.iso today, and it appears to boot okay, but when the desktop comes up, it is entirely white. The top panel and its components are visible, and an empty grey bar is visible on the left side. Everywhere else is pure white. The left side bar has no icons displayed, but the Unity components are apparently there -- mousing over the bar pops up the text labels. If I click on the spot where the Dash icon should be, the Dash panel comes up and displays fine over the white desktop. If I open any application, the window can't be seen on the white desktop. Checked the Xorg log file, but didn't see anything that looked significant. I tried to restart lxdm and gdm from tty1 screen, but they were not recognized. Logout from the top panel power button doesn't work. How do I restart X? Any other things I could try?

I am running an nVidia FX5200 video card. I've been using Ubuntu with this card at least as far back as Ubuntu 7, and I've never seen this before -- in fact I've never had any graphics problems that I can remember (but I may have forgotten).

Update:
I managed to restart lightdm, but the white desktop came back.

During boot I see several instances of the following error message:

Command line "debus-launch --autolaunch=......" exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.

This looks like a problem. No clue what to do about it. Any ideas?

---

### Post by cariboo on 2011-09-24
Have you tried starting with nomodeset enabled, by pressing F6 at the initial splash screen?

---

### Post by haresear on 2011-09-25
Thanks for the suggestion. I finally managed to get to the login screen, where I was able to select Unity 2D, and get a functional desktop (nomodeset works also to get directly into Unity 2D).

I tried to install the Nvidia drivers using jockey, but that failed. From looking at the jockey.log file, it appears that it couldn't auto-detect my card, and tried to install the version 96 drivers. (I know my card uses the version 173 drivers.) I guess I would have to install the Nvidia drivers manually if I want 3D capability. I had the same experience with Bodhi 1.2 recently (which is also running a kernel 3.0.x). I was hoping that the Ubuntu 11.10 version of jockey would work with my card, but I guess not. I was able to manually build and install the Nvidia 173 drivers on Bodhi, but I'm not sure I really want to go that route long term.

Thanks for your help.

---

