---
title: "Can I install Ubuntu Desktop over server?"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by ckmiller on 2008-11-25
Okay, so I'm obviously new to Ubuntu, but I'm very interested in getting up and running with it.  I installed server on a PC that I intend to use as a print server.  I think that was a mistake because when it loads now all I get is text and command line requests.  I am not familiar enough with that type of "computing" to engage in that process.  So, two questions...

1.  Is there a user-friendly interface that I can install for my Ubuntu server box?

or

2.  Can I install Ubuntu desktop back on the server box (BTW, I've tried that and it just keeps hanging in the middle of that process - so maybe I'm doing it wrong...).

Thanks to anyone and everyone who can help!

---

### Post by halitech on 2008-11-25
short answer - yes.

long answer, depends on how much daily use it will get. If you just need the gui to set things up there are alternatives to installing a full desktop (ie SWAT, Webmin). If you will be using it for moderate use as well as a server, just install the basics (xfce desktop, abiword, gedit, etc) but if its going to be for daily use, install a full desktop
```
sudo apt-get install ubuntu-desktop
```
from the command line.

---

### Post by taurus on 2008-11-25
If you want Gnome window manager, just install it from a prompt.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by Tatty on 2008-11-25
Yes this is very possible.  All packages in a ubuntu system come from a central repository, and the only real difference between a server system and a desktop system is which packages you have installed.

For a server I would reccomend you install the Xubuntu desktop package, as it is more lightweight than a standard ubuntu install:

```
sudo aptitude install xubuntu-desktop
```

However, if you want the standard ubuntu desktop then:

```
sudo aptitude install ubuntu-desktop
```

---

### Post by ckmiller on 2008-11-25
Thanks to all for the extremely quick responses.  This is all very helpful, and the process itself is pretty exciting.  It's new - and it's not Windows (and I can't afford an Apple).

Thanks again!

---

