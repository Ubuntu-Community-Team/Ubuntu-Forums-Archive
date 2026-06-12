---
title: "Changing display resolution from commandline"
date: 2011-02-21
forum: Programming Talk
---

### Post by Vesa Paatero on 2011-02-21
Hello,

I'd like to change display resolution by using shell command(s). Normally I change it via gnome-display-properties, but that program is interactive and I'd prefer to do it from a script. 

I am planning to make a startup script that changes resolution to show things bigger in a certain program which itself provides no option to change the size of things:

  - change to smaller resolution
  - run the program
  - change to normal resolution

Thanks for any help!

Vesa

---

### Post by Vesa Paatero on 2011-02-21
It seems that the xrandr utility solves the problem.

---

