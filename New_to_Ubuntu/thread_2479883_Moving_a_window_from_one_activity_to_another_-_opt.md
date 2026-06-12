---
title: "Moving a window from one activity to another - option missing now"
date: 2022-10-11
forum: New to Ubuntu
---

### Post by send2gokul on 2022-10-11
Hi,
All was working good, till I got the recent update (which was yesterday). Now all of a sudden I don't see an option to move my window to another "activity".
Did anything change?

Normally I Rt click on the title bar of any window and chose move and then select the activity. Now it's gone.

My ubuntu is current, I use

[FONT=monospace][COLOR=#000000]Distributor ID: Ubuntu[/COLOR]
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy
KDE Plasma Version: 5.24.6
KDE Frameworks Version:5.92.0
Kernel Version: 5.15.0[/FONT]

---

### Post by MAFoElffen on 2022-10-14
IDK. I have GNOME. You Have KDE Plasma. 

Difference in the windows manager may not matter, because windows scheme behaviors are controlled by dconf/gsettings...

Via the path of
```

/org/gnome/desktop/wm/preferences/action-right-click-titlebar

```
But some spplications override that default behavior with their own behaviors. For instance gnome-terminal uses window > right_click > Defual value... But Firefox has it own values.

Are you saying in your now defalut value, that the option for "Move" is missing?

This was a while ago since you posted, has updates between then and now not corrected that?

---

### Post by send2gokul on 2022-10-16
[COLOR=#232629][FONT=-apple-system]I am surprised and also happy. It fixed by itself. Did Ubuntu roll out a patch?[/FONT][/COLOR]

---

