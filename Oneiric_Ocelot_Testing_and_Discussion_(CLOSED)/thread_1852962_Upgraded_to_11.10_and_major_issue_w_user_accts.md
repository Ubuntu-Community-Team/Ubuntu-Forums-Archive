---
title: "Upgraded to 11.10 and major issue w/ user accts"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by llarios on 2011-10-01
Newbie here...I upgraded to 11.10, all was running OK but then, last night I added a few things from the repositories including ccsm. I changed some settings to unity but when I added wobbly windows, ccsm just crashed (I got other messages too) then machine froze. After that, my user acct is useless. Every time I log in, i have/see nothing but the desktop background --No dash, no indicators, nothing will open or work...just the background looking at you-- However, other user accts are working fine and I CAN run my acct in unity 2D just fine.I tried some newbie approaches b/c i have no idea what is going on (i.e I uninstalled ccsm) but nothing is working. I thought I could create a new user and delete my original account (saving Home of course) and problem solved, but the new user I created inherited the same issue...Now what?

---

### Post by howefield on 2011-10-01
Thread moved to the development forum "*Ubuntu +1 (Oneiric Ocelot)*"

---

### Post by cariboo on 2011-10-01
I'd suggest you log into Unity, press Ctrl-Alt-t, to open a terminal then type:

```
ccsm
```

to start conpizconfig-settings-manager, and make sure the Unity plugin is enabled.

---

