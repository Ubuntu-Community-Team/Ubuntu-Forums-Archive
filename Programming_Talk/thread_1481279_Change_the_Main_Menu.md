---
title: "Change the Main Menu"
date: 2010-05-12
forum: Programming Talk
---

### Post by damian.garrido on 2010-05-12
hello
I would like to consult on how to change the look of ubuntu
I'm doing a custom version of this and I like to modify the  main menu.
I thought that changing attributes  Alacarte way I work, but it was not.
I  feel that the Live CD version written somewhere on the changes made by  me.
for the time and I managed to identify  where to make cosmetic changes, but I can not find where it makes the  main menu also has these changes.

very  grateful for any response.
:)

---

### Post by roccivic on 2010-05-12
global: /etc/xdg/menus/applications.menu

in 8.04 it was ~/.config/menus/application.menu for individual users, but there doesn't seem to be one on my 10.04 machine, maybe it got moved or maybe I just didn't make any changes to the menu...
also look here: ~/.local/share/applications

---

