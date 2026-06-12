---
title: "boot my ubuntu from command line"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by ubhi on 2008-10-30
hi all, i want to boot up my ubuntu system from terminal means from command line with network support as well, after that if i wish to go onto graphic mode then i can go with startx option or something else...

can anyone suggest me the proper way..??

---

### Post by skymera on 2008-10-30
You can remove GDM.
Which will leave you in command console and simply type startx to go to GUI.

---

### Post by aeiah on 2008-10-30
changing /etc/inittab default run level to 3 should do the trick if you dont want to remove anything

---

### Post by skymera on 2008-10-30
> **aeiah said:**
> changing /etc/inittab default run level to 3 should do the trick if you dont want to remove anything

I'm pretty sure /etc/inittab doesn't exist on Ubuntu 8.04 / 8.10

---

