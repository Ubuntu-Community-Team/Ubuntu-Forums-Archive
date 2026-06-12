---
title: "newbie trying to install apr and apr-util for Apache, need help"
date: 2016-05-26
forum: New to Ubuntu
---

### Post by david_ford3 on 2016-05-26
I downloaded Apache and tried to install but it said I needed apr.

downloaded apr and apr-util

from looking at this instruction, I don't know how to load apr and apr-util to the prescribed subdirectory,/httpd_source_tree_root/srclib/ :

APR and APR-Util
Make sure you have APR and APR-Util already installed on       your system. If you don't, or prefer to not use the system-provided       versions, download the latest versions of both APR and APR-Util       from [Apache APR]("http://apr.apache.org/"), unpack       them into /httpd_source_tree_root/srclib/apr and /httpd_source_tree_root/srclib/apr-util       (be sure the directory names do not have version numbers; for example,       the APR distribution must be under /httpd_source_tree_root/srclib/apr/) and use       ./configure's --with-included-apr       option.  On some platforms, you may have to install the        corresponding -dev packages to allow httpd to build        against your installed copy of APR and APR-Util.



I tried ./configure prefix=/httpd_source_tree_root/srclib/, but it didn't like that.  I did create all that directory structure by hand, as nothing else seemed to be creating it.

I then tried running 
  ./configure
   make
   make install

Seems to have created another structure of stuff under "local", but nothing working, and I seem to have closed the terminal window that gave me some error messages.

So, sorry to my rambling and lack of pertinent details.  How can I fix this, or backtrack and try another route?

---

### Post by david_ford3 on 2016-05-26
Never mind.  Part of Ubuntu.  Installed like that.

---

### Post by DuckHook on 2016-05-26
> **david_ford3 said:**
> Never mind.  Part of Ubuntu.  Installed like that.I take it you mean that it is already in the repositories and you installed using apt or software centre. If so *please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

### Post by izznogooood on 2016-05-28
I find that "tasksel" is a good tool for this sort of "jobs".

For installing a LAMP (<-- Google it) server you could "sudo tasksel install lamp-server"
(It comes pre-installed in 16.04)

You can read more about tasksel here: [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

