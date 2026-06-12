---
title: "[SOLVED] How to configure gdm?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by bhadotia on 2008-05-14
I wanted to try kde4 , so I installed it. When the kde configuration dialog poped up I selected kdm as the default display manager . Now when I log into gnome desktop enviornment  I am unable to use some of the options in the system>preferences . 
The following dialog pops up:

**GDM (GNOME Display Manager) is not running.**
You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. If you wish to use this feature, then your system will need to be configured to use GDM instead.


So how can I use GDM again?

Thank you very much in advance.

---

### Post by kellemes on 2008-05-14
From terminal..
```
sudo dpkg-reconfigure gdm
```

---

### Post by bhadotia on 2008-05-14
Thanks.


Is there a way in which we can configure these gdm and kdm to start automatically when I log into gnome or kde?

---

