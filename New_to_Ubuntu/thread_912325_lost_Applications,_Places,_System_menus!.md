---
title: "lost Applications, Places, System menus!"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by thom314 on 2008-09-06
I don't know how but I lost the Applications, Places and System drop-down menus from the main task bar! I know I can get the Applications menu back from the "Add to Panel..." although that one is just the icon without the name displayed which I would prefer. What about the Places and System menus? Help?

Hardy 8.04.1

---

### Post by Scunge on 2008-09-06
There are two menu panel items, one is the "Main Menu" (which gives the orange Ubuntu icon and you get each Applications section as a main heading, followed by "Places" and "System"), and the other is "Menu Bar" (which gives the icon and the three titles alongside).

You are picking the latter from "Add to Panel", yes?

If so, right-click on the icon and there's an "Edit Menus" option. Look in there and click "Revert", see if that fixes it.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by wolfen69 on 2008-09-06
alt-f2, then type in gnome-terminal. then ```
sudo apt-get install gnome-menus
```

---

### Post by thom314 on 2008-09-06
I was picking the "Main Menu" which just gave me the Ubuntu icon. Duh! I should have tried the "Menu Bar" item. I assumed it was for creating your own menus.

So I selected "Menu Bar" and everything came back just fine. Thanks a lot!

---

### Post by Beth1957 on 2008-09-22
THanks to Thom 314 for asking the question (I've just done the same thing!) and to Scunge for the answer; worked for me :D

---

