---
title: "reading keyboard events from CLI?"
date: 2009-12-30
forum: Programming Talk
---

### Post by TheHimself on 2009-12-30
How can one write a shell script that would do certain things if a specific key combination is pressed?

Also a related question: how can one run an application without allowing it to read (and act upon) keyboard events? 

Than you.

---

### Post by blazemore on 2009-12-30
That's real-time programming, not shell scripting.
Any key combinations would be interpreted by the shell/window-manager, not your program.
The only exception would be Ctrl+C, which programs can use to exit cleanly if they want, I think you could get it to do something else; bit of a hack though.

---

### Post by TheHimself on 2009-12-31
Yes, it's interpreted by  shell/window-manager but then it's passed to the program/window which is in focus. That's how hotkeys in applications work. Also there are CLI programs which have menus.  I want to know how to employ this.

My second question is this: how can one simultaneously run two applications  from CLI?

---

### Post by hessiess on 2009-12-31
Ncurses.

---

### Post by falconindy on 2009-12-31
> **TheHimself said:**
> Yes, it's interpreted by  shell/window-manager but then it's passed to the program/window which is in focus. That's how hotkeys in applications work. Also there are CLI programs which have menus.  I want to know how to employ this.

My second question is this: how can one simultaneously run two applications  from CLI?

Look at the source code for [DWM](http://dwm.suckless.org/). it's only 2000 lines and is coded very cleanly. It employs the use of a "master" mod key plus modifiers and a letter/number to accomplish a task.

[This](http://tldp.org/LDP/gs/node5.html) is a decent intro on Linux's job control.

---

