---
title: "HELP menu missing"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by heiowge on 2008-08-17
I've come to my inlaws who are using Hardy.  They've managed to remove the menu bars from the desktop (Applications, Places, etc).

I can either reinstall everything (major problem) or rebuild everything (so I have to find everything).  is there a better way to quickly retrieve or reinstall from a restart disc, or elsewhere?

---

### Post by Perfect Storm on 2008-08-17
If it's the bars:

press <alt>+<F2>
Then:
```
gnome-panel
```
From there you can add another bar and/or stuff to your bar(s).

---

### Post by heiowge on 2008-08-17
That didn't seem to do anything.

I have managed to get the ubuntu symbol and if I left click and hold on it, I get a windows-esque drop down menu.

What I really want is the original ubuntu menu that works in the normal way.

All my menu entries are there, but the menu isn't tabbed.

---

### Post by Sorivenul on 2008-08-17
Are you saying they removed the Gnome Panels?  If that's the case see [THIS]("http://ubuntuforums.org/showthread.php?t=881301") post.

However, I think the proper remove and reinstall command should be ```
sudo apt-get remove gnome-panel nautilus && sudo apt-get install gnome-panel nautilus
```

Good luck!

---

### Post by Perfect Storm on 2008-08-17
> **heiowge said:**
> That didn't seem to do anything.

I have managed to get the ubuntu symbol and if I left click and hold on it, I get a windows-esque drop down menu.

What I really want is the original ubuntu menu that works in the normal way.

All my menu entries are there, but the menu isn't tabbed.

okay, wasn't sure what you meant.
Right click on your panel. Click "add to panel". Scroll down and pick "menu bar" (not Main menu).

---

### Post by sisco311 on 2008-08-17
EDIT:Never mind!

---

### Post by heiowge on 2008-08-17
Thanks guys, but there's more missing here.  Looks like their son has let his friends have a play on the machine.  Restart time!!!

---

