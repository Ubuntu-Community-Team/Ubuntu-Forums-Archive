---
title: "change icon"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by golgo13 on 2008-06-20
still getting used to the linux way of doing things...
If I have an icon called say - applications-internet.png
located at -
/usr/share/icons/Human/24x24/categories
how would I go about changing it for something else?

---

### Post by sayakb on 2008-06-20
Open from terminal:
```
gksudo nautilus
```
And navigate to the directory. Replace the PNG with the one you want to.

---

### Post by golgo13 on 2008-06-20
not really sure how to do that
as I said I'm still getting used to the linux file system
please explain in more detail

---

### Post by aeiah on 2008-06-20
to open a terminal use the menu to navigate to applicatinos > accessories > terminal

and type gksudo nautilus and press enter, and enter your password

---

### Post by aeiah on 2008-06-20
sudo more or less stands for 'super user do'. if you issue this command before another one, it will give you admin privilages to change things that are in your root (important stuff like software, os files etc)

nautilus is the name of the default file manager in ubuntu. a bit like windows explorer. if you launch it with gksudo you can modify things that are in the root, and this includes the icons located at: /usr/share/icons/Human/24x24/categories

if however, you just want to change one icon for one bit of software or one folder, you can right click, go to properties, and change it there. this will only be applied to that instance though obviously.

if you do this and find that your icon is still the same it may be because you've replaced the wrong icon. all icons in 24x24 are 24x24px in size. you may need to change a bigger icon

---

