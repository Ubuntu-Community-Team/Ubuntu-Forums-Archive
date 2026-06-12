---
title: "How about python 2.4-pysqlite2 package?"
date: 2005-06-21
forum: Programming Talk
---

### Post by JuanC on 2005-06-21
Hi to all ,

I show taht ubuntu/Kubuntu has a lot of python modules preinstalled , but i try to find a package call pysqlite2 , but i can find , this package is in debian testing and unstable.

[http://packages.debian.org/unstable/python/python2.4-pysqlite2](http://packages.debian.org/unstable/python/python2.4-pysqlite2)
[http://packages.debian.org/testing/python/python2.4-pysqlite2](http://packages.debian.org/testing/python/python2.4-pysqlite2)

I don't show it in synaptic to install.

Why this package isn't be in Hoary?

Another question , why python2.4-qt3 isn't be preinstalled in kubuntu? I think is good idea to include it , this package is common using to create KDE/Qt app in Python.

---

### Post by buffbikedude on 2005-06-26
Considering sqlite3 is the latest version, I doubt you'll find anyone who thinks it's worthwhile to put sqlite2 into Ubuntu.

I recommend you install sqlite 3 yourself in /usr/local.

---

### Post by buffbikedude on 2005-06-26
I agree with you about PyQT, though I have no need for it. If you want anything done about it this is the wrong place to post. The Kubuntu topic is better for that.

---

### Post by JuanC on 2005-06-26
[QUOTE=buffbikedude]Considering sqlite3 is the latest version, I doubt you'll find anyone who thinks it's worthwhile to put sqlite2 into Ubuntu.

I recommend you install sqlite 3 yourself in /usr/local.[/QUOTE]

I think you are confusing pysqlite to sqlite.

In Hoary there is a package called python2.4-sqlite that uses sqlite 1 or 2 (Too old version of sqlite , in my opinion).

I'm talking about python2.4-pysqlite2 package that use sqlite 3 , this package is a binding of sqlite 3 into python , more info [www.pysqlite.org](www.pysqlite.org) .

My question , is that Ubuntu/Kubuntu has a lot of python modules preinstalled , why this package isn't be in Hoary and is in debian testing and unstable.

---

### Post by buffbikedude on 2005-06-27
Sorry...my bad. pysqlite2 uses sqlite 3.0 all right.

I installed the latest pysqlite2 knowing that it requires sqlite 3.1 but Ubuntu has sqlite 3.08. It installed without complaining, but some of the tests failed.

I'm going to remove the ubuntu sqlite3 package and install the latest version from source in /usr/local, where I installed pysqlite, and reinstall pysqlite, if needed.

I don't use any Debian packages, only Ubuntu. I like to keep my /usr prefix pristine, and install all packages not included either to /usr/local, or to my home directory.

---

