---
title: "[SOLVED] Screen is to dark when running on battery"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Friccy on 2008-08-06
Hi!

I have installed the Hardy on a new HP laptop and when I am running it on battery, the screen has not enough brightness. After several minutes of working it can be very painful for my eyes.
I have tried to adjust it from the Power Management (like in Windows), but there is no way to do it from there.
How can I adjust the brightness?
Thanks!

---

### Post by ViRMiN on 2008-08-06
On the top panel, right click and select "Add to Panel...", then look for "Brightness Applet".  You can then adjust your brightness and be able too see the screen comfortably.

---

### Post by Friccy on 2008-08-06
Thanks!
It helps right now, but is there any other way to set this brigtness for a final value? I mean, this time at every startup I have to adjust manualy.

---

### Post by ViRMiN on 2008-08-06
Not sure... my girlfriend says she doesn't have to change the setting when she boots up her laptop?  Maybe I did something when I was playing about on it one day!  She's on 8.04......

---

### Post by sayakb on 2008-08-06
Press Alt+F2
Type in **gconf-editor **and press Enter
Navigate to /apps/gnome-power-manager/backlight and change the **brightness_battery **value and the **idle_brightness** value.

---

### Post by ViRMiN on 2008-08-06
Ummm... I don't remember doing that but, if it works!  Plenty of ways to skin the cat!

---

### Post by Friccy on 2008-08-07
> **LinuxIsInnovation said:**
> Press Alt+F2
Type in **gconf-editor **and press Enter
Navigate to /apps/gnome-power-manager/backlight and change the **brightness_battery **value and the **idle_brightness** value.

I have tried this but still can't see any difference.
If I am not using the Brightness applet it's still dimmed.

---

### Post by phidia on 2008-08-07
In the power management applet there should be a tab for "on battery". 
There are sliders in there that control screen brightness but look at them carefully the slider for screen brightness on battery works opposite of how you might think.

---

### Post by Friccy on 2008-08-07
> **phidia said:**
> In the power management applet there should be a tab for "on battery". 
There are sliders in there that control screen brightness but look at them carefully the slider for screen brightness on battery works opposite of how you might think.

Hello!
On my laptop, with the Hardy on it, at the System>Preferences>Power Management the sliders are for the time to put display to sleep and Put computer to sleep. No other slider.

---

### Post by MrPatton84 on 2008-08-07
I'm also having the same problem. I've tried the ways that have been suggested, and changed the settings, but the display is still dark when the laptop is running on battery alone. 

I would say it's something to do with the laptop, but Friccy's running on HP, I'm on a Samsung. 

Any more suggestions? Thanks in advance.

---

### Post by phidia on 2008-08-07
There are a few related posts in the forums. Try [this;]("http://ubuntuforums.org/showthread.php?t=881241&highlight=screen+brightness") and [this]("http://ubuntuforums.org/showthread.php?t=881194&highlight=screen+brightness") to see if your motherboard is supported for that feature. Also see if your owner manual provides a keystroke way (the function keys for instance) of adjusting brightness of the screen.

---

