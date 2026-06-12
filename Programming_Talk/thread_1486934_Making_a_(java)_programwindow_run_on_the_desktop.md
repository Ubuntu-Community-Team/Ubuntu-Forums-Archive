---
title: "Making a (java) program/window run on the desktop"
date: 2010-05-18
forum: Programming Talk
---

### Post by bvdelft on 2010-05-18
Hi,

I am playing with Java on Ubuntu and trying to make an application that will be running on the desktop, much as in the Ubuntu Notebook Remix edition (but of course waaay better ;-] ). Now I would like for my application to

- remain visible when pressing Show-Desktop shortcut (already managed that)
- be excluded from alt-tabbing
- not be visible as an icon in the window panel

I suspect the last two points can be solved at the same time, on the other hand, if you think that I should use a different approach than Java (e.g. use another language / program a widget), please let me know :-)

---

### Post by .:PiXi²:. on 2010-05-18
In Java: instead of starting from a JFrame, start from a JDialog. You can do everything in a JDialog what you can do in a JFrame, but it will not be visible in any listing of the currently open windows.

---

### Post by bvdelft on 2010-05-18
Thanks! Well, JDialog didn't work, but JWindow did!
EDIT: Oh now, it did not really, JDialog requires an existing JFrame, but JWindow can't get focus...

---

### Post by .:PiXi²:. on 2010-05-19
Are you sure that a JDialog requires an existing JFrame?
Try this constructor:
```

JDialog(null, "I'm a non-modal JDialog without an owner frame") 

```

---

### Post by dragos2 on 2010-05-19
If you want to be productive use Netbeans and draw swing interfaces quickly although you
can get the project out of your hands with it.

---

### Post by bvdelft on 2010-05-19
> **.:PiXi²:. said:**
> 
Try this constructor:
```

JDialog(null, "I'm a non-modal JDialog without an owner frame") 

```

Nope, although there is no owner frame, the dialog does appear in the Alt-Tab and in the gnome-panel... Is there a possibility to minimize a JFrame to the tray (so not the alt-tabbable panel) but leaving the JWindow / JDialog elements in place? Or should I just switch to creating a screenlet / gDesklet ?

(PS: Needed to alter our code a little PiXi, null made an amibiguous reference since the method is overloaded for both Frames and Dialogs: )
```

JDialog((Frame) null, "I'm a non-modal JDialog without an owner frame")

```

---

### Post by .:PiXi²:. on 2010-05-20
I think creating a screenlet or a gDesklet is the best option.

---

