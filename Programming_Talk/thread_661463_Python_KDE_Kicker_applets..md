---
title: "Python KDE Kicker applets."
date: 2008-01-07
forum: Programming Talk
---

### Post by solarwind on 2008-01-07
Hey all, I was wondering if anyone could point me in the right direction or help me out  in making KDE Kicker applets in Python. I'm good at Python, but just don't know where to begin to write Kicker applets for KDE.

---

### Post by OpenFish on 2008-01-09
i too like python though im not convinced it is the right tool for the job but what the hell good look any way 

i am a gnome person so i cant really help too much but as no one else has posted i think u need a KDE version of this tutorial may be???

[http://linuxfocus.org/English/July2000/article160.shtml](http://linuxfocus.org/English/July2000/article160.shtml)

i know its not what u are looking for but it might be usefull (at least be thought provoking) and u prob wont get it with a search with kde in it

i dont know any thing about kde and only ever use it with knoppix and dsl so sorry

good luck!

---

### Post by solarwind on 2008-01-09
Thanks for the reply. I know Gnome has good support for creating applets in Python but I have no idea where to start for KDE.

By the way, that article is 8 years old.

---

### Post by solarwind on 2008-01-13
Hmm, I have some really nice Python scripts that I would like to run as Kicker applets.

However, anyone have any tutorials (Any programming language) on making Kicker applets?

---

### Post by solarwind on 2008-01-16
Bump...

---

### Post by solarwind on 2008-01-19
Bump.

---

### Post by nick_h on 2008-01-19
Here is a simple C++ example - [Extending the KDE Panel](http://developer.kde.org/documentation/tutorials/dot/panel-applets.html).

---

### Post by solarwind on 2008-01-19
> **nick_h said:**
> Here is a simple C++ example - [Extending the KDE Panel](http://developer.kde.org/documentation/tutorials/dot/panel-applets.html).

Oh well I guess I could execute python scripts using C++. Thanks.

---

### Post by solarwind on 2008-02-14
Anyone know of a way to write kicker applets in python?

---

### Post by sin on 2008-08-31
Install pykde and look here [http://www.riverbankcomputing.co.uk/static/Docs/PyKDE4/toc.html]("http://www.riverbankcomputing.co.uk/static/Docs/PyKDE4/toc.html")

Googling always beats thread necromancy.

---

### Post by snova on 2008-08-31
Two things.

[LIST=1]
[*]You want PyKDE. This is the glue that makes it possible to write KDE applications in Python, rather than its native language (C++).
[*]Kicker is going the way of the dinosaur. By the time you learn to make applets for the panel, it will have been fully replaced by Plasma.
[/LIST]
Plasma is the future! Don't get stuck in the past.

Unfortunately, I'm not sure if PyKDE yet supports KDE 4. You'll have to check. If not, read the C++ documentation and try to learn the API. When Python support is finished, check up on any differences, and you'll be all set.

---

