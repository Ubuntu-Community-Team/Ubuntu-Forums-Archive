---
title: "Changed refresh rate on HP Envy 360x, now display settings are all over the place"
date: 2019-07-17
forum: New to Ubuntu
---

### Post by jcameron45 on 2019-07-17
I just recently installed ubuntu mate onto my HP Envy 360x, and everything was working fine until I started testing out display settings

I went to change the refresh rate, and it caused my display to go black. I waited to see if it would revert back, but nothing happened. Restarting will bring me to the login screen just fine, but once I log in it goes right back to a black screen. Admittedly, the brightness was probably on zero, but I ended up trying to connect an external monitor to troubleshoot. Now when my external monitor is connected, I can see my laptop screen just fine like it was originally, and the display is extended/mirrored to my monitor. I reverted the display settings of my laptop display, but now when I unplug the HDMI cable, it goes back to an all black screen, and turning up the brightness doesnt fix it, it only brightens the backlight.

I apologize in advance if I forgot to include any crucial details, but feel free to let me know what info I can provide to help.

Thanks!

---

### Post by mastablasta on 2019-07-17
could it be that external monitor is considered as primary one and display is simply moved there? this happens to me with some games in fullscreen (battle for wesnoth, World of padman...). the monitor would simply go black and display is moved to external monitor (TV) weather that one is plugged in or not and regardless of the fact that it is a secondary display.

---

### Post by CatKiller on 2019-07-17
The monitor settings for when you're logged in are stored in ~/.config/monitors.xml. Deleting that - which you can do from the command line at one of the TTYs - should get you back on track.

The reason plugging in another monitor worked is that Gnome can't handle having monitors of different refresh rates, so your broken one got changed to the default of the other one.

---

### Post by jcameron45 on 2019-07-17
Just tried deleting the monitors.xml and now I&#8217;m back to normal. Thank you so much!

---

