---
title: "Problem with desktop"
date: 2018-11-26
forum: New to Ubuntu
---

### Post by 4ng3l2 on 2018-11-26
Hi,

I have installed Ubuntu in my pc (I come from Windows). In first time, i selected install on spanish languague (I from spain). But, to follow tutorials and documentation, i think that is better have english languague. After to select english languague, when i try to create some element in my desktop, i have the following error:



How i can fix it?

Thank you very much!!!

Regards,
Ángel.

---

### Post by mastablasta on 2018-11-27
show us more details (click the arrow next to "show more details") and attach the picture to your post using attach tool. or if you can, just copy the text. However, it look slike the directory doesn't exist. not really an error.

command line in linux is used in tutorial and when giving help, because it doesn't matter which language you installed the OS in or what interface (gnome, KDE, XFCE...) you use - it will always be the same.

---

### Post by Impavidus on 2018-11-27
Most tutorials and documentation is in english, but it shouldn't be too hard to follow those on a spanish system.

There's a number of directories that get created automatically when a new user is created, with named like Documents, Downloads, Pictures. These directories get their name translated to whatever language your system uses. In your case, there's a mismatch between the directories existing and those expected by the desktop manager. You can fix it in two ways. Either change the names of the directories to match the expectation or change the configuration file ~/.config/user-dirs.dirs to tell the desktop manager the correct names of these directories.```
gedit ~/.config/user-dirs.dirs
```

---

