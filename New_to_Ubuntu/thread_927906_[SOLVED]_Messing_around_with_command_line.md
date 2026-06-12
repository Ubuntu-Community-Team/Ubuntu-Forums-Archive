---
title: "[SOLVED] Messing around with command line"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Eto_Demerzel on 2008-09-23
I was trying to change colors/appearance using command line. For example, I found that editing the ./.gconf/desktop/gnome/background/%gconf.xml file would change desktop background color on next reboot/logout and login.

Similarly, editing the ~/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml file could change terminal appearance. But again, only after logout and login or reboot.

How do I change appearance on the fly, i.e., without having to reboot for the change in settings to take place? (Using command line, I mean)

Thanks.

---

### Post by Yannick Le Saint kyncani on 2008-09-23
Hi Eto_Demerzel, I could be mistaken because I'm not using gnome any more, but some time ago, changes to the gconf database had effects in real-time.

You just had to use gconftool, now gconftool-2, instead of changing the configuration files.

I hope it still works :)

---

### Post by terry_gardener on 2008-09-23
you can also change the colour of the terminal using the menu in the terminal windows. 

click edit-current provide and select the colour tab and have fun.

---

### Post by Eto_Demerzel on 2008-09-23
Thanks a lot, Yannick. gconftool-2 was exactly what I was looking for. It still works :)

For example:

```
gconftool-2 -s /apps/gnome-terminal/profiles/Default/background_color -t string "#110022"
```

And Ta-daa!!

---

### Post by Yannick Le Saint kyncani on 2008-09-23
> **Eto_Demerzel said:**
> And Ta-daa!!

Well, glad it works.

/me thinks someone is about to play with the gconf database a lot and have some fun :popcorn:

---

### Post by Eto_Demerzel on 2008-09-23
You bet! 

:guitar:

---

