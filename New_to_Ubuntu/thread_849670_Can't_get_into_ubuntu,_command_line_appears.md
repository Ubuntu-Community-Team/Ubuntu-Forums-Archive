---
title: "Can't get into ubuntu, command line appears"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by esotericguy on 2008-07-04
I've got ubuntu via wubi set up and suddenly it won't let me in. It loads up and everything but when it gets to the point where the login screen is supposed to be a command line/terminal shows up. How can i get bring up the Login screen?

---

### Post by sayakb on 2008-07-04
Into the terminal, type:
```
startx
```
And see if it comes up.

---

### Post by TheTrlak on 2008-07-04
you could also try and use ctrl + alt + f7 but thats usually only used to get back into x when you left it for the comand line.

---

### Post by ayenack on 2008-07-04
Try this instead.

**sudo /etc/init.d/gdm start**

If that doesn't work try this.

[B]xinit

gdm start[/B]

---

### Post by WinterMadness on 2008-07-04
i had the same problem and when i tried to reboot it i didnt even have to enter startx.

it was just a one time thing for some reason

---

### Post by solid71 on 2008-07-11
I had the same problem. But i have found that if you let your computer boot into windows then have windows shut itself down you will then be able to boot into ubuntu..

---

