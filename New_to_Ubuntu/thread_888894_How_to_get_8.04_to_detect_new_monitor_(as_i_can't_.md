---
title: "How to get 8.04 to detect new monitor (as i can't get higher rez than 1280x1024)"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Doctoxic on 2008-08-13
Am running Ubuntu 8.04 and have just bought  a shiny new LG L227WT 22" LCD.

Its working but not recognised as i con only get max resolution of my old hardware (1280x1024). I've looked on all the menus and did a bit of googling but didn't find anything obvious.

Also can i (and if so how) install the drivers from the Windows driver disk

many thanks

doc

---

### Post by overdrank on 2008-08-13
> **Doctoxic said:**
> Am running Ubuntu 8.04 and have just bought  a shiny new LG L227WT 22" LCD.

Its working but not recognised as i con only get max resolution of my old hardware (1280x1024). I've looked on all the menus and did a bit of googling but didn't find anything obvious.

Also can i (and if so how) install the drivers from the Windows driver disk

many thanks

doc

Hi and you may use the alt, F2 keys and enter this command ```
gksu displayconfig-gtk
``` there you maybe able to adjust your resolution and detect your new monitor

---

### Post by Doctoxic on 2008-08-13
thanks Overdrank - thats sorted it

seems crazy you can't get to this through a 'menu' option though

doc

---

### Post by overdrank on 2008-08-13
> **Doctoxic said:**
> thanks Overdrank - thats sorted it

seems crazy you can't get to this through a 'menu' option though

doc

Hi and you can, right click on your applications, and select edit menus. Under other is screens and graphics. Check the box then it will be listed under applications, others.

---

### Post by Doctoxic on 2008-08-13
thx again

but its still crazy it isn't there by default  :D

doc

---

