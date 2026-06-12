---
title: "How to package?"
date: 2012-05-27
forum: Packaging and Compiling Programs
---

### Post by rgreener25 on 2012-05-27
I have got a file directory like so:
0x03db-0.0.1:
    __init__.py
    game.py
    ai.py
    config.py
    0x03db.desktop
    0x03db-icon.png
And i want to make a binary deb(.deb) and the source debs(.orig.tar.gz, .debian.tar.gz and .dsc) i want it to have all the .py files in this directory /opt/extras.ubuntu.com/0x03db
the 0x03db.desktop file in /usr/share/applications and 0x03db-icon.png in /usr/share/pixmaps

I can edit the debian/controls file and debian/copyright but i am lost everywhere else and i just cant do it if anyone can help me i will be beyond grateful

---

### Post by rgreener25 on 2012-05-27
Oh and its python2 btw

---

### Post by agillator on 2012-05-27
The best bet if you really want to create a deb file is [http://www.debian.org/doc/manuals/maint-guide/](http://www.debian.org/doc/manuals/maint-guide/). From there you probably need to talk more to debian developers than users.

---

### Post by Cheesemill on 2012-05-27
[http://developer.ubuntu.com/packaging/html/](http://developer.ubuntu.com/packaging/html/)

---

### Post by oldos2er on 2012-05-27
Moved to Packaging and Compiling Programs.

---

### Post by rgreener25 on 2012-05-28
-.- i still dont get it

---

