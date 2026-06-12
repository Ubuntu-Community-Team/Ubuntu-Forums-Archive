---
title: "[SOLVED] autostart terminal"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by hellomoto on 2008-11-30
hey I set my terminal to autostart on booting up a while back but now I would prefer for it not to load automaticly. 

Only problem is I can't rember what i did to make it autostart.

Its not in the autostart apps GUI, so im stumped! Any ideas?

Im using Xubuntu 8.04

---

### Post by Locutus_of_Borg on 2008-11-30
~/.config/autostart/
remove the *.desktop file that refers to your terminal

---

### Post by hellomoto on 2008-11-30
this is the same as accessing the xfce autostart apps GUI. For some strange reason there is nothing in there that realates to my terminal.

---

### Post by Locutus_of_Borg on 2008-11-30
oh, you probably had restore session set

right click on your desktop, and choose log out, but make sure you unclick save session,

you should start with a new session next you log-in, and only what is in the autostart directory will be started

---

### Post by hellomoto on 2008-12-01
Thank you that fixed the problem.

---

