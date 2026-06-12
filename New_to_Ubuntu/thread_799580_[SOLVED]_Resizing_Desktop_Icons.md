---
title: "[SOLVED] Resizing Desktop Icons"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by drsox1899 on 2008-05-19
I must be missing something in the basic Ubuntu documentation, but I can't find a way to resize the desktop icons.

As a convert from WinXp, I'm looking to be able to pack lots of desktop icons on my screen(s), but can't find the way to do it.

Yes, I can make the icons smaller, but can't change the spacing.  
What I want are smaller icons - closely spaced.

Downloading new icon themes doesn't seem to answer the problem.

Where should I be looking ?

---

### Post by N.N. on 2008-05-19
Open the file manager and go to "Edit" > "Preferences". Then, under "icon view", set the default zoom layout to 25%.

You can achieve the same thing by issuing the following command from a terminal: ```
gconftool --type string --set /apps/nautilus/icon_view/default_zoom_level "smallest"
```

---

