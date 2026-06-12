---
title: "The Composite extension is not available"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by XTR0RDiNAiRE on 2008-06-22
when i go to visual effects, and click on the second option
thats the message i get, what do i need to do to get this working

---

### Post by billgoldberg on 2008-06-22
Assuming you installed your graphics card either manually, with envy or by using "hardware drivers", open up xorg.

In a terminal (applications -> accessories) copy/paste this

```
gksudo gedit /etc/X11/xorg.conf
```

look for the line that says "composite" and change it from "0" to "1".

That worked for my ATI card in Ubuntu 7.10.

---

### Post by XTR0RDiNAiRE on 2008-06-23
appreciate the help ,

i finally got it working

thx

---

