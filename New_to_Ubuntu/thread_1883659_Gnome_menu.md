---
title: "Gnome menu?"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by n5050 on 2011-11-19
Is it possible to add a little delay when navigating from one menu to another because sometimes when trying to move the mouse down the horizontal menu changes (when moving down diagonally)?

---

### Post by ajgreeny on 2011-11-19
As you are asking about the gnome menu I assume you are using something with the classic desktop and not unity or gnome 3.

In my 10.04 setup I have a hidden file in my home called **.gtkrc-2.0** which has the contents ```
gtk-menu-popup-delay=0
```in my case to stop any delay;  perhaps you can use something similar but with a different integer to slow yours and allow you to navigate more easily.  I do not know if the "0" in my file relates to milliseconds, seconds or something else, nor if this will allow you to get what you want, but it must be worth a try.

---

