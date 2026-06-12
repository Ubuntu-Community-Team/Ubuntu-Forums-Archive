---
title: "Block sites in Epiphany"
date: 2007-04-17
forum: Programming Talk
---

### Post by Alex99 on 2007-04-17
Is,
is there a way to block an entire site in epiphany - not just ads, but to create a blacklist of urls?
Thanks!
Alex

Edgy Eft, Epiphany 2.16.1

---

### Post by simplyw00x on 2007-04-17
If you use greasemonkey and the Kiwi Cloak userscript [1], you can block sites between certain hours of the day, for certain minutes of the hour. Some minor editing of this script (PM me if you'd like this done for you) will block sites you specify.

[1] [http://jeremyfreese.blogspot.com/2007/01/kiwi-cloak-quasi-coercive-anti-websurf.html](http://jeremyfreese.blogspot.com/2007/01/kiwi-cloak-quasi-coercive-anti-websurf.html)

---

### Post by phossal on 2007-04-18
Many routers give you that ability, if you're bent on blocking sites. You don't have to do it at the browser level.

---

### Post by kerry_s on 2007-04-18
You can use your /etc/hosts file to block sites. you just put "127.0.0.1 name-of-site.com" and it will be blocked.

I use a very large hosts file to block all bad sites. See attached->

---

### Post by Alex99 on 2007-04-18
Thanks, works very well!

---

