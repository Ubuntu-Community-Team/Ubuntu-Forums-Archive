---
title: "Changing icon for Places menu..."
date: 2008-08-01
forum: New to Ubuntu
---

### Post by mudrain911 on 2008-08-01
Just a quick question... How would you go about changing the icon displayed for the Places menu in the Panel of Xubuntu? I've searched but have found nothing. Is there a config file for this or am I just missing something extremely simple :)

---

### Post by iaculallad on 2008-08-01
I don't know if this could work (I'm in Ubuntu), try editing the menu file:

```
cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml
mousepad ~/.config/xfce4/desktop/menu.xml
```

---

### Post by mudrain911 on 2008-08-01
Ok I'll go try that... I'll let you know if it works thanks!

EDIT: I'm pretty sure that is for the Applications menu. I wish the Places menu worked like that one because there is a setting in properties to change the icon for Applications.

---

### Post by BGFG on 2008-08-01
Hey i don't know if you have some specific custom icons you created but here's a good place to get lots of icon packages. Fiddling around with my theme has become my new thing.

[http://art.gnome.org/](http://art.gnome.org/)

---

### Post by mudrain911 on 2008-08-01
I know what icon I want for it, I just have no idea how to change the one that is already there. Does anyone know of a config file for me to do it?

---

### Post by mudrain911 on 2008-08-02
Well, I just found out how to change the icon for it in 'Add New Items', but the icon in the actual panel stayed the same. I don't know anything about programming, so if there is a line for me to add to this file let me know.

(/usr/share/xfce4/panel-plugins/places.desktop)

---

