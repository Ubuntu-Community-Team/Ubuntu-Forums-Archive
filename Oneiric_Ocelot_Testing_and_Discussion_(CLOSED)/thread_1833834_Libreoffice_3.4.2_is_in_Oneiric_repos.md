---
title: "Libreoffice 3.4.2 is in Oneiric repos"
date: 2011-08-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-08-26
The new release version of LibreOffice (3.4.2 final) is now in Oneiric repos.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/libreoffice/1:3.4.2-2ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/libreoffice/1:3.4.2-2ubuntu2)

However, the issue with launcher icons still exist.
After installation, if you want to see launcher icons, you need to set the actual link to icons to these files in /usr/share/application:
- libreoffice-x.desktop
   (where x is the name of the application, like writer)
The link should point to /usr/share/icons/hicolor/48x48/apps/

The release notes are here:
[http://www.libreoffice.org/download/release-notes/#LO342](http://www.libreoffice.org/download/release-notes/#LO342)

---

### Post by jbicha on 2011-08-26
Simply logging out and logging back in usually fixes icon hiccups.

---

### Post by Harry33 on 2011-08-26
> **jbicha said:**
> Simply logging out and logging back in usually fixes icon hiccups.

No not this time.
The libreoffice-x.desktop files simply do not work. Not even after a reboot nor a complete halt.

---

### Post by coffeecat on 2011-08-26
> **Harry33 said:**
> No not this time.
The libreoffice-x.desktop files simply do not work. Not even after a reboot nor a complete halt.

The LO launcher icons work here. I've just updated my system and updated LibreOffice to 3.4.2. The icons neither disappeared nor became non-functional. They still work just fine after a reboot.

System installed from the 22nd August daily live and fully up-to-date as of a few minutes ago.

---

### Post by Harry33 on 2011-08-27
> **coffeecat said:**
> The LO launcher icons work here. I've just updated my system and updated LibreOffice to 3.4.2. The icons neither disappeared nor became non-functional. They still work just fine after a reboot.

System installed from the 22nd August daily live and fully up-to-date as of a few minutes ago.

Icons do not work in my three different setups.
Each one of them has Gnome-shell and Gnome-panel as a fallback; no Unity here.
As I wrote, I get the icons back by adding the direct link into the *.desktop file.
So actually no problem with that.

---

### Post by Harry33 on 2011-08-27
Some more info here:

I have only the new gnome-menu system installed:
- gnome-menus (3.1.5)
- libgnome-menu-3-0

And only one icon theme:
- gnome-icon-theme (+ -full and -symbolic)

---

### Post by Sennaista on 2011-08-27
Over here the menus are usually corrupted when opened and items only appear when you move the mouse over them.

---

