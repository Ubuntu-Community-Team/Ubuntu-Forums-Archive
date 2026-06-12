---
title: "Trouble logging on"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by sakid on 2008-05-24
[ubuntu 8.04]

Hi all,

Since a reboot last week I cannot log on. After I enter my credentials it goes to the orangish screen like usual before it loads the desktop, but it doesn't get to the desktop. The top left corner turns white and when you put your mouse over it you get the typing cursor and that's as far as it will get.

I know I probably don't make sense but I hope someone can help.

Cheers

---

### Post by bwhite82 on 2008-05-24
Can you boot into safe mode? Either way, you can either drop into a terminal upon boot or boot into safe mode and check the file: .xsession-errors for clues. Some may label this as bad advice, but I've had success in the past by deleting the following from my home directory:
.gconf .gconfd .gnome2 .gnome2_private .metacity .nautilus
Do so at your own discretion.

---

### Post by sakid on 2008-05-24
> **Soldierboy said:**
> Can you boot into safe mode? Either way, you can either drop into a terminal upon boot or boot into safe mode and check the file: .xsession-errors for clues. Some may label this as bad advice, but I've had success in the past by deleting the following from my home directory:
.gconf .gconfd .gnome2 .gnome2_private .metacity .nautilus
Do so at your own discretion.

I couldnt find any clues in .xsession-errors - although I don t really know what I was looking for.

I also deleted those directorys with no luck.


One thing I do remember is this happened after I installed my wifi but after a reboot it was fine.


helllp.. xp is killing me lol

---

### Post by sakid on 2008-05-25
I've decided to just re-install.

Cheers

---

