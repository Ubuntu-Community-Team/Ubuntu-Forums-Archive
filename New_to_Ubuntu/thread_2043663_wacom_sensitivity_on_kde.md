---
title: "wacom sensitivity on kde"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2012-08-17
uninstalled unity and gnome and installed kde.
Pen works fine, but on mypaint in gnome/unity i could change colors with the side buttons.
On kde, the pen has to be touching in order for the side button to be used.
I figured it was a lack of sensitivity, but I can not find a menu in kde to adjust wacom sensitivity.

---

### Post by Favux on 2012-08-17
Hi LunaticHiatus,

It doesn't sound like a sensitivity issue, it sounds like the TabletPCButton parameter is on.  That means hover mode is not available and the pen acts like a tablet PC pen.  The driver should default to TabletPC off for a graphics tablet.

Enter **xinput list** into a terminal and post the output.  Then identify the stylus device name or ID number.  Then try this command:
```
xsetwacom set "device name" TabletPCButton off
```
And see if it works correctly then.

The KDE settings app. uses a KDE daemon.  Maybe that's the problem and it is set wrong.  I think the app. may be broken in Kubuntu Precise and you have to compile it.  Anyway it is at:  [http://kde-apps.org/content/show.php/wacom+tablet?content=114856](http://kde-apps.org/content/show.php/wacom+tablet?content=114856)  Probably in the software center.

---

