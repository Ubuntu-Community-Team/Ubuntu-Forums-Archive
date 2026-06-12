---
title: "[SOLVED] Help!!!"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by heiowge on 2008-08-17
Update manager:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any ideas what to do?

---

### Post by dje on 2008-08-17
in a terminal (applications >> accessories >> terminal) run:
```
sudo dpkg --configure -a
```
please use search before posting in future, there are a lot of threads on this topic and also please use descriptive thread titles as it may well get you more help quicker ;)

dje

---

### Post by rune0077 on 2008-08-17
Try what it says. Open a terminal and run:

```
dpkg --configure -a
```

---

### Post by dje on 2008-08-17
> **rune0077 said:**
> Try what it says. Open a terminal and run:

```
dpkg --configure -a
```

it requires root privilidges so you must prepend it with sudo ;)

dje

---

### Post by heiowge on 2008-08-17
Thanks.  It works.

Funny.  it failed when i tried it before!  That's why I looked for help.

---

### Post by Riffer on 2008-08-17
A couple of things.

Try running 

Sudo dpkg --configure -a

in your terminal.

Change your server by going to the drop down menus System > Administration > Software Sources.  It will ask for your password, give it.  In the new window there will be some tabs, make sure you have "Ubuntu Software" open.  In the middle of that tab is popup box marked "Download From", click there and choose a new server, click close.  

From there you could run your update manager again.

---

