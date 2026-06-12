---
title: "changing the panels look"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-07-01
I know you can goto properties and change the image, but how do I use things like Vpanels that come zipped up and often have a bunch of files?

also, a lot of people have the gnome foot thing instead of the ubuntu circle thing, how is that done?

[http://gnome-look.org/content/show.php/vPanels?content=74722](http://gnome-look.org/content/show.php/vPanels?content=74722)

---

### Post by WinterMadness on 2008-07-01
sorry for the bump.
It just got on page four before anyone could even respond. so instead of making a new post, i figured this would be better.

---

### Post by sayakb on 2008-07-01
If you have a foot icon (eg. foot.png), rename it to start-here.png
Now press Alt+F2 and type:
```
gksudo nautilus
```CAREFUL WITH THIS: because it opens nautilus as root giving you write access to everything.
Anyway, copy this start-here.png to /usr/share/your_icontheme_name/22x22/places
Also copy it to other sizes such as 24x24 and scalable.

For the panel backgrounds, just drag and drop the image on the panel to set it as background.

---

