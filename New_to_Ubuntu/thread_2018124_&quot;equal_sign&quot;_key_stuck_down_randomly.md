---
title: "&quot;equal sign&quot; key stuck down randomly"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2012-07-06
i just installed xubuntu on an Asus EEEPC 1005HAB and the equals/plus key on the keyboard randomly gets stuck down, even when i'm not touching it.

i googled how to disable an individual key in linux, and found [this guide]("http://www.linuxscrew.com/2008/09/15/faq-how-to-disableremap-a-keyboard-key-in-linux/") and disabled keycode 21 by running in a terminal:
```
xmodmap -e 'keycode 21='
```

however, the problem still persists! i cant use the key anymore (even holding it down), but i'll still get lots of equals signs inserted when i'm typing.

if this isnt the keyboard randomly sending keypresses, what is going on with my system? it was doing the same thing in windows XP so this has to be some kind of hardware problem

---

### Post by critin on 2012-07-06
Perhaps it needs cleaning?  A tiny drop of soda pop spill?

Is yours a UK keyboard?

---

### Post by Sonic Reducer on 2012-07-06
> **critin said:**
> Perhaps it needs cleaning?  A tiny drop of soda pop spill?

Is yours a UK keyboard?

as far as i can tell its the US version. $ on 4 and all that.

and wouldnt a stuck key be solved by *xmodmap*?

.:EDIT:. holy jesus the xmodmap doesnt apply when apply in the screensaver lock. i gave up and rebooted after 15 minutes trying to get my password input

---

### Post by SonnyE on 2012-07-06
The best solution is to repair or replace the key or the whole keyboard. I repaired my HP Pavilion laptop to get the Ctrl keys working, by removing the keyboard and trimming a fraction of a millimeter from the end of the ribbon cable. Before that I was using SharpKeys in Windows XP to make one of the Alt keys a Ctrl, and trying to learn every way to substitute keys in Linux.

[Changing keyboards on the asus eeepc 1005ha]("http://www.ubikann.com/2009/10/03/changing-keyboards-on-the-asus-eeepc-1005ha/")

[www.replacementlaptopkeys.com ASUS 1005HAB Laptop Keys]("http://www.replacementlaptopkeys.com/servlet/the-17009/ASUS-1005HAB-Laptop-Keys/Detail")

If you want to learn to disable the key in software so that whenever Linux boots it has a keyboard profile to ignore the key, as if your keyboard never had it (and you have to assign some other way to type "=" or "+") then start with these instructions:

[wiki.archlinux.org Map scancodes to keycodes]("https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes")

Nice looking computer. My little brother has an Eee and runs #! (CrunchBang) Linux on it. Wishing you luck with it.

---

### Post by Sonic Reducer on 2012-07-14
i just noticed that i only have this problem when the netbook is plugged into the power adapter. has anyone ever heard of that?

---

### Post by QIII on 2012-07-14
Is the power cord socket in close proximity to the key?

---

