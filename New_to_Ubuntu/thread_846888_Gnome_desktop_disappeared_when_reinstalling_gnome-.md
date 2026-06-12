---
title: "Gnome desktop disappeared when reinstalling gnome-menus"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by caliva on 2008-07-01
This all started when I uninstalled Evolution via Synaptic. Then I went to look at the menus to see if the application was totally removed from the Gnome menu. I noticed that the "menu editor" was no longer visible on the menu.

I reinstalled gnome-menus 2.22.2 and then rebooted betting that this would restore it. When I rebooted, now all of the Gnome desktop is gone - menu bars etc..

how do I reload the desktop? 
and
how do I add the 'menu editor' back on the menu?

Hardy 8.0.4

---

### Post by wolfen69 on 2008-07-02
assuming you can get to a terminal and are online, i would do
```
sudo apt-get clean
```
```
sudo apt-get autoremove
```
then ```
sudo apt-get install ubuntu-desktop
```
it's probably worth a shot.

---

