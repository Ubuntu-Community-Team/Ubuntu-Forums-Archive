---
title: "Making panel items match the theme"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by shatteredmindofbob on 2008-11-03
I posted this in the desktop customization forum but it's since fallen to the third page with no replies, so I thought I'd try here. 

After installing a new theme in Ibex, that new user switcher item retains the gray background of the original panel (see screenshot) How do I fix this?

---

### Post by Sand Lee on 2008-11-03
have you tried restarting X?

---

### Post by mcduck on 2008-11-03
try restarting the panel. "killall gnome-panel" should do the trick..

---

### Post by shatteredmindofbob on 2008-11-03
Nope, restarting X or gnome-panel doesn't do it...

---

### Post by shatteredmindofbob on 2008-11-03
Any other ideas?

---

### Post by mcduck on 2008-11-04
If reloading the panel doesn't work it could simply be a bug in the theme you are using, perhaps it defines a background picture for panel itself, but not for panel applets or even a suitable color for the applets..

You could try using another theme, or defining the panel background image manualy from the panel's configuration (which is much better than those panels included in themes, anyway, as this way it's possible to enable rotation and scaling of panel backgrounds in gconf-editor while theme-defined backgrounds only really work with horizontal panels of certain size)

---

