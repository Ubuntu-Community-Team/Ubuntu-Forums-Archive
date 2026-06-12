---
title: "Panel and icon bar disappeared; Terminal can't be open"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by letter on 2013-04-24
Hi there,

I somehow managed to crash the panel and the icon bar in my account. Because it's gone now. 

I tried to open the terminal and follow these steps:
[http://www.youtube.com/watch?v=5tW_UyCHUv0](http://www.youtube.com/watch?v=5tW_UyCHUv0)

But without results. So I've tried to install the panel again. But no results. The panel and the icon bar (taskbar) are still missing. In addition to that I can't open the terminal with the short cut (ctl+alt+t) anymore. But everything works fine in the guest account. :(

---

### Post by ibjsb4 on 2013-04-24
Ctrl + Alt + F1 (thru F6) will get you to tty

Ctrl + Alt + F7 will return you to your desktop

---

### Post by letter on 2013-04-24
Thanks, but how do I solve the missing menubar and the missing panel?

---

### Post by ibjsb4 on 2013-04-24
One way would be to reset Unity.  Are you running 12.10?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+unity+12.10&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+unity+12.10&sa=Search&cof=FORID:9)

---

### Post by letter on 2013-04-24
No, 12.04

Isn't there another way besides resetting? I made some custom changes (3d cube; 3d windows, ....and other effects). I don't want to do it again.

---

### Post by ibjsb4 on 2013-04-24
> **letter said:**
> No, 12.04

Isn't there another way besides resetting? I made some custom changes (3d cube; 3d windows, ....and other effects). I don't want to do it again.

Im sure there is, but I run metacity and not familiar with compiz.  So  you will have to wait for someone else to come along with an answer to  that.  Good luck :)

---

### Post by letter on 2013-04-24
...thanks anyway.... :(

---

### Post by stylintile on 2013-05-05
I'm not on unity anymore, but if I remember right from when I did the same thing I had to run:
```
gnome-panel &
```

and then go into panel preferences with Super key+right click on a blank space in the panel, then recheck the box to have it start automatically.

Hope this helps.

---

