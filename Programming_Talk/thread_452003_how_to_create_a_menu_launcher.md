---
title: "how to create a menu launcher?"
date: 2007-05-22
forum: Programming Talk
---

### Post by squinx22 on 2007-05-22
Hi! I am currently developing a software, but it seems I have trouble in making a my application present in the menu items. What sould I do in the terminal to do this one? thanx...

---

### Post by seamless on 2007-05-23
Menu entires are read from .desktop files in /usr/share/applications/.

Here is an example for the game Enemy-Territory (et.desktop):
```
[Desktop Entry]
Encoding=UTF-8
Name=enemy-territory
Comment=
Exec=/opt/games/enemy-territory/et
Icon=/opt/games/enemy-territory/ET.xpm
Terminal=0
Type=Application
Categories=Application;Games;X-Red-Hat-Base;
```

Simply make a .desktop file, put it in /usr/share/applications, and it will show in the menu. Be sure to get the categories line right for your application so it shows in the correct submenu.

---

