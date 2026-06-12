---
title: "[SOLVED] Applets failing to load on startup.Please help"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by JMGM123456 on 2008-06-26
I accidentally removed the gnome panel from synaptic(yeah kinda dumb), the problem is that this panel contained applets running(cpu meter,network meter..).Now after i reinstalled it, the applets wouldn't work giving me the error:
The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".
Do you want to delete the applet from your configuration?
If i delete or not nothing happens.But the really annoying thing is that the applets were supposed to run on startup, that means everytime i log in i get like 10 error messages:the panel encountered a problem....

Please help, at least getting rid of the annoying startup issue!

---

### Post by iaculallad on 2008-06-26
Try this:

```
sudo apt-get install --reinstall gnome-applets
```

---

### Post by JMGM123456 on 2008-06-26
Thanks works now :)

---

