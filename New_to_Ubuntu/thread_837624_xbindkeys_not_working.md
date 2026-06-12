---
title: "xbindkeys not working"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by doctor bangali on 2008-06-22
I can't get xbindkeys to work.
I have an empty xbindkeysrc.scm file and my .xbindkeysrc contains these lines:

# Run Kile
"kile"
   Alt+k

---

### Post by erginemr on 2008-07-10
The shortcut you have described works in my computer. You should make sure that xbindkeys is working in the background: Alt+F2 >> xbindkeys

To make this permanent, you need to include xbindkeys to the session autostart with:
Menu >> System >> Preferences >> Sessions >> Add new entry with the commnad "xbindkeys"

---

