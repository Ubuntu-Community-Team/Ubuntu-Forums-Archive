---
title: "purge gnome classic"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by jaramarana on 2013-01-04
Hi,

I installed gnome-shell in 12.10 to see if I liked it better than unity, and I didn't, so I purged it. This didn't deal with 'gnome classic' and 'gnome classic (no effects)', however, which remain on my login window.

How do I remove them without also removing delicate parts of my system?

Thanks.

---

### Post by Frogs Hair on 2013-01-04
```
sudo apt-get remove gnome-session-fallback
```

You can use the purge command for the package as well.

---

### Post by audiomick on 2013-01-04
Why not leave that there, though? It is not costing you anything but a little bit of disk space, and it might, for instance, still work if your Unity should develope problems...

---

### Post by HernanLinux93 on 2013-01-04
Audiomick is right I had some trouble with Unity...and had to revert back , but now I got it all working again.

---

### Post by Frogs Hair on 2013-01-04
I like to use alacarte and the main menu and the gnome panel is a dependency. I use the Gnome Shell so I have to keep the fallback-session installed but the main menu is nice tool for creating launches and would want it installed even if I was a Unity only user.

---

### Post by Rocklobster690 on 2013-01-06
Or try LXDE or XFCE sessions.

---

