---
title: "compton(v13.04) switched off autostart"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by saltcushy on 2013-04-28
[http://lubuntublog.blogspot.com/p/compton.html](http://lubuntublog.blogspot.com/p/compton.html)

My file:
```
@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@xfce4-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1

@compton -c -r 16 -l -24 -t -12 -G -b
```
Log:
```
** (leafpad:2589): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,
borders don't fit within the image

** (leafpad:2589): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,
borders don't fit within the image

** (leafpad:2589): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical-sel.png,
borders don't fit within the image

```
   Works manually it in the terminal without "@"  compton -c -r 16 -l -24 -t -12 -G -b but no autostart.
 Under 12.10 works fine but under 13.04  sth is up.

---

### Post by saltcushy on 2013-04-28
Solved, I added a file to /etc/xdg/autostart :)

---

### Post by sitof on 2013-05-13
Can you please be more specific? What kind of file did you add?

---

