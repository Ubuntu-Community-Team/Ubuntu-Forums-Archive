---
title: "window manager problem"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by spencer218 on 2008-06-25
After installing compiz and deciding not to use it untill I upgrade my memory , I took the command out of the autostart menu and now my windows are all messed up with no close or minimize functions in the upper right corner anymore. Went to applications and settings and when clicking the window manager tabs it says it cant open, unknown window manager. I thought it wouldnt be difficult to change back. Can anybody tell me how to get the xubuntu default window manager back ?  thanks

---

### Post by Canis familiaris on 2008-06-25
Press Alt+F2

type:
```
metacity --replace
```

EDIT: Oh! You use Xfce. I thought you use GNOME.

For Xfce I think but not completely sure:

```
xfwm --replace
```

---

### Post by vambo on 2008-06-25
<Alt> <F2> ti bring up "Run Program"
Then:
```
xfwm4
```

Should bring xfce back

---

### Post by spencer218 on 2008-06-26
Thanks yall , it worked,...but that had to be done every time I boot up for some reason. Seems like xfwm4 was lost when shutdown. I went into applications > settings > settings manager >autoloading programs and added it but I cant remember if it was there before I tried compiz. Did I just do a patchwork rig that could haunt me later ?

---

### Post by pharaujo on 2008-08-13
I have a similar problem: since I ran "sudo nautilus" to browse as root some directories, everytime I start xfce I have to set "Allow Xfce to manage the desktop" in *Applications > Settings > Settings Manager > Desktop*. I guess nautilus set metacity as my default wm, but I can't find a way to change this..

---

### Post by pharaujo on 2008-08-16
I found out that nautilus was automatically starting. I killed nautilus, then logged off then back again, and it worked..

---

