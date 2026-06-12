---
title: "Icons on desktop"
date: 2015-10-18
forum: New to Ubuntu
---

### Post by Hakan__Venderlof on 2015-10-18
Hello
Is it possible to make icons on destop in ubuntu 15.4 like on windows desktop?

---

### Post by shadytv on 2015-10-18
Look in /usr/share/applications there are *.desktop config files in there that specify info about your icons. You can find default icons in /usr/share/icons.

---

### Post by slickymaster on 2015-10-18
[LIST=1]
[*]Open Nautilus
[*]Navigate to **/usr/share/applications**
[*]Right-click on the application you want to use and select copy
[*]Click on your desktop and select paste
[*]Right click on the icon that has just been created and select properties
[*]On the Permissions tab check Execute then click Close
[/LIST]

---

### Post by Hakan__Venderlof on 2015-10-18
Tx :-)

---

### Post by mc4man on 2015-10-18
> **slickymaster said:**
> [LIST=1]
[*]Right click on the icon that has just been created and select properties
[*]On the Permissions tab check Execute then click Close
[/LIST]
Experience here is .desktop files copied from /usr/share/applications don't need to have permissions reset when copied to the Desktop 
(Though do almost anywhere else copied to.
If a copied .desktop shows up as an icon then it's executable.

---

