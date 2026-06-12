---
title: "Getting rid of a printer"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by lile001 on 2012-02-29
I have been reading tutorials about working with printers, and have successfully added some printers using the graphical interface "printers".  I need to get rid of an old printer that is no longer available.   However, the tutorials say to just delete inactive printers in this GUI.  There is no option I can find to do this, right click, etc, to delete a printer.  Nor could I figure out how to start this GUI as root  (sudo printers doesn't do anything.)  

How do I delete an old printer?  

P.S.  "Throw it out a second story window" isn't the sort of answer I am looking for, although that would be hilarious.

---

### Post by wyliecoyoteuk on 2012-02-29
try opening a wen browser and entering 

[http://localhost:631](http://localhost:631)

that should start the Cups interface.

---

### Post by MG&amp;TL on 2012-02-29
In the printers dialog, right-click on the printer-> delete. I'm assuming that's what you want to do. :) Although I'm thinking not...

If you do want to run the printer dialog as root, btw (for some unknown reason):

```
gksu gnome-control-center
```

---

### Post by lile001 on 2012-02-29
> **MG&TL said:**
> In the printers dialog, right-click on the printer-> delete. I'm assuming that's what you want to do. :) Although I'm thinking not...

If you do want to run the printer dialog as root, btw (for some unknown reason):

```
gksu gnome-control-center
```


Right click is disabled in my interface, i.e. nothing happens when I right click on a printer.  System Settings > Printers = No right clicky.  

Same thing if I use gksu gnome-control-center (which is why I was asking, I figured GOD could do anything, and sometimes ROOT has more options and functions in a program than regular me - there is some other program in System settings that works like this but I can't remember which one)  

Right click used to work for me too.  This is Ubuntu 11.10.  Have they changed this interface maybe? 

Still... tossing the printer out a window might be satisfying....

---

### Post by lile001 on 2012-02-29
> **wyliecoyoteuk said:**
> try opening a wen browser and entering 

[http://localhost:631](http://localhost:631)

that should start the Cups interface.


THat did it!

---

