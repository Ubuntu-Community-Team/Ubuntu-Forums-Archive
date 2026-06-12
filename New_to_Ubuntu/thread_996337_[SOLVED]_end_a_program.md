---
title: "[SOLVED] end a program"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by fillintheblank on 2008-11-28
is there a ctrl+alt+delete function to end a program?

---

### Post by halitech on 2008-11-28
press ALT-F2 and run xkill is 1 way. This will turn your cursor into a skull and crossbones and whatever you click on will be closed. Open a terminal and do a killall nameofprogramto kill is another.

---

### Post by fillintheblank on 2008-11-28
i cna't find xkill...

---

### Post by a0u on 2008-11-28
> **fillintheblank said:**
> i cna't find xkill...
Isn't it already included by default?
Enter
```
xkill
```
into the terminal.

For older versions of Ubuntu, you may need to manually install from the repositories.
```
sudo apt-get xkill
```

Also, there's a "Force Quit" applet that you can add to a panel, if you're using GNOME.

---

### Post by lukjad on 2008-11-28
Try this:
Hit Ctrl+Alt+F1.
Then log in. (Using the usual name and password.)
Then type 

```
killall [program name]
```
For example, if I wanted to stop Firefox I would type:

```
killall firefox
```

EDIT: To get back to the desktop, hit Ctrl+Alt+F7

---

