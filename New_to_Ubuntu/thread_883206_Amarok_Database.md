---
title: "Amarok Database"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Matuku on 2008-08-07
Where is the Amarok Database saved if you are using MySQL? I'm wondering if there is a way to simply transfer it onto some kind of storage so that when I reinstall I don't have to remake it. Or is it already under .home somewhere (which I have on a separate partition). If it is, how would I go about making amarok use it after reinstalling Ubuntu?

---

### Post by txcrackers on 2008-08-08
If you use MySQL for the database, it's stored where the MySQL server's set up to store it - and, no, it's not in your home directory.

However, if you use the SQLLite option, it **is** stored in your home directory, which you should back up the whole thing, whether or not you need/want to re-install.

---

### Post by logos34 on 2008-08-08
Here's the wiki page:

[http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)
(=>'Automatic backups')

---

