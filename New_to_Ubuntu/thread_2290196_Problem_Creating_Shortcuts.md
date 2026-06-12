---
title: "Problem Creating Shortcuts"
date: 2015-08-10
forum: New to Ubuntu
---

### Post by h8chanz on 2015-08-10
I cannot drag a shortcut to my desktop. Even when I run sudo nautilus and create the shortcut that way, wheh I try to cut and paste the link to the desktop I still get an error message saying "Permission Denied". How do I do this?

---

### Post by howefield on 2015-08-10
Hello and welcome to the forums, not a drag and drop but you could try navigating to /usr/share/applications/*.desktop and right clicking on the icon for the application you want, select "Copy to" and choose the desktop.

---

### Post by h8chanz on 2015-08-10
I'm trying to create a shortcut for a subfolder.

---

### Post by yancek on 2015-08-10
This works for me with a standard Ubuntu install, first install:

sudo apt-get install --no-install-recommends gnome-panel

Then do:  gnome-desktop-item-edit ~/Desktop/ --create-new

You get a pop-up window and if you want a link to a directory, select Location from the Type drop-down and in the box below enter the path.

---

### Post by h8chanz on 2015-08-10
thx, but I found a different way afterwords:

sudo ln -s /path/of/folder /path/of/shortcut/shortcut_name

---

