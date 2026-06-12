---
title: "Hello, all. I need some help..."
date: 2008-05-19
forum: New to Ubuntu
---

### Post by munkyinvasion on 2008-05-19
I recently tried to install Hardy Heron onto my Flash drive, and it went on there just fine, but whenever I try to login, it just hangs at a beige screen with a functional pointer. What should I do? I would really prefer not to install it onto my computer's HDD but I can if absolutely necesary. Thanks for any help

---

### Post by bubba_169 on 2008-05-19
What are your reasons for not wanting it on your HDD? If its just you dont like patitioning then why not use WUBI instead? It can let you install Ubuntu from within Windows with no partitioning, and remove it just as easily...

---

### Post by GolanTrevize on 2008-05-19
> **munkyinvasion said:**
> I recently tried to install Hardy Heron onto my Flash drive, and it went on there just fine, but whenever I try to login, it just hangs at a beige screen with a functional pointer. What should I do? I would really prefer not to install it onto my computer's HDD but I can if absolutely necesary. Thanks for any help

You could change to the console (Ctlr-ALT-F1 .... Ctlr-ALT-F6) and try to login.
Then take a look at /var/log/Xorg.0.log. Propably you can get more information from that.

Another source is the .xsession-errors in your home-directory

---

### Post by munkyinvasion on 2008-05-19
ok I'll look at those files when I get home. Does wubi have all of ubuntu or is it missing some parts?

---

### Post by bubba_169 on 2008-05-19
WUBI is a complete ubuntu install only it installs it into a file on your windows drive rather than a separate partition... :D

---

### Post by benpage26 on 2008-05-19
As far as i know wubi is the whole of Ubuntu, just installed to a file under windows rather than a seperate partition.

---

### Post by chinchilla2392 on 2008-05-19
wubi isnt missing anything.
try it out. if it doesnt work, which isnt likely at all
you can uninstall it from windows in an instant

---

### Post by munkyinvasion on 2008-05-19
Alright, I'm going to try wubi when i get home. I'll post the results later.

---

