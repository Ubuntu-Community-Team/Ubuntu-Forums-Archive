---
title: "[SOLVED] task bar gone"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by stonerrob420 on 2008-09-23
My task bar at the bottom of my screen the one used to access everything is gone. How can I pull up the system settings with the konsole to be able to adjust it back to regular size and unhide it? Oh by the way I am using kubuntu hardy.:confused::lolflag:

---

### Post by digitalvectorz on 2008-09-23
Gnome or KDE?

if it's KDE, i'm not sure.

For gnome, try this:

Press ALT+f2 (brings up 'Run Application')

type:
```
killall gnome-panel
```

That should kill it (if it's running) and restart it.

If that doesn't work, let me know.

---

### Post by Elfy on 2008-09-23
Had a dig on the kubuntu forum - to get the control centre up

Alt+F2 - run kcontrol to get the settings, think its Desktop > Panels

@digitalvectorz - it's likely to be kde as it's kubuntu

---

### Post by stonerrob420 on 2008-09-23
I figured out how to do it. it's Alt+F2 brings up run then type kcontrol. Panels could be adjusted from there. So you both where right. Just took a little mixture of your help. thanks :)

---

### Post by jemate18 on 2008-09-23
please mark this THREAD as SOLVED

---

