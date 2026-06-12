---
title: "combination of SHIFT + UP/DOWN ARROW do not function as before"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by Javier_Portugal on 2014-04-18
Hi,

I have with this issue for some time, I tried to find some information in the web but till now, I couldn't find any usefull one.

Problem: In file manager, or in openoffice Calc or Writer, when I tried to selec files or lines with "SHIFT + ARROW", what happened is that the bright of that only window change... just after some clics on the arrow (and that the window got darker or lighter) begun the selection of the files.

Clue: I installed Cairo dock some time ago, then, I uninstalled.  Maybe that program modified the "normal" use of SHIFT + UP/DOWN ARROW.  But I am not sure.

System: Ubuntu 12.04, laptop Lenovo Core I-3, GNOME Shell 3.4.1, Nautilus.

Thanks in advance with any help about this annoying issue.

BR

---

### Post by Javier_Portugal on 2014-04-19
Hi,
I got the solution.

The problem was caused by COMPIZ application.  To solve you need to run $ ccsm , (Compiz configuration manager), look for Accessibility, then Opacity button and enter there, and find the Bright tab.  That's it.
Thanks.

---

