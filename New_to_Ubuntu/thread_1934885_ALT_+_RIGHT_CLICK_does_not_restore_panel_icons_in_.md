---
title: "ALT + RIGHT CLICK does not restore panel icons in 11.10"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by suomalainen on 2012-03-03
Ubunteros,

I deleted by accident the battery, sound and network manager icons from panel by accident.

When I did the ALT+ RIGHT CLICK and "add to panel" these missing icons could not be located.

How can I get  them back?

Thanks everyone.!!!

---

### Post by mayur.shetye on 2012-03-03
Search for indicator applet in 'add to panel' window.
If it is not found install indicator applet complete using the command
```
sudo add-apt-repository ppa:jconti/gnome3
sudo apt-get update
sudo apt-get install indicator-applet-complete
```

---

### Post by suomalainen on 2012-03-03
Thanks buddy!!!

---

### Post by mayur.shetye on 2012-03-03
:)

---

