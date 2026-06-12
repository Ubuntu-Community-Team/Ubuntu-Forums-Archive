---
title: "How do I disable hotplug?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by titus on 2008-06-28
Hi, I'm planning to use a custom kernel and load modules manually as required.

I would like to disable hotplug and any other hardware autodetection mechanisms. How can I do this?  

Can someone link to any recommended reading about how ubuntu boots?

---

### Post by sdennie on 2008-06-28
This is probably not going to go as well as you are hoping but, you will probably be able to do that by preventing udev and possibly hal and dbus from running.  That may render much of your system unusable if you plan to use gnome.  This guide seems to have good information on runlevels (which is what you'd need to use to prevent those services from starting): [http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

---

