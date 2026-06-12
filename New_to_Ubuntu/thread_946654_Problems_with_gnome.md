---
title: "Problems with gnome"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by collinge on 2008-10-13
... i did something wrong... i think i installed a bad theme file... i clicked on it after i installed it and the my computer froze... now when i login i see a black screen with a white terminal... no menus or anything. 
I have tried to use the following commands with no luck:
mv ~/.gnome2 ~/.gnome2.old
and
gconftool-2 - -recursive-unset /apps/panel 


nothing....how can i reset gnome or whatever i did... HELP!!

---

### Post by Ryadt on 2008-10-13
Try ```
sudo apt-get install ubuntu-desktop
```

---

### Post by kerry_s on 2008-10-13
in fail safe mode you can use "gconf-editor" to unset the theme.

---

### Post by collinge on 2008-10-13
that did nothing so i tried get upgrade and after it installed....still nothing. i created a new user account... it works fine..but i would still like to fix the other account

---

### Post by kerry_s on 2008-10-13
> **collinge said:**
> that did nothing so i tried get upgrade and after it installed....still nothing. i created a new user account... it works fine..but i would still like to fix the other account

did you unset all the themes?
what theme is it, so i don't make the same mistake? :lolflag:

---

