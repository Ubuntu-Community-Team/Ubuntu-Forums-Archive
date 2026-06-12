---
title: "gedit tabs: I want to increase the contrast"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by vasa1 on 2011-10-29
Ubuntu 11.10 Unity 3-D mode, Ambiance theme for desktop and for GTK (set in GNOME tweaks = *Advanced Settings*).

I would like to know how to increase the contrast between the active tab and the inactive tab(s) when I have more than one file open in gedit (Text Editor).

In other words, I want the background color of the active tab to be easily seen to be different from inactive tabs.

There is a slight difference existing (by default) but I'd like to increase it.

I've looked at gtk.css, settings.ini, and gtk-widgets.css but I can't tell which is the selector that has to be tweaked (and how).

I don't want to try another theme as the solution because  I've otherwise got most of what I need with tweaking Ambiance.

---

### Post by vasa1 on 2011-10-30
Despite appearances, it's nice to know I'm not alone!

[http://askubuntu.com/questions/46182/gnome-terminal-tabs-are-very-dark-difficult-to-tell-which-tab-is-in-use](http://askubuntu.com/questions/46182/gnome-terminal-tabs-are-very-dark-difficult-to-tell-which-tab-is-in-use)

[http://askubuntu.com/questions/40332/how-to-make-selected-tab-in-terminal-more-prominent](http://askubuntu.com/questions/40332/how-to-make-selected-tab-in-terminal-more-prominent)

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/771701](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/771701)

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/771641](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/771641)

---

### Post by vasa1 on 2011-10-30
In the gtk-widgets.css file ...
Replace
```

    background-image: -gtk-gradient (linear, left top, left bottom,
                                     from (shade (@bg_color, 0.97)),
                                     color-stop (0.80, shade (@bg_color, 0.95)),
                                     to (shade (@bg_color, 0.92)));

```
with
```
    background-color: #222222
``` or any other suitable color
or
just modify the values in the gradient

Note: that the section which has been modified deals with ".notebook tab". I'm doing all this on a laptop. I'm not sure what ".notebook" means but there was no harm in trying. Plus, it worked. No idea about desktops or other devices.

---

### Post by vasa1 on 2011-10-30
This tweak also works for tabs in GNOME Terminal.

---

