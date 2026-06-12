---
title: "How to add a shortcut  to /home/user on my desktop"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by George7a on 2008-11-03
Hi,

How can I add a shortcut to /home/user on my desktop?

- George

---

### Post by tuxxy on 2008-11-03
[http://ubuntuforums.org/showthread.php?t=684623](http://ubuntuforums.org/showthread.php?t=684623)

---

### Post by Fass on 2008-11-03
In a terminal, type:

```
gconf-editor
```

Click through to Apps -> Nautilus -> Desktop. There, tick the square by "home_icon_visible".

---

### Post by MrWES on 2008-11-03
[http://ubuntuforums.org/showthread.php?p=6030111#post6030111](http://ubuntuforums.org/showthread.php?p=6030111#post6030111)

---

### Post by Qlontz on 2008-11-03
If you press <alt><f2> and type gconf-editor and locate Nuatilus > Desktop, under Apps in the tree on the left, you will find an option to place home icon/computer icon/trash icon/network icon on desktop.

---

### Post by George7a on 2008-11-04
I have tried that, and I missed up!

I change the string value of home icon name and I kept getting an error. So I searched for this error and one of the posts I found said to unset this variable and recreate it. so I did. But now there is nothing on my desktop (though some of the options I checked, and I added a shortcut to the termenal) the mouse's right click is no working on the desktop and niether is the left click (selection)! What should I do?

Please help!

- George

---

