---
title: "Using Windows Key with desktop"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by gulagarchipelago on 2008-04-23
I currently am able to use the Windows key on my keyboard to launch the KDE menu.  However, when I use rdesktop to connect to a terminal server, the Windows key does not launch the start menu (on the terminal server).  Is there any way to map the key so that this functionality is available?

---

### Post by SunnyRabbiera on 2008-04-23
I am not sure on this particular issue, but might I ask what setting do you use in KDE for your keyboard layout?

---

### Post by gulagarchipelago on 2008-04-23
Currently I am using English (US) as my layout.

---

### Post by sayakb on 2008-04-23
I use Gnome + the Mint menu. Can't I use the Super key to open the menu?

---

### Post by Swiftfeet8 on 2008-04-23
I have been able to use the Super Key to open the gnome menu.  However, I am not able to open the menu with compiz-fusion running.  This could just be a key-binding issue with compiz, but in gnome you can do the following:

1.  Press Alt+F2 and type gconf-editor and hit enter
2.  Then navigate to "/apps/metacity/global_keybindings/panel_main_menu"
3.  Change the value of this key to Super_L
4.  Close out of gconf-editor and try hitting your windows key
5.  If it doesn't work you might have to restart gdm (sudo /etc/init.d/gdm restart)

If you have compiz running disable it and try to see if the menu will open.  Hopefully this helps.  If it doesn't just post back here and we can try to help you more.

---

### Post by SunnyRabbiera on 2008-04-23
> **gulagarchipelago said:**
> Currently I am using English (US) as my layout.

Nono, I mean your layout in keyboard shortcuts under regional&accessibility

---

