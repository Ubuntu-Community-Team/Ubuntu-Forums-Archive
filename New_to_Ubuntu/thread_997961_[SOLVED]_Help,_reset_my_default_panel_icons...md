---
title: "[SOLVED] Help, reset my default panel icons.."
date: 2008-11-30
forum: New to Ubuntu
---

### Post by trooperchix on 2008-11-30
I don't know how I did it, I was fooling around, and I totally muffed up the panel icons in the upper right hand corner.  I was able to get into the "add to panel" area, but none of the default working icons are there.  For example, upper right hand, how the power down button works and appears in Intrepid?  Gone.  No actual "working" icons, just a bunch of launch icons that just sit there.  Another example.  When one starts Amarok or Limewire, I get the little dog head  or lime looking thing to show in the upper right hand corner letting me know it is running.  Now, I just launch either, and no working icon appears.  If I closed the working windows, those little icons would pull up the working window again (they don't stay on the lower panel).  I just want to get the upper right hand icons reset, hopefully that will make my ubuntu world a bit better.  

Thanks.
Trooperchix.

---

### Post by drs305 on 2008-11-30
You can move or rename (safer than deleting) the /home/*username*/.gconf/apps/panel folder. Then restart. When ubuntu doesn't find the 'panels' folder, it will create a new one and you will have the default panel with only the minimal/default items on it.
```

mv $HOME/.gconf/apps/panel $HOME/Desktop/old-panel
sudo /etc/init.d/dbus restart

```

---

### Post by trooperchix on 2008-11-30
Dood, you rock.  Totally worked. Thanks!

---

