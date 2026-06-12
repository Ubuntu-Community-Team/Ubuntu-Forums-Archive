---
title: "Hardy install - older laptop - No desktop!"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by diaz028 on 2008-06-01
I just put in the live CD to try Ubuntu on my machine.... Arrow is present, i can move the mouse around, but the desktop is empty, nothing to click on. 

Ctrl+Alt + F1 gives me a command line...

Bad drivers??

-D

---

### Post by tamoneya on 2008-06-01
what do you mean by the desktop is empty.  Can we get a picture.  Also try to get gnome panel running by hitting alt-F2 and then typing:```
gnome-panel
```

---

### Post by diaz028 on 2008-06-01
Cant get a screenshot...

Screen has the standard beige wallpaper, but there are no panels. Just the pointer, and I can move the pointer. No desktop icons nothing.

-D

---

### Post by phidia on 2008-06-01
Does your laptop meet the [system requirements]("https://help.ubuntu.com/community/Installation") for 8.10? If you know what your gpu is you can try to set it up yourself type > sudo dpkg-reconfigure xserver-xorg in the commandline you've opened and fill in your parameters when asked by that set up program. Hope that's helpful.

I should have asked, too, did you check the md5sum of the iso you downloaded or verify the cd through the menu item for that?

---

