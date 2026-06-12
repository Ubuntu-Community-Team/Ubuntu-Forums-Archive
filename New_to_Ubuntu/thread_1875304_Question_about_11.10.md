---
title: "Question about 11.10"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by L Campbell on 2011-11-04
I just upgraded from 11.04 to 11.10 with a disk.

So far I have not found how to set up a weather station at the bottom of the screen, as I did in 11.04 and I haven't found the icon in the bottom left corner for clearing the desktop.

TIA

---

### Post by Frogs Hair on 2011-11-04
Use the command and logout / in and search for weather indicator in dash . The indicator will appear on the top panel . You would have describe your weather setup in 11.04 because I don't know what you used to set up weather on the bottom of the screen .   ```
sudo apt-get install indicator weather
```

---

### Post by peter d on 2011-11-04
Press Super+D to show desktop. Press again to restore your windows.

---

### Post by L Campbell on 2011-11-04
> **Frogs Hair said:**
> Use the command and logout / in and search for weather indicator in dash . The indicator will appear on the top panel . You would have describe your weather setup in 11.04 because I don't know what you used to set up weather on the bottom of the screen .   ```
sudo apt-get install indicator weather
```

Thanks for your help here. This is how I set it up with 11.04:-

Right click in the bottom panel and select Add to panel.

Type 'weather' in the open box.

This will bring up 'Weather Report', clicking  ADD will add this to the bottom panel.

Right clicking on the new icon will give options like Details, Updates, Preferences, which will allow you to choose the weather news for YOUR location.

Hope this helps you.

---

### Post by Frogs Hair on 2011-11-04
11.10 doesn't have a bottom panel unless you have the Gnome fallback session installed , which looks more like Gnome 2 . If you have fallback installed it is possible to restore some of the panel functionality of Gnome 2 .  Fallback :[http://ubuntuforums.org/showthread.php?t=1859960](http://ubuntuforums.org/showthread.php?t=1859960)

[http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html#more](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html#more)

---

