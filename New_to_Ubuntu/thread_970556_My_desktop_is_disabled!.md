---
title: "My desktop is disabled!"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by George7a on 2008-11-04
Hi,

I had the problem that is described in this thread:
[http://ubuntuforums.org/showthread.php?p=6101746#post6101746](http://ubuntuforums.org/showthread.php?p=6101746#post6101746)

After I tried to fix it, the desktop is now disabled! No shortcuts, no mouse left click and no mouse right click. 

Can anyone help please?

- George

---

### Post by drs305 on 2008-11-04
If the desktop has symptoms like there is a plate of glass over it (you cannot do anything to or on it), the 'show desktop' setting may be inactive.
You may be able to restore it by running this command:
```

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'

```

For me, refreshing the desktop sometimes didn't make the change 'take', so I had to log off and back on for the desktop to show again.

---

### Post by George7a on 2008-11-05
I have tried that but it did not work! any other suggestions?

---

### Post by George7a on 2008-11-05
This thread helped me:
[http://ubuntuforums.org/showthread.php?t=543127&amp;highlight=items+desktop](http://ubuntuforums.org/showthread.php?t=543127&amp;highlight=items+desktop)

I installed gtweakui, uncheck & checked "Use nautilus to draw desktop" and it worked.

---

### Post by drs305 on 2008-11-05
> **George7a said:**
> 

I installed gtweakui, uncheck & checked "Use nautilus to draw desktop" and it worked.

This is interesting. I've been using the gconftool command to show and hide the desktop for years - I have a shortcut on my panel. With intrepid it's been a bit hit or miss - sometimes the command works, sometimes it doesn't. I figured it was a bug created by something with my compiz or wallpaper setup.

I installed gtweakgui, which I am guessing uses the same commands to display/hide the desktop since it is a front end for gconf. Anyway, ever since I installed gtweakui my shortcut commands have been running reliably - without using gtweakui ...

---

