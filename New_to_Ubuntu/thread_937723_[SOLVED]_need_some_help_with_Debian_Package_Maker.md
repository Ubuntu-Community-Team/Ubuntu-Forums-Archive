---
title: "[SOLVED] need some help with Debian Package Maker"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by gandaran on 2008-10-04
I'm building some .debs packages for simple program files and I'm facing just one problem with the menu application launches, how do I add this information to the package, do I have to make some sort of script? if so how do I do it or is there any other way?
thanks in advance

---

### Post by 3rdalbum on 2008-10-04
It's accomplished through a .desktop file. You can find heaps of examples of these in the "/usr/share/applications" directory; just open one up in a text editor, change the parts that you want changed, and chuck it into your package under /usr/share/applications.

---

### Post by gandaran on 2008-10-04
> **3rdalbum said:**
> It's accomplished through a .desktop file. You can find heaps of examples of these in the "/usr/share/applications" directory; just open one up in a text editor, change the parts that you want changed, and chuck it into your package under /usr/share/applications.

nope, I still don't get it! are you sure about the "/usr/share/applications" examples? they are in fact launches but there is no option for opening them in a text editor.

edit:
okay, success  in opening the .desktop file  using the gedit terminal command 
finally got it working
thanks

---

