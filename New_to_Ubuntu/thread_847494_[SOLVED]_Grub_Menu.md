---
title: "[SOLVED] Grub Menu"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by anderskitson on 2008-07-02
How would you change the background or make the grub menu more graphical. This isn't a necessitie for me, but I would like to learn how to do it.

---

### Post by drs305 on 2008-07-02
> **anderskitson said:**
> How would you change the background or make the grub menu more graphical. This isn't a necessitie for me, but I would like to learn how to do it.

For simple changes, you can use StartUp-Manager to set colors, background images, menu display times, kernel numbers to view, etc.

To install it:
```
sudo aptitude install startupmanager
```

To run it:
gksudo startupmanager
or:
System, Administration, StartUp-Manager

The display options are in the Appearance tab.

To learn more about SUM, here is a link although I didn't discuss the visuals of the grub options in that tutorial:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Shazaam on 2008-07-02
The simplest is to edit menu.lst and uncomment this section..
```
# Pretty colours
#color cyan/blue white/blue
```
You can also install Startup-Manager from the repos.

---

### Post by bumanie on 2008-07-02
You can do a great many things as above, but also look [here]("http://users.bigpond.net.au/hermanzone/p15.htm") It tells you how to make a new splash image.

---

### Post by anderskitson on 2008-07-02
Thanks guys all looks great for what I wanted

---

