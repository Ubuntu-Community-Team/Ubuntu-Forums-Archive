---
title: "Connection Icon On Intrepid"
date: 2009-05-04
forum: Philippine Team
---

### Post by ysNoi on 2009-05-04
Guys, just want to ask some workaround on how to fix my problem on connection icon..!

Okey naman kasi may connection naman po ako kaso yung icon po ay may x po...!

Image attached...

Thanks...

---

### Post by loell on 2009-05-04
try to look at you "network information" by right clicking then proeprties.

---

### Post by ysNoi on 2009-05-04
Eto ang lumalabas siR pag check ko po...Pero connected naman po..! Eto nga ginagamit ko ngayon..!

Error displaying connection information:

---

### Post by loell on 2009-05-04
try removing and re-installing nm-applet

```
sudo apt-get remove --purge network-manager network-manager-gnome
```

and then reinstall it.

---

