---
title: "[SOLVED] strange behaviour"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by bob_hilton on 2008-06-20
i just installed codecs etc following the guide at;

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I rebooted following the instructions and now my wallpaper and drives mounted on the desktop have vanished? the drives still automount and show in 'places' though.

any ideas?

---

### Post by sailor2001 on 2008-06-20
[URL="http://ubuntuforums.org/showthread.php?t=798122"] 
is this any help for you?

---

### Post by Dynaflow on 2008-06-20
To restore the wallpaper, go to System -> Preferences -> Appearance -> Background [tab].

---

### Post by bob_hilton on 2008-06-20
no joy.. 

the desktops lost all functionality-

1) no drives are visable, even though there are two hd's and 2x optical drives mounted. 
2) the wallpaper has disappeared, leaving just the default color and
3) the right mouse button gives no context menu?

---

### Post by Dynaflow on 2008-06-20
I can't think of anything in that tutorial that would have resulted in an utterly borked desktop, unless you did something *very* unorthodox when manually editing /etc/gnome/defaults.list.

---

### Post by bob_hilton on 2008-06-20
to be honest i don't have the first idea- ubuntu's my fist attempt at any linux os and i've been using it less than a week.

i have no idea where the problem stems from but that was the last configuration/alteration to the system that i'd made before the problem arose. 

Dynaflow; i just restored the original settings of /etc/gnome/defaults.list. to test but no change.

Anybody have any other idea's?

---

### Post by Dynaflow on 2008-06-20
Have you tried restarting X to see if everything just sorts itself out?  You don't need to restart the computer; just do a [CTRL]+[ALT]+[BACKSPACE] to restart X11 and then log back in.

---

### Post by wormser on 2008-06-20
Maybe we can find out what when wrong by posting your history.  Only post it if you feel comfortable with it.

```
history
```

---

### Post by bob_hilton on 2008-06-20
it worked! :)

i tried rebooting it before i'd posted but to no avail.

Thanks for your efforts Dynaflow.

---

