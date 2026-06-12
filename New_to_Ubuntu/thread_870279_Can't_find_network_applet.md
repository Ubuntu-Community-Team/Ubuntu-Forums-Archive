---
title: "Can't find network applet"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by maoglone on 2008-07-25
Looks like I removed the network applet from my panel, and I'd really like to have it there.  Problem is, when I open the "add to panel" menu, the applet doesn't appear as a selection.  Any idea where I can find it?  Thanks!

---

### Post by Nepherte on 2008-07-25
You should enable 'Network Manager' (command: nm-applet) under system > preferences > sessions.

---

### Post by maoglone on 2008-07-25
Still can't get the applet to show up in my panel.  Next step?

---

### Post by Nepherte on 2008-07-25
Did you try to log in again? Try explicitly entering the command in a terminal:
```
nm-applet
```

---

### Post by maoglone on 2008-07-25
Nothing happened.

---

### Post by Nepherte on 2008-07-25
Did it give any output? It damn works over here :(

---

### Post by maoglone on 2008-07-25
No output.  I certainly hope that "remove from panel" button didn't wipe the thing off the computer completely ;)

---

### Post by nikgare on 2008-07-25
You need to make sure that the **Notification Area** is there.

---

### Post by maoglone on 2008-07-25
Any other ideas?

---

### Post by maoglone on 2008-07-25
> **nikgare said:**
> You need to make sure that the **Notification Area** is there.

Not sure what that means...

---

### Post by fatality_uk on 2008-07-25
Right click on any panel.
Select **Add to panel...**
Open a terminal and type **nm-applet**
That *will* create a new instance of the nm-applet

---

### Post by maoglone on 2008-07-25
> **maoglone said:**
> Not sure what that means...

Scratch that.  I figured it out, though I now have 7 network managers on my panel.  I'm a douche.  Now to figure out how to get 6 to go away.  

Thanks, y'all!

---

### Post by ajgreeny on 2008-07-25
I'm sure there may be an easier way to do this but the way I managed when I ended up with several glipper applets after crashes, was to delete the files from ~/gconf/app-s/panel/applets.  To do it right you need to find out what each applet is first by opening up **gconf-editor** (use Alt+F2) and navigate to apps>>panel>>applets and you will find out what each applet is related to, then delete that numbered applet folder (~/gconf/app-s/panel/applets) in nautilus.  As I say, there may be a quicker way direct from gconf-editor, but if so I couldn't find it.

---

### Post by msdisatis on 2010-12-21
Hi,
At frist, you should add **Notification Area** to your panel.
Then open a Terminal and type "**sudo nm-applet**".

---

