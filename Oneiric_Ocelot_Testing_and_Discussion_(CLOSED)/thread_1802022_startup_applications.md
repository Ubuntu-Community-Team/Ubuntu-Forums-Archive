---
title: "startup applications"
date: 2011-07-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-07-11
has it been moved or renamed in anyway or are we still just waiting for it to be added yet,

---

### Post by arpanaut on 2011-07-11
[http://ubuntuforums.org/showthread.php?t=1795650](http://ubuntuforums.org/showthread.php?t=1795650)

The times they are a changing.... B. Dylan

---

### Post by CaptainMark on 2011-07-11
so i have this script which used to be triggered in startup applications```
#!/bin/bash

for script in $(ls /home/mark/Documents/bash/login_scripts/*)
do
bash $script &
done
```to run all my custom scripts when i login. where should i put this now, ill try make a desktop launcher and place it in /etc/xdg/autostart

---

### Post by seeker5528 on 2011-07-11
> **CaptainMark said:**
> ill try make a desktop launcher and place it in /etc/xdg/autostart

You shouldn't put anything in '/etc/xdg/autostart/' unless you want it to be used in every login account on the system.

Stuff you want to autostart only for your login should go in '~/.config/autostart/', if you use 'gnome-session-properties' AKA 'Startup Applications', and use the add button it will create a .destkop file in '~/.config/autostart/' for you.

Later, Seeker

---

### Post by CaptainMark on 2011-07-12
i would do that but i dont have startup applications, its not here since doing installing 11.10 i type startup into the dash and only get startup disk creator. hence i was wondering if it had been removed altogether

---

### Post by Quackers on 2011-07-12
Type gnome-session-properties in the terminal and hit enter and see what happens :-)

---

### Post by mc4man on 2011-07-12
It was hidden for a bit, the recent update to gnome-session should have returned it to menus and dash (gnome-session-common (3.1.3-0ubuntu2)

---

### Post by CaptainMark on 2011-07-12
I'll check when I'm home, ill also have a look at the held back packages, apt-get has about 24l5 its keeping from me rather than the 21 most others seem to have.

---

### Post by CaptainMark on 2011-07-12
it didnt seem to be in the list of held back packages but i ran an update anyway and put gnome-seesion-properties in a terminal and hey presto now its in the dash too, weird, maybe i didnt have the current version

---

