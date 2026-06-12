---
title: "[SOLVED] Creating a IPYTHON launcher"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Qtips on 2008-08-18
Hi,

I want to create a ipython custom launcher on the Applications/Programming sub-menu...but, i don't know what is the command to call ipython from there...i know that from a gnome-terminal i use >> ipython, but it doesn't work for the launcher. And, at the same time, where can i find a suitable icon for ipython ?

Thanks for the help.

---

### Post by y-lee on 2008-08-18
Just open the Alacarte Menu Editor and click on programming. then click file on the menu and select New Entry.

In the dialog box that opens fill in name and comment and for command put ipython and be sure run in terminal is selected. That is it except for choosing an icon. Finding an icon for ipython is up to you as this would be a matter of personal taste. I might suggest looking thru icons already on your system or using google to find one you like.

---

### Post by ibuclaw on 2008-08-18
Usually a Python/Snake is used as a Icon.

Or you could use Python2.5's one found here.
**/usr/share/pixmaps/python.xpm**

Or you could check out the ipython package and see if they have an icon of their own:
```
dpkg -L ipython | less
```

But it is really just what you want to make of it. You could use a fish for your icon...

Regards
Iain

---

