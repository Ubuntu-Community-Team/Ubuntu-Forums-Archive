---
title: "[SOLVED] desktop icon for home"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by iluminati63 on 2008-07-03
How do I put an icon for home on the desktop
say to /home/user/ ????

---

### Post by aethralis on 2008-07-03
In nautilus, with mouse right click folder -> make link and drag this link to desktop.

Or in terminal: 
ln -s ~ ~/Desktop/home
to get your home dir on desktop

---

### Post by pferpaddy on 2008-07-03
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) and theres an option in it to enable certan desktop icons like home and trash

---

### Post by tjwoosta on 2008-07-03
or 
press alt-f2
type gconf-editor
navigate to Apps-Nautilus-Desktop
check the box that says show home folder on desktop

or
right click desktop
click create launcher
use this as the command
```
nautilus /
```

---

### Post by sayakb on 2008-07-03
> **tjwoosta said:**
> or 
press alt-f2
type gconf-editor
navigate to Apps-Nautilus-Desktop
check the box that says show home folder on desktop

or
right click desktop
click create launcher
use this as the command
```
nautilus /
```

Err.. that would be 
```
nautilus /home/username
```

---

### Post by tjwoosta on 2008-07-04
> Err.. that would be
Code:

nautilus /home/username



lol

duurrr... my bad

forgive me, it was a late night

---

