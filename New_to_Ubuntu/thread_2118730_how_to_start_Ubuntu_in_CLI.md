---
title: "how to start Ubuntu in CLI"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by uow513 on 2013-02-22
Hi I'm new to Ubuntu. Can someone tell me how to start system with Command line Please. Your assistance is much appreciated.

uow513

---

### Post by Cheesemill on 2013-02-22
The following command will disable the display manager meaning your system will always boot in CLI mode:
```
 echo "manual" | sudo tee -a /etc/init/lightdm.override 
```If you want to start the GUI just login and type:
```
 startx
```

---

### Post by MG&amp;TL on 2013-02-22
> **uow513 said:**
> Hi I'm new to Ubuntu. Can someone tell me how to start system with Command line Please. Your assistance is much appreciated.
 
uow513
 
While Cheesemill's solution is what you want to do, why do you want to do that? You can have graphical terminals in a graphical session or virtual terminals by pressing Ctrl-Alt-F1 or any other function key except F7.

---

### Post by uow513 on 2013-03-04
Thanks guys. I've got more than I asked for.

---

