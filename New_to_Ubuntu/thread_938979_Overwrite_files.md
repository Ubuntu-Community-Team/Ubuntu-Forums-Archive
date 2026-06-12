---
title: "Overwrite files?"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by NyTE on 2008-10-05
Im trying to overwrite a file in my /usr/lib/ folder but it says "Permission denied"

What do I need to do

---

### Post by halitech on 2008-10-05
are you trying to do it in a gui (ie Nautilus) or CLI?

---

### Post by NyTE on 2008-10-05
in Nautilus

---

### Post by halitech on 2008-10-05
then you will need to open Nautilus as root

***WARNING*** Be VERY careful when using this as you can damage your system if you make a mistake and I take no responsibility for any action you take on your system

open a terminal and type ```
gksu nautilus
```

---

### Post by NyTE on 2008-10-05
Ok thanks i got it

---

### Post by fooman on 2008-10-05
or install nautilus-gksu and you can right click in nautilus,  choose "open as administrator" and make the changes in gedit.  get it in synaptic,  or from a terminal:

```
sudo apt-get install nautilus-gksu
```

---

