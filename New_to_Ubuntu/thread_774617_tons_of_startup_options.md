---
title: "tons of startup options"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Zopiac on 2008-04-29
so when i boot up my computer, it asks me if i want to boot up ubuntu, two different recovery modes, and another option that i think is identical to the first. of course, it asks me if i want to load up windows, too, but that i know how to get off ;) how do i get the others off? they annoy me.

---

### Post by H.Callahan on 2008-04-29
Hey!  One I know the answer to!

In a terminal window:
```
sudo gedit /boot/grub/menu.lst
```

Down near the bottom you will see entries for all the options.  Comment out (add a # to the beginning of the line) the ones that you don't want to appear on the grub bootup menu.

(and, as always, back up the file prior to making changes in case either you or I screwed up!)

---

