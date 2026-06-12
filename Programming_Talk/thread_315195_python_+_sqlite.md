---
title: "python + sqlite"
date: 2006-12-08
forum: Programming Talk
---

### Post by daniminas on 2006-12-08
Hi all

What i need to install on my Drapper to develop python applications with sqlite databases?.. all..

Thanks VERRY much))

Daniel

---

### Post by gummibaerchen on 2006-12-08
Hmm, first you need some knowledge.

I would just fix on sqlite, there is at least one DB-API with which you can access MySQL, PgSQL and SQLite.

What you need is python-sqlite2, I'm not sure wether it is in the repos, I compiled it myself.

[http://www.initd.org/tracker/pysqlite](http://www.initd.org/tracker/pysqlite)

And sqlite3 to create the databases.

---

### Post by pmasiar on 2006-12-09
Python 2.5 has sqlite as standard library. Remember, python's motto is "bateries included" :-)  Default python is 2.4 but 2.5 is also supported (has ubuntu logo in synaptic).

So your real question is, how to safely install python 2.5. Or, if you are brave, just install 2.5 on top of current 2.4 (using synaptic) and look if something breaks.

---

### Post by daniminas on 2006-12-09
Thanks for the answers.. i've my databases working now.. i been installed: 
sqlite
python2.4-pysqlite2
and..
sqlite-doc ;)

Tnx! :)

---

