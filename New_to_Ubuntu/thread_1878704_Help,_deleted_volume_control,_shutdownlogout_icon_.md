---
title: "Help, deleted volume control, shutdown/logout icon from top panel"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by cavolt on 2011-11-10
Title pretty much says it. I've tried the "add to panel" option and those controls aren't there to be added. I've also snooped around in system preferences and I haven't found any way to get them back.

I'm running 10.10. Help would be greatly appreciated.

---

### Post by dolphin194 on 2011-11-10
An easy way to get the icons back is to restore your panels to the default settings. To do this, simply run the following 4 commands in Terminal.
```
gconftool-2 --shutdown
gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
That will reset all the panels to the default settings.

---

