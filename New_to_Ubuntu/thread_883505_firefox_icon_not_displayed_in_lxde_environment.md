---
title: "firefox icon not displayed in lxde environment"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by imgkg on 2008-08-08
hi guys , i have a weird problem i dont see firefox icon in my panel neither kopete  icon also firefox icon isnt visible in menu of lxde environment ,tell me how to change the icons

---

### Post by sharks on 2008-08-08
just right click the app and select properties. at that window click on the left side of name and type and change the icon

---

### Post by imgkg on 2008-08-08
in lxde environment its different i guess,i went to /usr/share/applications right clicked on firefox application then properties there is nothing like that to change icon just a file name option

---

### Post by thorekk on 2008-11-21
I had the same problem in Ibex with LXDE. I had to edit the firefox.desktop file, and write in the whole route to the icon file.
```
 gksudo mousepad /usr/share/applications/firefox.desktop
```
I changed the Icon=firefox-3.0.png row to Icon=/usr/share/pixmaps/firefox-3.0.png .
Now it does work, but I'm sure there's a better solution.

---

