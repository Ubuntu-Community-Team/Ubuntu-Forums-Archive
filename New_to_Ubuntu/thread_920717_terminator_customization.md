---
title: "terminator customization"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by adamogardner on 2008-09-15
I had it so my gnome terminal was black backgroud and colored fonts but I recently changed my default terminal emulator to terminator.  I want to do a few things but am not finding the literature.
1. customize the colors.  
2, use shortcuts to divide the terminal horizontally and vertically (which is what terminator does) 
3, Make it always open as Maximized, w/out scroll bar, and quartered (4 terminals)

---

### Post by adamogardner on 2008-09-16
no seriously, what is up with terminator customizations?

---

### Post by sachin on 2008-11-13
hey here are solutions for 1 and 2, im not sure how you cold do 3., but I dont know all about terminator.
1. If you change the color settings in gnome terminal (right click profiles>profile preferences>colors) the terminator colors should change as well.
2. running a `man terminator` will give you the hotkeys

---

### Post by hydrotemplar on 2009-09-03
the terminatorrc file is:
~/.config/terminator/config

the options that I know of so far are:
fullscreen=true
maximised=true
borderless=true
scrollbar_position=hidden

---

### Post by Eisenwinter on 2009-09-03
Open the terminal:
```
man terminator_config
```

This man-page explains all the options and how to edit the configuration file, for full customization possibilities.

---

### Post by adamogardner on 2009-09-17
thankyou

---

