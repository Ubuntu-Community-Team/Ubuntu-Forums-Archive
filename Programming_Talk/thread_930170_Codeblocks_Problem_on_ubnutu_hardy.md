---
title: "Codeblocks Problem on ubnutu hardy"
date: 2008-09-25
forum: Programming Talk
---

### Post by fahdovski on 2008-09-25
I installed codeblocks but space button doesn't work
it opens a list of C++ command 
Why space button d'ont work.:guitar:

---

### Post by SeanHodges on 2008-09-26
Are you using a french keyboard? This appears to be a common occurrence on (but not limited to) French keyboard layouts:

> Space bar problem: 

Under Ubuntu 8.04 (Hardy Heron), the space bar key doesn&#8217;t work with Code::Blocks. The problem comes from the configuration of the xorg server (cf. bug #221112): 

sudo gedit /etc/X11/xorg.conf 

and comment the following line by adding #: 

#Option        "XkbVariant"    "oss"

[http://lgp203.free.fr/spip/spip.php?article1](http://lgp203.free.fr/spip/spip.php?article1)

---

