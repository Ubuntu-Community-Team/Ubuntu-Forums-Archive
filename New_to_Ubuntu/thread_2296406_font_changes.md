---
title: "font changes"
date: 2015-09-25
forum: New to Ubuntu
---

### Post by trav9595 on 2015-09-25
Anyone running Xubuntu ever have their fonts change mysteriously without doing anything???Would like to hear whats going on??

---

### Post by Toz on 2015-09-26
Is is just the fonts that change or do other graphical changes happen as well? 
It's possible that the xfsetttingsd process is crashing on you. You can verify this by looking at your logfiles: ~/.xsession-errors and/or ~/.cache/upstart/startxfce4.log.

---

