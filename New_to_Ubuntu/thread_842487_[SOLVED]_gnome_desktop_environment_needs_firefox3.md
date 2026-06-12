---
title: "[SOLVED] gnome desktop environment needs firefox3?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Zopiac on 2008-06-27
i DILSIKE firefox, and want it gone. however, in synaptics, in order to remove firefox 3, gnome desktop envirenment must also be removed. why is this? i just want FIREFOX gone!

---

### Post by anderskitson on 2008-06-27
Which package are you trying to uninstall? the only thing i get for additional required changes is firefox-3.0-gnome-support, which isnt gnome itself. What is going to replace firefox for you?

---

### Post by Zopiac on 2008-06-27
> **anderskitson said:**
> Which package are you trying to uninstall? the only thing i get for additional required changes is firefox-3.0-gnome-support, which isnt gnome itself. What is going to replace firefox for you?

i am trying to uninstall firefox-3.0 (which autoselects others, including gnome desktop environment)

i use Opera, fully. there is nothing firefox has that opera doesnt have, that i like, other than being centered around a fox (fav animal).

---

### Post by Vivaldi Gloria on 2008-06-27
> **Zopiac said:**
> i am trying to uninstall firefox-3.0 (which autoselects others, including gnome desktop environment)

In a terminal write

```
sudo apt-get remove firefox-3.0
```

and press enter. It will also remove the packages

```

firefox
firefox-3.0-gnome-suport
firefox-gnome-suport
ubufox
```

Say yes to these. These are only support files, removing them will NOT remove gnome.

---

### Post by anderskitson on 2008-06-27
You must have another package selected, all I get in synaptic is this when trying to uninstall firefox-3.0
[COLOR="Blue"][http://www.flickr.com/photos/8368367@N08/2615506733/sizes/o/](http://www.flickr.com/photos/8368367@N08/2615506733/sizes/o/)[/COLOR]
Which is exactly same as removing it in terminal

---

### Post by Zopiac on 2008-06-27
> **anderskitson said:**
> You must have another package selected, all I get in synaptic is this when trying to uninstall firefox-3.0
[COLOR="Blue"][http://www.flickr.com/photos/8368367@N08/2615506733/sizes/o/](http://www.flickr.com/photos/8368367@N08/2615506733/sizes/o/)[/COLOR]
Which is exactly same as removing it in terminal

no, when i select uninstall for firefox-3.0, it sahows me all of the other things needed to be uninstalled (in synaptics), where gnome desktop environment is included

the terminal uninstall worked, though. thank you!

---

