---
title: "Update problem"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by ozbolt on 2008-07-25
I can update and do apt-get things normally, but there is one messege that I dont want to be there:
[[img]http://shrani.si/t/44/13N/4Ir2WZWy/screenshot.jpg[/img]](http://shrani.si/?44/13N/4Ir2WZWy/screenshot.png)

---

### Post by GreenN00b on 2008-07-25
Go here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
And follow the instructions ...

Probably you did not execute the following command:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```
in a terminal

---

### Post by AndyCooll on 2008-07-25
I had that message and simply re-imported the Wine repos GPG key.

:cool:

---

