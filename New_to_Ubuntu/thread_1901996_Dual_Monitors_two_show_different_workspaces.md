---
title: "Dual Monitors two show different workspaces?"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by shevin on 2011-12-29
I just got an extra monitor , now I have a laptop and a monitor,
now I have dual monitor on my ubuntu , I wonder if I could make each of them to show a diffrent work space?

for example could I make the second monitor to show the second workspace all the time?

---

### Post by audiomick on 2011-12-29
Nope, doesn't work that way. I don't think that is possible at all, at least not to ordinary mortals.

---

### Post by pierreyy on 2011-12-29
hey... good idea btw, if this works with you i wouldnt mind setting one up like it for me


if found this 

>   [http://ubuntuforums.org/showthread.php?t=826717](http://ubuntuforums.org/showthread.php?t=826717)  

let me know if its any help.

---

### Post by shevin on 2012-01-03
hm...any other ideas?

---

### Post by I_can_see_the_light on 2012-01-03
> **pierreyy said:**
> if found this 

> [http://ubuntuforums.org/showthread.php?t=826717](http://ubuntuforums.org/showthread.php?t=826717)

let me know if its any help.

It doesn't seem like that would do what the OP wanted, and I'm not sure it could be done the way (s)he want it to work either. 

Having a second monitor beside your laptop in "[extended mode]("https://en.wikipedia.org/wiki/Multi-monitor#Span_or_extended_desktop_mode")" is not that difficult, at least not with the open source ATI drivers or the Intel drivers. I usually do it by running *xrandr*.

This is a script I use to start extended desktop with my TV:

```
#!/bin/sh
xrandr --output S-video --mode 800x600 --right-of LVDS --output LVDS --auto &
```

To stop extended desktop:

```
#!/bin/sh
sleep 1 && xrandr --output S-video --off &
```
There may well be a simpler solution for you, so I suggest you simply connect the monitor to your laptop and start the program that handles your display settings (forgot the name, it's in the control panel).

---

