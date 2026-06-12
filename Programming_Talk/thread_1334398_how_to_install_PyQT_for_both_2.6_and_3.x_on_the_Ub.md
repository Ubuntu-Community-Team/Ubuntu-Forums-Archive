---
title: "how to install PyQT for both 2.6 and 3.x on the Ubuntu"
date: 2009-11-22
forum: Programming Talk
---

### Post by python.noob on 2009-11-22
Hai friends,

                I don't want to rewrite the story again.. Plz. visit this link and answer my question.. [http://www.daniweb.com/forums/post1054510.html#post1054510.]("http://www.daniweb.com/forums/post1054510.html#post1054510")
This is the right place to ask the question...

---

### Post by Can+~ on 2009-11-22
You can either:

[LIST=1]
[*]Compile the [lastest build]("http://www.riverbankcomputing.co.uk/software/pyqt/download") yourself, for python3.1 support.
[*]Stick with python 2.6 and use [FONT="Courier New"]from future import ...[/FONT] and code like it's python3, if you care for forward-compatibility. And wait for ubuntu to update the repo, then make the switch (painless). There's an [open ticket]("https://bugs.launchpad.net/ubuntu/+source/python-qt4/+bug/400826") about it.
[*]Seek for a .deb precompiled package if you don't want to compile it yourself.
[/LIST]

---

