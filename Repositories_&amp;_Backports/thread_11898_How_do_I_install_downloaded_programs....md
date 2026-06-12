---
title: "How do I install downloaded programs..."
date: 2005-01-20
forum: Repositories &amp; Backports
---

### Post by ngch on 2005-01-20
I am a newbie to Linux, so I know very little.  I downloaded the game [Project: Starfighter](http://www.parallelrealities.co.uk/starfighter.php) as an rmp package. But I do not know how to install it. Can someone help me?

---

### Post by Ste on 2005-01-20
[QUOTE=ngch]I am a newbie to Linux, so I know very little.  I downloaded the game [Project: Starfighter](http://www.parallelrealities.co.uk/starfighter.php) as an rmp package. But I do not know how to install it. Can someone help me?[/QUOTE]
 Rpm is Redhats package manager.
Get the .deb instead. then from the terminal
```
sudo dpkg -i starfighter-1.1-1.deb.deb
```

---

### Post by az on 2005-01-20
If there is no deb available, use alien to convert an rpm into a deb.  Be aware that this may screw up your system as packages are rarely compati ble.

install alien.

sudo alien -i whatever.rpm

---

### Post by ngch on 2005-01-20
Thanks for the help guys.  :)

---

