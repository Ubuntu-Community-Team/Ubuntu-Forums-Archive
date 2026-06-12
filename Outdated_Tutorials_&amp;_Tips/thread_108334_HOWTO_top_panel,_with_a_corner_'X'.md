---
title: "HOWTO: top panel, with a corner 'X'"
date: 2005-12-25
forum: Outdated Tutorials &amp; Tips
---

### Post by benplaut on 2005-12-25
One of my biggest complaints about Gnome-panel is that when you set it to auto-hide, even with the amount showing set to 0, there is still a one pixel border of the panel - this wastes two corners of the screen, plus the entire top, according to Fitt's Law.

Using a program called WMcontrol, you can add the 'X' of each window to your panel.

first, install WMcontrol
```
sudo apt-get install wmctrl
```

Next, make a custom application launcher on your panel.

You have two options now - either the X can close whatever window is active, or it can change the cursor into a crosshairs, and you click the window you want to close.

For the active window, put this into the 'command' section
```
wmctrl -c :ACTIVE:
```

To click on the window you want to close:
```
wmctrl -c :SELECT:
```

Have fun! :)

---

