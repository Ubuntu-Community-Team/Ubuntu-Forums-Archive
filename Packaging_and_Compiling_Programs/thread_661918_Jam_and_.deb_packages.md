---
title: "Jam and .deb packages"
date: 2008-01-08
forum: Packaging and Compiling Programs
---

### Post by rmores on 2008-01-08
Hi,
I wonder if I can make a deb package with jam makefiles instead of gnu make, like with checkinstall.

---

### Post by Perfect Storm on 2008-01-10
Well you could build a .deb package from the scratch, otherwise checkinstall can't handle jam.

---

### Post by rmores on 2008-01-10
I haven't found any guide on that. Can you post a link?

---

### Post by wesswei on 2008-07-31
Not sure if you're still wanting to build deb packages. I'm just starting to build a few myself.

[http://www.linuxdevices.com/articles/AT8047723203.html](http://www.linuxdevices.com/articles/AT8047723203.html)

This will help you build from scratch.

I do remember seeing this somewhere, but I'm not sure if it works.

sudo checkinstall -Dy "jam"

---

