---
title: "Xserver Help"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Samerious on 2008-11-26
[http://ubuntuforums.org/showpost.php?p=3908174&postcount=2](http://ubuntuforums.org/showpost.php?p=3908174&postcount=2)
I need someone to help me who has done this before. I typed in the code 
```
 sudo /etc/init.d/gdm stop

```
It brought me to a black screen that didn't do much It was like a DOS window it checked a few things and they said OK next them... I'm not sure what it was suppose to do.

---

### Post by nhasian on 2008-11-27
you have seven virtual consoles (accessible by pressing Ctrl-Alt-F1 to F7).  Press Ctrl-Alt-F1 to go to the first one and you can stop the GDM (graphical display manager) from there.  

Note Ctrl-Alt-F7 returns you to your graphical display.

---

### Post by Samerious on 2008-11-27
Ok with that advice i got a bit further... But now when i try to do the line:
```

X :3 -ac

```
it says it doesn't recognise that event.

---

### Post by Samerious on 2008-11-27
bump

---

### Post by nhasian on 2008-11-28
shouldnt you put sudo infront of that command?

```
sudo X :3 -ac
```

---

