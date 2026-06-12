---
title: "i got this error with panel twice today at startup"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by neil_1 on 2011-10-31
i got this error with panel twice today at startup
what should i do?
see screenshot

---

### Post by Calerid on 2011-10-31
I got an error like this recently. I had to reset the gnome panels to get it to work. There was another solution that I forget. Maybe someone will post it. 
> gconftool-2 --recursive-unset /apps/panel 
killall gnome-panel

---

