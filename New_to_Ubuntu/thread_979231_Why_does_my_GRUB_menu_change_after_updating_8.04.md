---
title: "Why does my GRUB menu change after updating 8.04?"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by andrewwg94 on 2008-11-11
I just did a clean hardy install, and it asked me to update as usual, and after it was finished, my GRUB menu looked like this:

Ubutu 8.04.1, Linux Kernel blah blah blah
Ubutu 8.04.1, Linux Kernel blah blah blah (recovery mode)
Ubutu 8.04.1, Linux Kernel blah blah blah
Ubutu 8.04.1, Linux Kernel blah blah blah
Ubutu 8.04.1, Linux Kernel blah blah blah (recovery mode)
Other Operating Systems:
Microsoft Windows XP Homme Edition

---

### Post by tuxxy on 2008-11-11
Its the different kernals, each one will be different kernal but launch Ubuntu.

---

### Post by andrewwg94 on 2008-11-11
> **tuxxy said:**
> Its the different kernals, each one will be different kernal but launch Ubuntu.

why do i need an old linux kernel?

---

### Post by Miljet on 2008-11-11
It's a good idea to keep at least two of the latest kernels just in case the newer one causes problems. You can always drop back to the older one. You can remove all the others, but the space they occupy is very minimal and usually not worth the trouble unless you are really, really strapped for disk space.
That said, you don't have to look at all those kernels each time you boot. Just edit the /boot/grub/menu.lst file. Find the line that says "# howmany=all." Change the "all" to the number of kernels that you want to display.
Have fun.

---

### Post by zvacet on 2008-11-11
Go to the synaptic and in search box type **linux-image**.You will find all your kernels.Leave two with higher number and remove others.

---

### Post by SunnyRabbiera on 2008-11-11
> **andrewwg94 said:**
> why do i need an old linux kernel?

Well its there just in case you have hardware issues.
But dont worry just because more then one kernel is listed doesnt mean your system is cluttered :D

---

