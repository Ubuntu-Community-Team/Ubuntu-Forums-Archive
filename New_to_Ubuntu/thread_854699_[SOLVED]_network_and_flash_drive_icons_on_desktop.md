---
title: "[SOLVED] network and flash drive icons on desktop"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Zopiac on 2008-07-09
my desktop is CLEAN. i has no gnomebars, icons, NOTHING. however, when i go to a network folder, or plug in a flash drive, etc., an icon for that appears on my desktop! i want it to be completely clean! how do i make it so that this doesnt happen???

---

### Post by tjwoosta on 2008-07-10
i also enjoy a clean desktop  :)


first press alt-f2 (its important to use this here rather than a terminal)

in the box type gconf-editor

then when it pops up navigate to apps-nautilus-desktop

uncheck the boxes on the right

your done

---

### Post by Zopiac on 2008-07-12
thanks a ton! i did use terminal tho ;) alt+f2 doesnt work for me, as i dont have a gnomebar; required for this command :\ i just said in gnome-do 'gksudo gconf-editor' (tab) 'run in terminal', entered password, and edited it :P works for me

---

### Post by tjwoosta on 2008-07-12
yea sorry i forgot you said you dont have a gnome panel

using the gnome-do command works jsut as good as alt-f2 though :)

---

