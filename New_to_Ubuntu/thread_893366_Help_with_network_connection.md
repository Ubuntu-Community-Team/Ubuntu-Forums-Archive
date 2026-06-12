---
title: "Help with network connection"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by frogbrains on 2008-08-18
Oooh, what an unoriginal name of a new thread.  Anyway, I do need help.  Ya know those bars that appear at the top and bottom of the Ubuntu desktop that one can put links and widgets and stuff on?  Right, well I accidentally deleted one of them, and now I can't connect to my network like I could before.  Please tell me how to fix this problem.
Adam

---

### Post by cdtech on 2008-08-18
Open a terminal and type:
```
gnome-panel
```

Hope this helps......

---

### Post by nothingspecial on 2008-08-18
Right click on your remaining bar and choose add to panel.
Scroll down untill you find network monitor.
Click on it.
It will appear on your panel.
It may look different but it will do the same job.
If you want 2 panels, right click on your remaining panel and choose new panel.
Using this method you can have however many panels you want with what you want on whichever panel you want it on.
Cool.

---

### Post by tarps87 on 2008-08-18
The original network manager bit is part of the notification area, which you can add to the panel the same as above. If it still does not appear post back and I'll find the other command for it when I get back to my pc

Edit: I think this command will do it nm-applet --sm-disable
Note: You need the notification area active and you may need to add this to the session file

---

