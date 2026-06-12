---
title: "Issues after updating xubuntu 11.10"
date: 2011-07-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Jerry5627 on 2011-07-13
Hi, I installed updates this morning which required a restart. Now I can't:

1. See the maximize & minimize buttons on the panels in file windows or in programs.
2. Alter the number of desktops in the setting ap (I had 2, now only 1).
3. Move windows around my desktop - they are stick in the top left hand corner.

Any help much appreciated, thanks.:D

---

### Post by Elfy on 2011-07-13
Thread moved to Ubuntu +1 (Oneiric Ocelot).

---

### Post by rojaasensei on 2011-07-13
I also lost the maximize/minimize buttons with all windows frozen in the top left corner after an update.

The only solution I found was to do a complete re-install of Xubuntu.  That was 2 days ago.  Yours is the first mention I found on the net for this problem.

---

### Post by Toz on 2011-07-13
Sounds like the window manager (xfwm4) has crashed. 

To see if its running, from a terminal:
```
ps -ef | grep xfwm4 | grep -v grep
```

If not, Alt-F2 and enter:
```
xfwm4 --display=:0.0 --replace
```

should get you going again.

---

### Post by Jerry5627 on 2011-07-14
> **Toz said:**
> Sounds like the window manager (xfwm4) has crashed. 

To see if its running, from a terminal:
```
ps -ef | grep xfwm4 | grep -v grep
```If not, Alt-F2 and enter:
```
xfwm4 --display=:0.0 --replace
```should get you going again.

Supa dupa mate, worked a treat, thanks so much.

---

### Post by Jerry5627 on 2011-07-14
> **rojaasensei said:**
> I also lost the maximize/minimize buttons with all windows frozen in the top left corner after an update.

The only solution I found was to do a complete re-install of Xubuntu.  That was 2 days ago.  Yours is the first mention I found on the net for this problem.

Thanks for your reply, take a look at the code, it worked for me - in case you get it again...

---

### Post by rojaasensei on 2011-07-14
Thank you very much.  Help like you have offered is always welcome, and appreciated.

---

