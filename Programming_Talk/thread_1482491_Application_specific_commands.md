---
title: "Application specific commands"
date: 2010-05-13
forum: Programming Talk
---

### Post by Concrete Pants on 2010-05-13
Hi there! I've been wondering how you would run, from the command line, applications function. For example a line to make a music player go to the next track. Is there a way to find out what commands different programs have?

I wanted to make use of the scripts section in compiz.

---

### Post by dv3500ea on 2010-05-13
```
man nameofapplication
```
You would generally have to go into programming using the same libraries the application uses to get some of that program's functionality. There is also something called [D-Bus]("http://www.freedesktop.org/wiki/Software/dbus"). That is used in the new MeMenu to get the functionality of Gwibber.

---

### Post by Concrete Pants on 2010-05-13
Brilliant! Exactly what I was looking for, I learnt  about the man pages long ago but then forgot... Thanks for that

---

