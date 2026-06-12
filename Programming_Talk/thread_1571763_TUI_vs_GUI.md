---
title: "TUI vs GUI???"
date: 2010-09-10
forum: Programming Talk
---

### Post by JohnElway on 2010-09-10
I'm interested in doing rapid app development in Python. Since this is mainly for prototyping purposes, I'm looking for a way of creating "rough" user interfaces. By this, I mean that they don't have to look professional, they just have to be flexible enough to make it look the way I want. Originally I was going to do this by creating a GUI (using something like GTK), but now I'm starting to think about TUIs (using ncurses).

I know very little about TUIs in general, so would it even be possible to use ncurses for an application written in Python? Assuming it is, what are the differences between creating a GUI versus a TUI? Would I be able to create the interface faster in pyGTK or ncurses?

---

### Post by juancarlospaco on 2010-09-10
See Urwid, just another Python battery.

Also install and try the program "dialog" from repo.

*TUI can be used on embebed systems, serial terminals, RS232, Servers and such.*

---

### Post by JohnElway on 2010-09-10
> **juancarlospaco said:**
> See Urwid, just another Python battery.

Also install and try the program "dialog" from repo.

*TUI can be used on embebed systems, serial terminals, RS232, Servers and such.*

Why Urwid? If I go the TUI route, I was thinking I would just use the curses module that comes with the default Python installation.

Also, I installed dialog, but how do I 'call' the dialog boxes from the terminal or within a shell script?

---

### Post by juancarlospaco on 2010-09-10
> **JohnElway said:**
> Why Urwid? If I go the TUI route, I was thinking I would just use the curses module that comes with the default Python installation.

Also, I installed dialog, but how do I 'call' the dialog boxes from the terminal or within a shell script?

Why not?, Urwid got ready-to-use ncurses widgets. 
You can use ncurses and make your widgets mannually tooo.

```
import os
os.system(dialog --progress --blahblah --someparameter)
```

---

### Post by nvteighen on 2010-09-11
curses is widely used and it works, although it's a really old-fashioned library that feels a bit weird. IIRC, there are other libraries, but like it or not, curses is the de facto standard and it's not a bad one.

---

