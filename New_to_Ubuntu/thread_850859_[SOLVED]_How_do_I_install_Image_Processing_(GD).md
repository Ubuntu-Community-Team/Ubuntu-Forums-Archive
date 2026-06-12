---
title: "[SOLVED] How do I install Image Processing (GD)"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by WebSiteGuru on 2008-07-06
Hi,

Currently, I am trying to configured my computer to use as a localhost for my local development. I got everything setup (Apache2, PHP5, MySQL) But I need Image Processing (GD) install. How do I go about doing it? I search for the way, but can not find it. :(

Please help. Thanks!

---

### Post by scott_g on 2008-07-06
Go to Synaptic Package Manager, and search for gd; the package you're looking for is php-gd I believe.  

Could also try:
```

sudo apt-get install php-gd
```

Then it should work.

Scott

---

### Post by WebSiteGuru on 2008-07-09
Thanks Scott, it was actually php5-gd when I found it. :D

---

