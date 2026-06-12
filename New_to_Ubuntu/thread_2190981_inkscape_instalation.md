---
title: "inkscape instalation"
date: 2013-11-30
forum: New to Ubuntu
---

### Post by broonsparrow on 2013-11-30
Hiya,
I'm running Lubuntu 13.04. I've just added inkscape but it's not appearing in the main menu --> graphics (nor under any other menu)

How do I run Inkscape, and how do I add it to the main menu

TIA

BS

---

### Post by ajgreeny on 2013-11-30
Open /usr/share/applications/inkscape.desktop using leafpad or whatever text editor Lubuntu uses now to see if there is a line saying:-
 **OnlyShowIn=GNOME;Unity; **
or similar, but not mentioning LXDE.

If needed you can edit the desktop file with **gksudo leafpad /usr/share/applications/inkscape.desktop** and add a # to the start of that line to comment it out and inkscape should then show in your menu at the next login to Lubuntu.

---

### Post by BenjaminCHILOE IS. on 2013-12-01
hi broosparrow,

I would try installing Inkscape from the terminal:  press CTRL +ALT+T and wait for your terminal come up;  then type this sudo apt-get install inkscape and press ENTER key;  next you will read in the terminal requesting your password, so you type it and then press ENTER;  and wait to see if the terminal says...anything like Inkscape latest version is already installed or  we cannot achieve this operation  cause  your system lacks  some dependencies.... .
If  terminal says Inkscape is already installed... type  Inkscape, add your password and wait to see if this app comes up...

---

### Post by walterorlin on 2013-12-01
You could also try going into pcmanfm the file manager and click on applications and see if it is in the menu there. Editing the .desktop file in post #2 will allow you to put it into the menu.

---

### Post by vasa1 on 2013-12-01
I think the first step would be to try **inkscape** from the terminal. If it runs, then fixing the .desktop file as ajgreeny suggested is the way to go. I've seen that happen with some packages from the Software: their default .desktop files assume the user is using one particular environment :(

---

