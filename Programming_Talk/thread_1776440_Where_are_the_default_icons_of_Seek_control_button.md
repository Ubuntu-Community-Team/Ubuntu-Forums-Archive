---
title: "Where are the default icons of Seek control buttons located?"
date: 2011-06-06
forum: Programming Talk
---

### Post by leon.vitanos on 2011-06-06
Hi.. I recently changed my theme at ubuntu and i saw that the icons of seek control buttons of movie player and clementine also changed.. So there must be a default path of this icons.. My application also have seek control buttons so i would like to free some space at my app :D

P.s When i mean seek control buttons i mean Play/Stop/Next

---

### Post by Petrolea on 2011-06-06
So what exactly are you trying to do? Find where the icons are stored?

If that's the case they are usually in /usr/share/icons.

---

### Post by leon.vitanos on 2011-06-06
Ok i found it.. I am using Qt Creator and it is QIcon::fromTheme() for this.. 
Thanks anyway ;)

---

