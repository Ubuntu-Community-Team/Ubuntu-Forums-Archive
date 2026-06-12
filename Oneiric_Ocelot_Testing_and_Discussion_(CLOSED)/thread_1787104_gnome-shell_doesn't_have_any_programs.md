---
title: "gnome-shell doesn't have any programs"
date: 2011-06-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jontxo on 2011-06-20
Hello

When I start oneiric with gnome-shell all the application menus appear without any application.

Has it happened to anyone else?

Regards.

---

### Post by jbicha on 2011-06-21
Well have you used Gnome Shell before?

If not, flick your mouse up to Activities and start typing the name of a program or click Applications (it's actually a button) to browse installed apps. Alt+F2 also works.

If you instead are complaining about something that doesn't work, you've got to give us a bunch more information about what you're trying to do and how what you get isn't what you expect to get.

---

### Post by jfernyhough on 2011-06-21
I had this problem, and it's an easy fix (though not an obvious one):

$ sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu

Just be aware that this may break things further down the line (though likely only an error when updating that a file needs to be overwritten).

I think (and this is pure supposition) this is down to the fact we're now using LightDM rather than GDM and when we log in the environment isn't being set correctly, so GNOME is looking for applications.menu rather than gnome-applications.menu.

---

### Post by dino99 on 2011-06-21
Hard time coming :(

now Applications is completly empty, even editing menu dont works
gnome-applications.menu empty

dont find a way to enable it back, have copied applications.menu inside gnome-applications.menu for testing, but no luck.

Edit: reuse an older config (thanks backup conf files) so menus are back :)

---

### Post by TechKing89 on 2011-06-21
On my netbook the application appears automatically :)

---

### Post by jontxo on 2011-06-22
Hello

Thanks jfernyhough. with the command 

sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menusudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu

Gnome-shell is working correctly now.

Regards.

---

