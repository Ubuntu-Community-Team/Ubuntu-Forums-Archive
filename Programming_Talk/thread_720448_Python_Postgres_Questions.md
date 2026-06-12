---
title: "Python Postgres Questions"
date: 2008-03-10
forum: Programming Talk
---

### Post by themusicwave on 2008-03-10
Hey everyone,

So here I am at work working(ironic isn't it) on an installer for a system I have created.  I am writing it in python because I can and because python makes it fairly easy.  This is also my subtle attempt to get my employer to warm up to python.

I have it installing and configuring apache, postgres, my app and some various other things just fine.  Essentially it just calls the installers and edits any config files for me.

Now my only problem is that I need to use it to create my postgres database.  So What I am wondering is this, is there is anything out there to to easily connect to a postgres DB via python.  Before you answer and list a dozen things, there is a catch...

The catch is that whatever it is also needs to have an installer that can run in quite mode.  I need a totally unattended installer.  I tried PyGreSQL, but alas no quiet installer.

I can use OleDB, ODBC, or a direct connection for this task.  All are acceptable.

Alternatively, could I manually copy the pygres files somewhere?

So python loving community, anyone have any ideas?

---

### Post by themusicwave on 2008-03-10
still no advice?

I'll keep on googling.

---

### Post by dwblas on 2008-03-11
There are several simplified APIs like SQLAlchemy that connect to most SQL databases including Postgres. They can be installed via Synaptic/apt-get.  Sorry, I don't recall the names of any others but a google for Python SQL may give some more hits.  Also, why not SQLite.  It doesn't require a running daemon process and It's included with Python-no installer necessary, unless it is too "light" and there is something missing
[http://www.rmunn.com/sqlalchemy-tutorial/tutorial.html](http://www.rmunn.com/sqlalchemy-tutorial/tutorial.html)

---

