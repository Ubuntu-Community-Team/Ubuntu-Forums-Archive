---
title: "KDE 4: Access denied to /usr/share/applications/Deluge.desktop."
date: 2008-08-10
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-08-10
I'm trying to change the name and icon of a desktop icon on KDE 4, I can do it with all the other icons but if I try and change the icon or name of deluge I will get an error box pop up and tell me that Access was denied...

```
Access denied to /usr/share/applications/Deluge.desktop.
```

is this a bug?

PS: Is the KDE team intending to sort out the default Firefox look in the new KDE? as it looks like someone battered it with an ugly stick:mad:

---

### Post by jordanmthomas on 2008-08-10
It doesn't seem like a bug to me.  Probably, your best bet would be to make your own launcher instead of trying to edit the one in /usr.  

As for the look of firefox, it looks bad probably because you have no gtk theme defined for it to use and no gnome-settings-daemon running for it to find.  Try installing gtk-chtheme, lxappearance or switch2 to choose a gtk theme so firefox won't look bad.

---

