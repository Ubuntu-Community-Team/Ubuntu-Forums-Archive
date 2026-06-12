---
title: "editing menu bars"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by misfit815 on 2011-10-31
Running 11.10. Ran "apt-get install gnome-session-fallback" because the new interface is horrid. Now I am hung up on one last thing I can't change.

The menu/task/app/whatever bars on the top and bottom of the screen... On my older version of Ubuntu, I used to be able to edit them, and now I can't figure out how to do so.

Specifically, what I do is cram all the useful stuff in the top bar and get rid of the bottom bar (I like my screen real estate).

Any help is appreciated.

---

### Post by philinux on 2011-10-31
> **misfit815 said:**
> Running 11.10. Ran "apt-get install gnome-session-fallback" because the new interface is horrid. Now I am hung up on one last thing I can't change.

The menu/task/app/whatever bars on the top and bottom of the screen... On my older version of Ubuntu, I used to be able to edit them, and now I can't figure out how to do so.

Specifically, what I do is cram all the useful stuff in the top bar and get rid of the bottom bar (I like my screen real estate).

Any help is appreciated.

IIRC you have to alt right-click.

---

### Post by ajgreeny on 2011-10-31
Have a look at this which I have copied from another forum thread and use to answer questions like this one.  The info is from bob-linux-user who collated it all from various sources;  incredibly useful!

> The instructions below let you use a panel, get rid of the diabolical overlay scrollbars and put the window controls back at top right.This is what I did:

Install ubuntu 11.10 in normal way
In a terminal type
```
sudo apt-get install synaptic
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0
sudo apt-get install gnome-session-fallback
sudo apt-get install gconf-editor
sudo apt-get install gnome-tweak-tool
```
log out and log back in gnome classic
In a terminal type
gksudo gconf-editor
Browse to apps/metacity/general. Double click on button_layout and gconf-editor and set value to
:minimize,maximize,spacer,close
Alt right click on panel at top
-Set orientation to bottom and size to 36, or position it where you want it.
Alt right click on time and move to extreme right
Alt right click on panel and add
-Main Menu
-Window List
Alt right click on "Applications Places" menu and remove
Alt right click on the "speech bubble" at bottom right and remove.  You can add or remove applets as you wish.
Remove the slim top panel by alt right clicking and deleting
Alt right click on panel and add
-Show desktop icon
On a general area of desktop right click and change the background to what you want ( I chose Jardin Polar)
in a terminal type
```
sudo apt-get install ubuntustudio-theme ubuntustudio-icon-theme human-theme
sudo gnome-tweak-tool
```
Set Theme:Icon theme to Ubuntu Studio
Set GTK+ theme to Raleigh
Set window theme to human
You may prefer other themes, but remember older gtk2 themes are not possible, as far as I'm aware.

---

