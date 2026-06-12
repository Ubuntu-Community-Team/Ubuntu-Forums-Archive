---
title: "Gnome DnD Makes it Hard to see where you're dropping"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by mattismyname on 2008-08-10
I've had this issue ever since the first releases of Gnome oh so many years ago.  Basically the issue is that when I drag an icon, it is very hard to see precisely where it is going to be dropped.  The reason is that the cursor is drawn on top of the icon and the icon is at 100% opacity.

In Windows and Mac OS this is not an issue because the icon is set to partial opacity which enables me to see where the cursor is relative to whatever is under the icon.

Anybody else had this issue?  Any known solutions?

thanks!

---

### Post by gjoellee on 2008-08-10
I am not having any issues

---

### Post by jordanmthomas on 2008-08-10
This hasn't ever been an issue for me because I look where I am going to drop it before I move my mouse there.

Also, my icons turn transparent when I drag them (perhaps the doing of compiz)

---

### Post by mattismyname on 2008-08-10
@jordanmthomas  --  Wow!  I wish my icons do that but they don't.  Maybe it is the doing of compiz...I am not running compiz (due to Nvidia driver issues...different story).

Anybody know if it is compiz that makes the icons transparent like that?  It would be so useful.

---

### Post by jordanmthomas on 2008-08-10
It turns out it was compiz doing it.
However, if you allow metacity to act as a composite manager, it works as well.
You can enable this by typing
```

gconftool-2 --set /apps/metacity/general/compositing_manager --type bool true

```
or by running gconf-editor and finding your way to the key

To be honest though, I don't think metacity does as good a job as compiz as far as speed goes, but it may be worth a shot.

---

### Post by mattismyname on 2008-08-10
Sweet!  It works!

Did not know metacity could do compositing.

---

