---
title: "Where is &quot;Screens and Graphics&quot; in Hardy"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by littletinman on 2008-05-17
My resolution is correct, but my graphics arent correct. For somereason my Nvidia card isn't in the Drivers Manager thing and i can't get it to show up. It worked fine about a month ago in hardy Beta. Anybody help?

---

### Post by shifty_powers on 2008-05-17
tried using envy?

---

### Post by philinux on 2008-05-17
It's in the menu's but not selected. It's in sys>prefs>main menu apps others.

---

### Post by littletinman on 2008-05-17
Philinux,

  Thanks man, ok now i should be able to try it. how do i install envy. I tryed installing Nvidia Settings Manager but it says my x config file isn't using Nvidia. I have a Nvidia 7000m and it works great in my two other partitions both running hardy. the dif is they are Kubuntu and this one is ubuntu. 

  Let me try the Screens and graphics.

---

### Post by littletinman on 2008-05-17
so will envy fix my problem?

---

### Post by shifty_powers on 2008-05-17
```
sudo apt-get install envyng-gtk
```

in a terminal iirc.

Envy is a program that will detect which video hardware you have and install the correct drivers for it ;)

edit: oops, forgot the sudo ;)

---

