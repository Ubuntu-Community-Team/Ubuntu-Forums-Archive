---
title: "Lost Splash Screen"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-06-14
Ok, so I had a problem with gnome and had to delete the /.gconf file. I knew I would lose all of my config but I can't retrieve the splash screen. I used the splash manager before and now it starts but can't do nothing but close it back again. How do I get it back? I have no splash screen, only the orange wallpaper until it completes the login. Please, help...

---

### Post by y-lee on 2008-06-16
Hmmm

Try opening the configuration editor.

```
gconf-editor
```

In the configuration editor navigate to **apps | gnome-session | options** and in the right box: do you have a **splash_image** key? If so change its value to **splash/ubuntu-splash.png**. If its value is already that or you have no splash_image key post back please and tell us.

Hopefully this will work :)

---

