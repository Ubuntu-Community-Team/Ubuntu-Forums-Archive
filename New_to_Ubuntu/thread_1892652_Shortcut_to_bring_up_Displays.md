---
title: "Shortcut to bring up Displays"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by boblettoj99 on 2011-12-08
Hello there,

I would like to make a desktop shortcut to bring up the displays window (show what monitors are detected etc..) however I don't know what the terminal command is.

I've got as far as creating a 'custom shortcut' in the keyboard preferences, can someone tell me the command I should use?

Thanks

---

### Post by cortman on 2011-12-08
I don't think you can bring up the Displays dialog itself, since it's part of the gnome-control-center application, not a standalone app. Probably the closest you can come is to map a shortcut to bring up gnome-control-center, which will take you within one click of Displays...

---

### Post by Krytarik on 2011-12-08
> **cortman said:**
> I don't think you can bring up the Displays dialog itself, since it's part of the gnome-control-center application, not a standalone app.
Yep, but it can be invoked with this command (just pulled from its .desktop file):
```
gnome-control-center display
```Note: The same is presumably true for most of the other parts of the Control Center (didn't check them all).

If you really want to create a desktop launcher (as opposed to a keyboard shortcut, at which junction you are currently), please see this post:

[http://www.tuxgarage.com/2011/10/creating-desktop-launchers-in-11-10.html](http://www.tuxgarage.com/2011/10/creating-desktop-launchers-in-11-10.html)

Regards.

---

### Post by cortman on 2011-12-08
> **Krytarik said:**
> Yep, but it can be invoked with this command (just pulled from its .desktop file):
```
gnome-control-center display
```Note: The same is presumably true for most of the other parts of the Control Center (didn't check them all).

If you really want to create a desktop launcher (as opposed to a keyboard shortcut, at which junction you are currently), please see this post:

[http://www.tuxgarage.com/2011/10/creating-desktop-launchers-in-11-10.html](http://www.tuxgarage.com/2011/10/creating-desktop-launchers-in-11-10.html)

Regards.

*Bows to Krtarik. Thanks for setting both the OP and myself right on that!

---

