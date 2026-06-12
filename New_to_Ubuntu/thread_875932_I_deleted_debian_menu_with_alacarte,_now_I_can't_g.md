---
title: "I deleted debian menu with alacarte, now I can't get it back"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-07-31
I deleted the debian menu using alacarte. 

I have tried ```
 sudo apt-get remove menu --purge
``` and then reinstalling. 

I don't know what else to try.

Anyone have any ideas? Thanks in advance!

---

### Post by tuxxy on 2008-07-31
Can you not redo the menu from scratch in alacarte

---

### Post by drs305 on 2008-07-31
If you run "alacarte" do you have a '*Revert*' button. That might restore the menu if available.

---

### Post by Anzan on 2008-07-31
sudo apt-get menu menu-xdg

update menu

---

### Post by pluckypigeon on 2008-07-31
Sorry, I should of mentioned...

> **drs305 said:**
> If you run "alacarte" do you have a '*Revert*' button. That might restore the menu if available.

I can't revert because I did this on a different Ubuntu which I broke and also ....

> **Anzan said:**
> sudo apt-get menu menu-xdg

update menu

I have tried reinstalling menu and menu-xdg and then update-menus

---

