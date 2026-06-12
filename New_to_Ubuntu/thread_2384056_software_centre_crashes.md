---
title: "software centre crashes"
date: 2018-02-01
forum: New to Ubuntu
---

### Post by jim Kane on 2018-02-01
Using 16.04.1 just tried to open the software centre and it crashes, everything else works ok 


is there any way I can safely try and repair it 


thanks
mike

---

### Post by cruzer001 on 2018-02-02
Try reinstalling it.

Open a terminal (Ctrl + Alt + t) and enter:

```
sudo apt install --reinstall software-center
```

You may also want to look at AppGrid.

[http://www.appgrid.org/](http://www.appgrid.org/)

---

### Post by Autodave on 2018-02-02
Are you making sure that your system is up to date? In a terminal:

sudo apt-get update
sudo apt-get upgrade

---

### Post by jim Kane on 2018-02-02
thanks for your replies, dont think I will bother I use synaptc mostly just wanted to see if there where any epson drivers in it, but have now sorted that problem

---

