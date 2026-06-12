---
title: "how to show desktop?.."
date: 2008-04-30
forum: Philippine Team
---

### Post by killer_d76 on 2008-04-30
guys need help here!.. i lost my desktop background and icons after messing with nautilus> desktop> preferrences!, i accidentally removed the tick on show desktop and boom!.. no more icons and wallpaper!

---

### Post by gbutalid on 2008-04-30
> **killer_d76 said:**
> guys need help here!.. i lost my desktop background and icons after messing with nautilus> desktop> preferrences!, i accidentally removed the tick on show desktop and boom!.. no more icons and wallpaper!

(1) Alt+F2
(2) Write down gconf-editor, RUN
(3) Choose Apps > Nautilus > Preferences
(4) Tick "Show Desktop"

Let me know what happens.

---

### Post by killer_d76 on 2008-04-30
i tried that earlier but  i found out that it's one of the bugs of hardy that you cannot change it back?.. kaya ayun reformat and re-install.. okey na ulit!.. :guitar:

---

### Post by SHENGTON on 2008-04-30
Same problem here and it seem I can't right-click anymore.

---

### Post by killer_d76 on 2008-04-30
yes that's exactly what happened to my desktop!.. you won't be able to view your desktop!.. i did a quick research about it, and found out that it is one of the bugs that's not yet fixed :(

---

### Post by SHENGTON on 2008-04-30
It seems that the problem of Ubuntu. Once you uncheck the box it seems you can't return it anymore.

---

### Post by gbutalid on 2008-04-30
Buti di ko siya nauncheck kanina sa gconf. :)

---

### Post by Rinzwind on 2008-04-30
> **gbutalid said:**
> (1) Alt+F2
(2) Write down gconf-editor, RUN
(3) Choose Apps > Nautilus > Preferences
(4) Tick "Show Desktop"

Let me know what happens.

No! You need to do a 
sudo gconf-editor
from terminal.

:)

It is also possible to change it from command line but I am too much of a rooky to give you advice on that :)

---

### Post by killer_d76 on 2008-04-30
tried it and i ended up in the same configuration!.. i just deleted hardy and re-install it! ;), but unfortunately i lost grub and now i can't boot back to windows xp!.. good thing my wife is in the good mood :p

---

### Post by SHENGTON on 2008-05-01
Hello guys! Just want to share after troubleshooting this problem.

I tried to check the box of "Show Desktop" in gconf-editor and restarted my computer. After that, everything is back to normal. Just like "regeditor" in Windows after changing some settings you have to restart before it takes effect.

Hope this help!

---

### Post by killer_d76 on 2008-05-01
dang!.. i wish i should have just restarted my computer, rather done going thru this whole process again! :D

---

### Post by killer_d76 on 2008-05-16
ok.. am very happy with Hardy.. i was able to get the 3D cube working and now i was able to install Dock on it!... check this out...

[IMG]http://i254.photobucket.com/albums/hh110/arvin_domingo/Screenshot2.png[/IMG]

---

