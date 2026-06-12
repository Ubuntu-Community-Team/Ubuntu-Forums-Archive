---
title: "Removing Avg2012flx"
date: 2013-11-10
forum: New to Ubuntu
---

### Post by johnwill on 2013-11-10
Ubuntu 12.04 LTS Dual Boot with Window's 7.

Removing AVG 2012flx:
Message stating; dpkg: warning:while removing avg2012flx directory '/opt/avg/av/lib not empty so not removed.
How do I continue now,is it possible to remove the above directory.

---

### Post by deadflowr on 2013-11-10
How did you install it.
And how are you trying to remove it?

What commands are you running?

---

### Post by johnwill on 2013-11-10
Hello.
I installed Avg via their website;

Tried to uninstall: sudo dpkg -R -P avg2012flx

---

### Post by deadflowr on 2013-11-10
```
sudo dpkg -r <packagename>
```
should be all you need to do.

I don't know what -R is.
You can also try with --purge.

---

### Post by johnwill on 2013-11-10
Hello Deadflower.
Thank you for your reply.

Tried sudo  dpkg  -r avg2012flx: message stating warning: Their is no installed package matching avg2012flx

Tried: dpkg  -r '/opt/avg/av/lib

Message: '/opt/avg/av/lib  is illegal must start with alphanumeric character

---

### Post by deadflowr on 2013-11-10
Did you install the tar or the deb?

Looky at this older howto from avg
[http://free.avg.com/us-en/129025](http://free.avg.com/us-en/129025)

---

### Post by sandyd on 2013-11-10
> **johnwill said:**
> Ubuntu 12.04 LTS Dual Boot with Window's 7.

Removing AVG 2012flx:
Message stating; dpkg: warning:while removing avg2012flx directory '/opt/avg/av/lib not empty so not removed.
How do I continue now,is it possible to remove the above directory.

The message is only a warning - the package should be removed if you installed it using a deb file

---

### Post by johnwill on 2013-11-11
Hello Deadflower.

A Deb file.

---

### Post by johnwill on 2013-11-13
Hello Deadflower and Sandyed.

Thank you both for your help.
Johnwill

---

