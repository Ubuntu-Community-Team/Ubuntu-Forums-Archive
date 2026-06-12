---
title: "BusyBox problem"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by 4400th on 2008-10-18
Just installed ubuntu and in a few hours I got 2 problems :lolflag:

So anyway, when loading the system, instead of loading the graphical interface, i get this command line interface, saying

```
BusyBox v1.1.3 (Debian 1:1.1.3-5 ubuntu12) Built-in shell (ash)

Enter 'help' for a list of built-in commands

(initramfs) {it was waiting here for a command}
``` 

any ideas on how to get rid of this? :confused:

---

### Post by damis648 on 2008-10-18
At the Grub (boot) menu, highlight the Ubuntu option and press "e". Then highlight the second line and press "e" again. Using backspace, remove the words "quiet" and "splash" from the end of that line and then press enter. Finally, press "b". When you see the BusyBox again, look for errors right before it. Post any that you find.

---

### Post by khoailang on 2009-02-25
> **damis648 said:**
> At the Grub (boot) menu, highlight the Ubuntu option and press "e". Then highlight the second line and press "e" again. Using backspace, remove the words "quiet" and "splash" from the end of that line and then press enter. Finally, press "b". When you see the BusyBox again, look for errors right before it. Post any that you find.

I see:  Target filesystem doesn't have /sbin/init
Please help me. Thanks

---

### Post by geirha on 2009-02-25
Right after you installed it, did it boot properly? or did it give you busybox shell right from the start?

---

### Post by khoailang on 2009-02-25
> **geirha said:**
> Right after you installed it, did it boot properly? or did it give you busybox shell right from the start?

It give me BusyBox shell right from the start

---

### Post by geirha on 2009-02-25
It seems the install hasn't been complete then. Could you boot with the CD and choose the option "Check CD for defects" (or something like that) from its boot menu to see if it might be a bad burn.

---

