---
title: "Installing icons with Quickly"
date: 2010-06-07
forum: Programming Talk
---

### Post by luopio on 2010-06-07
Hi,

I've created a small application using Quickly ([https://edge.launchpad.net/~luopio/+archive/ppa](https://edge.launchpad.net/~luopio/+archive/ppa)) and everything has gone smoothly so far. The issue right now is that I need to install an icon file into /usr/share/icons/hicolor/<size> and can't seem to get it working. This icon is used by the indicator.

I've tried two ways:
[LIST=1]
[*]a quick function in setup.py that calls "xdg-icon-resource install". Didn't work.
[*]read the docstrings on DistUtilsExtra.auto and that suggested putting them into data/icons/<size>/<category>/<file>.png. I had data/icons/48x48/hicolor/icon.png (i guess category should be "theme"). Didn't work either.
[/LIST]

What would be the recommended way?

---

### Post by kvarley on 2011-08-02
Easiest way would be to use python to set the icon for the icon that appears on your window list at the bottom of the screen and then just set the icon for the application in the Applications menu by editing your .desktop file.

---

