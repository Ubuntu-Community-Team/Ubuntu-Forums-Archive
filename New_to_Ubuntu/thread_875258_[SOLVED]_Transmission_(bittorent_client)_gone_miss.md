---
title: "[SOLVED] Transmission (bittorent client) gone missing"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-07-30
I don't regularly use Transmission. Maybe last time, over a month ago. So when I pulled down Apps/Internet/ . . .  and tried to find Transmission, it has gone missing.

Nobody touches the computer but me. I have seen no error msgs. reported on startup/shutdown about this. Synaptic Pkg. Mgr. shows it as installed (but not transmission-gtk). When I tried to install that, Synaptic wanted to downgrade some packages and I "q" for quit the work. 

What the heck goes on here? Both Gimp and Wine have been updated (technically) UPgraded over the last few days and they can only do partial upgrades.

What am I missing?

---

### Post by barney385 on 2008-07-30
Did you try to open Transmission in the terminal?

---

### Post by tuxxy on 2008-07-30
system > prefs > main menu > internet

Locate the app here and enable it in your main menu.

---

### Post by koji042 on 2008-07-30
If you want the graphical version of transmission, you should install the package "transmission-gtk". That should install the graphical front-end to Transmission. 

Hope that helps. :)

---

### Post by Mark_in_Hollywood on 2008-07-30
Why has my OS UNINSTALLED Transmission? Even if I "re-install" Transmission, what prevents whatever causing it to un-install from doing that again?

According to the terminal, when I invoke: transmission, the term. reports that transmission is not installed and to install it type sudo apt-get install transmission-gtk.

What changes to Ubuntu/kernel/other parts are causing this?

---

### Post by Mark_in_Hollywood on 2008-08-04
Although I never received word as to why Transmission had been deleted from my Hardy H., I have "re-installed" it and it is working.

---

