---
title: "get rid of last gnome-panel"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Zopiac on 2008-11-04
in [another thread]("http://ubuntuforums.org/showthread.php?t=814985") i asked about getting rid of the gnome-panels completely, but in 8.10 a required tab in Sessions is gone, and when i upgraded the panels came back. How do i get rid of all of my panels now?

---

### Post by brandoncolorado on 2008-11-05
Do these help?

[http://sudan.ubuntuforums.com/showthread.php?t=625282](http://sudan.ubuntuforums.com/showthread.php?t=625282)

[http://adventuresinubuntu.blogspot.com/2008/02/getting-rid-of-all-gnome-panals.html](http://adventuresinubuntu.blogspot.com/2008/02/getting-rid-of-all-gnome-panals.html)

---

### Post by Zopiac on 2008-11-05
> **brandoncolorado said:**
> Do these help?

[http://sudan.ubuntuforums.com/showthread.php?t=625282](http://sudan.ubuntuforums.com/showthread.php?t=625282)

[http://adventuresinubuntu.blogspot.com/2008/02/getting-rid-of-all-gnome-panals.html](http://adventuresinubuntu.blogspot.com/2008/02/getting-rid-of-all-gnome-panals.html)

sorry, they do not. or, at least, they do not do nearly as well as the 8.04 fix did....

---

### Post by Zopiac on 2009-02-15
w00! figured it out in 8.10 :D

gconf-editor
desktop>gnome>session>required_components>panel

just delete the gnome-panel command withing required_components and you're good to go :)

Gnome-Do is just soo much better than gnome-panel for me :D

---

