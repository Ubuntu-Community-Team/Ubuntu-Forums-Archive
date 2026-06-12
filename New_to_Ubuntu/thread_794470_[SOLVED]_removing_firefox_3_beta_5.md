---
title: "[SOLVED] removing firefox 3 beta 5?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by gameryoshi600 on 2008-05-14
will this be safe. i got opera 9.50 and i am planning to get firefox 2

---

### Post by N.N. on 2008-05-14
Yes, removing firefox 3 is perfectly safe. You have to do it from Synaptic, though, not from "Applications" > "Add/Remove". Open the Synaptic package manager, right click on [FONT="Courier New"]firefox-3.0[/FONT], and mark it for removal. You'll be asked to remove the packages [FONT="Courier New"]firefox[/FONT], [FONT="Courier New"]firefox-3.0-gnome-support[/FONT], and [FONT="Courier New"]firefox-gnome-support[/FONT]. Doing so is safe, cf. [http://www.psychocats.net/ubuntu/firefox2hardy](http://www.psychocats.net/ubuntu/firefox2hardy).

---

### Post by Oldsoldier2003 on 2008-05-14
> **N.N. said:**
> Yes, removing firefox 3 is perfectly safe. You have to do it from Synaptic, though, not from "Applications" > "Add/Remove". Open the Synaptic package manager, right click on [FONT="Courier New"]firefox-3.0[/FONT], and mark it for removal. You'll be asked to remove the packages [FONT="Courier New"]firefox[/FONT], [FONT="Courier New"]firefox-3.0-gnome-support[/FONT], and [FONT="Courier New"]firefox-gnome-support[/FONT]. Doing so is safe, cf. [http://www.psychocats.net/ubuntu/firefox2hardy](http://www.psychocats.net/ubuntu/firefox2hardy).

faster easier easier way:
```
sudo apt-get purge firefox-3.0
sudo apt-get install firefox-2
```

---

### Post by N.N. on 2008-05-14
> **Oldsoldier2003 said:**
> faster easier easier way:
```
sudo apt-get purge firefox-3.0
sudo apt-get install firefox-2
```

You don't say. I'll up the ante: ```
sudo apt-get purge firefox-3.0 && sudo apt-get install firefox-2
``` This is "Absolute Beginner Talk" after all. I don't recommend using the terminal straight away because I don't know whether the OP is comfortable with using it.

---

### Post by Oldsoldier2003 on 2008-05-14
> **N.N. said:**
> You don't say. I'll up the ante: ```
sudo apt-get purge firefox-3.0 && sudo apt-get install firefox-2
``` This is "Absolute Beginner Talk" after all. I don't recommend using the terminal straight away because I don't know whether the OP is comfortable with using it.

:) yeah but i find that having the newcomers use the terminal is a sure fire way to:

1. educate them and make them less afraid of the "scary terminal"
and  more importantly:
2. be sure that they actually get the issue resolved quickly since all they have to do is cut/paste rather than wade through menus and refer back to a post :)

---

### Post by gameryoshi600 on 2008-06-03
I may be a beginner, oldsoldier2003 but I am not afraid of the terminal as it is soooo useful.

---

