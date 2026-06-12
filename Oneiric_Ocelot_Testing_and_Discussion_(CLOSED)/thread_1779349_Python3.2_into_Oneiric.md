---
title: "Python3.2 into Oneiric"
date: 2011-06-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-06-10
The latest lsb (lsb 4.0-0ubuntu13) package lsb-release depends on python3, which depends on python3.2.

These can of course coexist with the old python2.7 (from Natty), but it is evedent that python 2.7 will be dropped.

---

### Post by xebian on 2011-06-10
> **Harry33 said:**
> The latest lsb (lsb 4.0-0ubuntu13) package lsb-release depends on python3, which depends on python3.2.

These can of course coexist with the old python2.7 (from Natty), but it is evedent that python 2.7 will be dropped.

Great.  Does it mean Eric5 will be in as well?

---

### Post by dext on 2011-06-10
> **Harry33 said:**
> The latest lsb (lsb 4.0-0ubuntu13) package lsb-release depends on python3, which depends on python3.2.

These can of course coexist with the old python2.7 (from Natty), but it is evedent that python 2.7 will be dropped.
i dont think they will drop it, as it takes a long long time to rebuild all python packages with 3.x .Fedora are slowly rebuilding python packages for 3.x only but its a long slow process.

---

### Post by juancarlospaco on 2011-06-10
$ 2to3 -w

---

### Post by inportb on 2011-06-10
There are still some very popular modules that depend on Python 2.x, i.e. Twisted and SciPy. I don't quite think we're ready to ditch those ;)

---

### Post by Framli on 2011-06-11
2.7 won't be dropped, but 2.6 certainly will.

[http://irclogs.ubuntu.com/2011/06/10/%23ubuntu-meeting.html#t16:25](http://irclogs.ubuntu.com/2011/06/10/%23ubuntu-meeting.html#t16:25)

---

### Post by Yeeha on 2011-07-31
> **xebian said:**
> Great.  Does it mean Eric5 will be in as well?
Just wanted to try Eric5 and saw that there is no Eric5 but Eric4, why not if theres python3.2? Eric4 uses python2 and Eric5 python3.

---

### Post by jbicha on 2011-07-31
Yes, Python 2 is picking up speed towards obsolescence now that Qt and GTK3 work fine on Python 3. GTK apps have to convert from PyGTK to GObject Introspection first which is a bigger switch than the Python 3 transition.

See [https://blueprints.launchpad.net/python/+spec/foundations-o-python-versions](https://blueprints.launchpad.net/python/+spec/foundations-o-python-versions) where a goal for Ubuntu 12.04 is switching the main CD to Python 3 exclusively. Python 2 will stay in the repositories for quite a while though.

By the way, Arch has set python3 as the default python, which surprised me when I noticed that this week.

I didn't realize there was an Eric 5. I'll take a look at it this week. I think Debian is staying with Eric 4 for now, but I can ask.

---

### Post by jbicha on 2011-08-03
Ok, I followed up on eric5. The issue is that Debian hasn't yet packaged python3-qt4. See [http://pad.lv/400826](http://pad.lv/400826) .__[]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=558389")

---

