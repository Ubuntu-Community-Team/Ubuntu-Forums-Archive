---
title: "In search of a MySQL database module for python"
date: 2008-11-18
forum: Programming Talk
---

### Post by null-cipher on 2008-11-18
I am writing a bit of a hobby application over the holidays with a few friends (to be licensed under the GPL of course! ;)), and I am looking for a simple module to make my python script talk to a remote MySQL server.

It is going to be a parts catalogue for the computer shop I work for. I currently have an abomination running as a web based program across our LAN. It's a real mess, and I would like to get my feet wet with Python.

I've looked into a couple, and they all have me pulling my hair out a bit. I need something simple that I can easily package together with my script, such that it can run on both UNIX platforms and Windows. (Unfortunately our shop has not been completely defenestrated)

Any help would be greatly appreciated. :)
Thanks

---

### Post by Modred on 2008-11-18
```
sudo apt-get install python-mysqldb
```

[http://mysql-python.sourceforge.net/](http://mysql-python.sourceforge.net/)

Alternately, you might want to check out something like [SqlObject](http://www.sqlobject.org/) or [SqlAlchemy](http://www.sqlalchemy.org/), so that you get a high-level db interface that can be ported across db back ends.

---

### Post by pmasiar on 2008-11-18
if you want web app, try Django. It has whole package, including DB, DB mappers, templating, URL mapping etc, and it will automagically generate basic DB read/update screens.

---

