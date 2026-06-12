---
title: "Games don't show in menu"
date: 2014-08-26
forum: New to Ubuntu
---

### Post by martin119 on 2014-08-26
Hi everybody,
i've recently installed Lubuntu on my netbook and i don't know much about this os.
After the os installation i also installed some games (visualboy, dgen, sudoku) from the software center, the problem is they don't show in the start menu, i have installed some other games that do appear in the menu.
What should i do for those games to appear in the menu.
Thanks so much for the information you can provide.

Ps. English is not my native languaje so i apologize for spelling errors and stuff.

---

### Post by claracc on 2014-08-27
Here, [https://help.ubuntu.com/community/Lubuntu/Windows](https://help.ubuntu.com/community/Lubuntu/Windows) you have examples about how to add programs (games, apps,...) to your start menu.

---

### Post by mcduck on 2014-08-27
Also make sure the games you installed are actually not just command-line based. For example you seem to have a few emulators on the list, and many of them are just command-line apps (unless you install some additional graphical front-end).

---

### Post by vasa1 on 2014-08-27
I installed gnome-sudoku and that shows up in the Lubuntu menu under Games.

Please run ```
dpkg --get-selections | grep sudoku
``` in a terminal and post the output here or tell us how you installed sudoku.

Another browser-based game that shows in the menu under Games is 2048. I got that from [http://sourceforge.net/projects/linuxfreedomfor/files/ubuntu/2048_1_all.deb/download](http://sourceforge.net/projects/linuxfreedomfor/files/ubuntu/2048_1_all.deb/download).

Edit: But I'm using the regular Lubuntu session or Openbox session whereas you're using the "notebook" version. I don't know if that's why we differ.

---

