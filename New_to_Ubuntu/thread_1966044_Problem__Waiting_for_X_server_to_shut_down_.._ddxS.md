---
title: "Problem : Waiting for X server to shut down .. ddxSigGiveUp: Closing log"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by IRhQ on 2012-04-26
When i Type the Startx command in BT5 ...
i see This : Waiting for X server to shut down .. ddxSigGiveUp: Closing log

Can i SLove thish problem with out Formating and Re-installing the BT5 ?!
( I use BT5 GNOME)

---

### Post by IRhQ on 2012-04-27
Please Help Friends :( ,,,

---

### Post by IRhQ on 2012-04-27
any one ?!

---

### Post by dniMretsaM on 2012-04-27
Apparently, you can't run just X for some reason (I had a similar problem). You have to run it with something like a display manager or window manager.

I.E. if your display manager is GDM you would run:
```
sudo service gdm start
```You would then proceed to log in.

Also, please don't bump your post more than once every 24 hours.

---

### Post by IRhQ on 2012-04-27
tnx my friend for help...

---

### Post by IRhQ on 2012-04-29
i have try it .. but it dosetn work :( ..the same problem is back to me !

---

