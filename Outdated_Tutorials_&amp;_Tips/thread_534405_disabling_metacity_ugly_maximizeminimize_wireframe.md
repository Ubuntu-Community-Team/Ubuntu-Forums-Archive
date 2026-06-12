---
title: "disabling metacity ugly maximize/minimize wireframes"
date: 2007-08-25
forum: Outdated Tutorials &amp; Tips
---

### Post by inoxllor on 2007-08-25
**Tested on Ubuntu 7.04 Feisty Fawn.**

Metacity has some ugly maximize/minimize wireframe borders that look very bad on the GNOME animation scheme (specially if we are using COMPIZ-FUSION).

But, do not fear. :D 
There is a way to change this:

1) run **gconf-editor** in terminal 
*(for windows users is an app similar in some aspects to regedit)*

2) navigate to **/apps/panel/global**

3) **uncheck "enable_animations"**

Use CTRL-ALT-BACKSPACE to restart GDM. 
Alternatively you may simply use ALT-F2 and run **metacity --replace**, or (if you use compiz) **compiz --replace** to update the gui. 

PS: if you don't have gconf-editor use apt-get or synaptics to install it.

---

### Post by coldReactive on 2009-10-06
And if that doesn't work,

apps/metacity/general

and make sure reduced_resources is checked. You don't have to restart GDM though in newer versions.

---

### Post by schmolch on 2009-10-06
Disabling the panel animations does not disable metacity's animations and "reduced resources" gives you a ugly and buggy wireframe when you move windows.

Metacity is just the dumbest, slowest and most retarded WM ever written.

---

### Post by -VladV- on 2010-07-10
From here: [http://ubuntuforums.org/showthread.php?t=175976](http://ubuntuforums.org/showthread.php?t=175976)

Well, now you've gotten rid of the lines when you minimize windows. New problem? You get this wire basket thing when you try to move Windows.

So, step two: System > Preferences > Assistive Technology Support.
Enable it.

---

### Post by schmolch on 2010-07-11
Thank you!

I think im gonna file a bugreport about this, i have never seen anything more unintuitive.

---

### Post by bubuzzz on 2010-09-10
it works well except the stupid wireframe (even in the panel) still appear when i switch the window (alt+tab). How to get rid of it ?

---

### Post by sp8bql on 2011-04-05
If the frames still appear, try running in terminal command:

sudo metacity --replace

---

### Post by sp8bql on 2011-04-23
gconftool-2 --type bool --set /apps/metacity/general/reduced_resources true

executing this command in terminal also disables the wireframes

---

