---
title: "Menu list problem"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by ViliX64 on 2013-03-16
Hi, I have a problem, I have uninstalled wine (using: sudo apt-get autoremove wine), but I still have a menu entry. 
I can not get rid of it, because it is not listed in menu list settings.
[ATTACH=CONFIG]240252[/ATTACH]

---

### Post by Merrattic on 2013-03-16
Try visiting ***/usr/share/applications***, and deleting/moving anything to do with **wine** in there

---

### Post by ViliX64 on 2013-03-16
Sorry to dissapoint you Merrattic but I have already tried that, there is nothing connected to wine..

---

### Post by sudodus on 2013-03-17
Read my longer post in your other thread, but briefly, use this command instead

```
sudo apt-get purge wine
```

to get rid of wine, at least if you installed it from the repositories.
[COLOR=#808080]If you installed wine some other way, you need to uninstall it that way too.[/COLOR]

---

### Post by ViliX64 on 2013-03-17
Well, I have been exploring in filesystem anyway and found something that looked like a configuration file, i have edited it and wine item is no more :)

---

### Post by Merrattic on 2013-03-17
What did you find and where ?

---

### Post by ViliX64 on 2013-03-17
Here you go:
```
/etc/xdg/menus/
``` 
and 
```
home/.config/menus/
```

There are some files ending .menu (it is xml format i suppose).
With some deleting/adjusting, you can do thing that menu setting is not capable

---

### Post by rburkartjo on 2013-03-17
try this to completely remove wine
[http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html](http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html)

---

### Post by ViliX64 on 2013-03-18
It wasn't problem with removing wine, it was problem with menu lists...

---

### Post by sudodus on 2013-03-18
> **rburkartjo said:**
> try this to completely remove wine
[http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html](http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html)

+1

This is a good link :-)

---

