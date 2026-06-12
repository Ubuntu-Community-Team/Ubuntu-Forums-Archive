---
title: "My Ubuntu 8.04 opens to an all white screen"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Norman Thom on 2008-07-06
I need some help please:

When I boot my computer with Ubuntu 8.04 it starts normally, goes to log in screen but then opens into a simple white screen.  My mouse pointer is there but nothing else.  It will even go into my screensaver normally but no access to my desktop.  Can anyone help me with this

Norm

---

### Post by Troll_the_Great on 2008-07-06
You could try a few things.First hit Alt+F2 and type ```
gnome-terminal
```
This will open the terminal.There type ```
startx
```
If that doesn't work you could try to reinstall the display manager
```
sudo apt-get remove gdm
```
and
```
sudo apt-get install gdm
```
In the worst case try
```
sudo aptitude install ubuntu-desktop
```
Tell me if it worked.
Cheers!

---

### Post by RequinB4 on 2008-07-06
Some more things to try, in order:

Boot in recovery mode (press the down button at the GRUB menu)

If you get a terminal on the whitescreen, run

```

nautilus

```

---

### Post by Nikitas350 on 2008-07-06
Try to recover xorg.conf. Boot in recovery mode and then select to fix xorg

---

