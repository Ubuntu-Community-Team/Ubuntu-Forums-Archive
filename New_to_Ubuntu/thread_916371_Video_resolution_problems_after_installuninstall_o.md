---
title: "Video resolution problems after install/uninstall of Wine/WoW"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by keyset on 2008-09-10
I'm having video trouble which I am afraid will require a reinstall, but I would rather try to fix it to learn a little more.

I (stupidly) tried to install World of Warcraft Trial under Wine. This of course did not work, so I blew Wine away. Now my lower taskbar is distorted (looks like pixellated static about 5 times the height of the normal taskbar) and the resolution looks wacked out. Top it off, Wireless networking is broken. When I disable the ATI driver, wireless comes back to life and video looks normal, but obviously I want 3d acceleration.

Stats: 64 bit Ubuntu, AMD Phenom 9850
ATI Sapphire HD3870 video card, ViewSonic 22" monitor at 1680x1050px and 60hz (this is when I have the 3d acceleration disabled)
8gb DDR2 RAM

I ran "sudo dpkg-reconfigure -phigh xserver-xorg" to rebuild xorg.conf and reinstalled the drivers, but this didn't help. I'm guessing it's another config file somewhere that's jacked up, but where do I start looking? :confused:

---

### Post by keyset on 2008-09-14
Anybody have any ideas?

---

### Post by keyset on 2008-09-14
OK wireless seems to be back up now with the 3D drivers enabled, but I've still got a large static bar at the bottom of the screen, and I can't see the lower taskbar. If I turn on the screensaver, it takes up the whole screen and looks good, and when I come back to the Desktop, the bar is black instead of static. I can see the mouse over this mysterious bar too. What IS visible on the desktop appears squished, as though this bar is pushing everything up, indicating a resolution problem. Res is set to 1600x1200, but every time I try to change this to ANYTHING else, it just comes back to this same resolution. :confused:

---

### Post by nonzer0 on 2008-09-14
I'm in the same boat.  I installed virtualbox, and now my screen resolution is stuck at 640x480.  If i uninstall the video card driver, the screen resolution returns to normal, but all effects are disabled.  Makes no sense.  
There seems to be a lot of people having issues with the resolution on their PCs and laptops, and i haven't been able to find an answer.  If any one knows a way to solve this we would both be quite appreciative.

---

### Post by keyset on 2008-09-15
hey nonzer0,

I dug thru some more old posts and managed to fix my resolution issues using this command from a terminal:

```
sudo displayconfig-gtk
```

This seemed to actually save unlike System > Preferences > Screen Resolution, but my wireless is still flaky. Seems like sometimes when I boot it up it will either not connect at all, or connect at brutally slow speeds. Any insight would be appreciated.

---

### Post by nonzer0 on 2008-09-16
I had tried that.  I figured out what the problem was after going through an 8 page thread someone started.  It turns out my monitor cable was just a little loose.  
lol.  What a nightmare.  I suppose it could have been worse.

---

