---
title: "Resolution"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by pepaman on 2008-08-12
Hi
Iv just downloaded ubuntu. Having problems trying to 

A. get nvidia drivers to work.Iv downloaded them from there webpage then when i goto install it props me to choose a program to start it with???

B. when i go to change the resolution the max is only 800x600?
I am using a 9500 gs.

I really just want to know if there is an easy way to get into the control panel on nvidia(like in windows) and change the resolution

Thanks

---

### Post by ajmorris on 2008-08-12
> **pepaman said:**
> Hi
Iv just downloaded ubuntu. Having problems trying to 

A. get nvidia drivers to work.Iv downloaded them from there webpage then when i goto install it props me to choose a program to start it with???

B. when i go to change the resolution the max is only 800x600?
I am using a 9500 gs.

I really just want to know if there is an easy way to get into the control panel on nvidia(like in windows) and change the resolution

Thanks

Hi there,
there is a tool in the menus for changing the gnome resolution, however, this will only allow higher resolutions if it is possible. To set your nvidia driver to be used, and to change the resolution, you might like to press alt+f2, and in the dialog box that appears, enter:
```
gksu displayconfig-gtk
```
you can set 'nvidia' to be used, instead of 'nv' and you can change your resolution, if this does not work, there are many other things we can do to make it work :)

AJ

---

