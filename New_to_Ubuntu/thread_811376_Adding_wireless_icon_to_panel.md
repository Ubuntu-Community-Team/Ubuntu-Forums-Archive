---
title: "Adding wireless icon to panel?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by KrisScofield on 2008-05-29
There doesn't seem to be an option for a wireless/internet signal bars on the "Add to panel" list (or I'm missing it). Every time I install Ubuntu it just vanishes after a few logins. :confused:

---

### Post by angry_johnnie on 2008-05-29
try this

System > administration > Sessions > autostarted applications > New

Name:  something (whatever you want)
command:  nm-applet --sm-disable.

Edit:  nm-applet is there by default, and unless you removed it yourself from the list of autostarted applications, then it should still be there.

Maybe what you're missing is the **notification area** in the panel.

---

### Post by KrisScofield on 2008-05-29
The notification area is still there. The bars just aren't there. I tried to go to session, but there was no autostart applications option. I'm on Hardy, if that makes any difference?

---

### Post by angry_johnnie on 2008-05-30
It's not there? :o
This?
[http://i234.photobucket.com/albums/ee205/yogajuan/shot.png](http://i234.photobucket.com/albums/ee205/yogajuan/shot.png)

If it's not there... then I've no clue...

What happens if you press Alt + F2
and then type:

```
nm-applet --sm-disable
```

That should put the applet back in the notification area.

---

### Post by KrisScofield on 2008-05-30
Popped back up after a couple start-ups. Weird. Thanks for the help :)

---

