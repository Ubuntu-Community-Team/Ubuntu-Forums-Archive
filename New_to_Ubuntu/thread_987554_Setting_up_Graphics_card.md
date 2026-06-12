---
title: "Setting up Graphics card"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Stickyfeatures on 2008-11-19
Hi - total noob so please be gentle

Just installed 8.10 

All set up ok but not very many screen resolution options so tried to install a new driver for my graphics card (ATI Radeon 7500 - R200). 

I downloaded the ATI catalyst drivers and installed those hoping they would work but they don't cover my card. I'm pretty sure I have uninstalled them using Synaptic but on start-up I get the same message every time:

"Ubuntu is running in low graphics mode"

Can someone please tell me how to set my card up properly and get rid of this annoying message. As a Windowz user I have only just discovered Terminal which is obviously very powerful but also not at all intuitive unless you know what you are doing.

Thanks!

---

### Post by shifty_powers on 2008-11-19
have you checked your restricted drivers manager?

system>administration>hardware drivers

---

### Post by Stickyfeatures on 2008-11-19
I have looked in there but it's totally empty

---

### Post by Stickyfeatures on 2008-11-19
It says "No proprietary drivers are in use on this system"

Any idea how i get some and which ones I should use. 

Please note that I have googles and I'm not just being lazy, but I simply don't understand the only results I've got

My card is mentioned here, [http://gatos.sourceforge.net/]("http://gatos.sourceforge.net/") but I really don't know what to do with the stuff that's on offer of if it is current, or how to install it if it is correct.:confused:

---

### Post by w4ett on 2008-11-19
Unfortunately AMD/ATI does not support their legacy cards in Linux.....The Radeon 9500 and above can use the FGLRX driver, but the RV 280/Radeon 9200 and below have to use the xorg-driver-ati (formerly the radeon driver) due to incompatibilities with the current X.

Using Synaptic or apt-get, remove and purge all attempted installs of the restricted driver and revert to the open source driver.

Hope this helps.

---

### Post by Stickyfeatures on 2008-11-19
Thanks for the reply.

I think I've got rid of the Catalyst drivers, but how do I know if my machine is using the correct open source driver? Is there some way to check or manually select the correct one?

---

### Post by w4ett on 2008-11-20
Ubuntu will normally select the correct driver for your chipset, but will revert to the failsafe vesa driver in extreme circumstances. The terminal command:

```
glxinfo
```

will give us the information that we are looking for.  Copy and paste the results of that command and let's see what driver and direct rendering you have.

---

### Post by atpat on 2008-11-20
You might find [http://http://ubuntuforums.org/showthread.php?t=814518&highlight=radeon+7500]("http://http://ubuntuforums.org/showthread.php?t=814518&highlight=radeon+7500") useful.  Worked for me...

---

