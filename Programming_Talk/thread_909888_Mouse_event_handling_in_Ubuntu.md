---
title: "Mouse event handling in Ubuntu"
date: 2008-09-04
forum: Programming Talk
---

### Post by shantanu.nalawade on 2008-09-04
Hi everyone :),

I've recently installed ubuntu. I'm working on a project for which I have to capture the mouse events.

Also besides capturing the events i have to display a secondary cursor on the screen.

Please i need help as this project holds grave importance in our college curriculum.

I've been researching on this but my efforts have been in vain.
I'm aware that the driver writes to the /dev/input file but i need write a program to do all this.

Any kind of help would be appreciated.

---

### Post by Zugzwang on 2008-09-04
Linux consists of a lot of components. You will need to find out which components are responsible for the parts of your task. If it suffices to do that while the X-server is running, it might be worth looking into the Xlib documentation.

---

### Post by shantanu.nalawade on 2008-09-05
Thanks alot man.:)

---

