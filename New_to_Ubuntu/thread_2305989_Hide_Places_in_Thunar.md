---
title: "Hide Places in Thunar"
date: 2015-12-11
forum: New to Ubuntu
---

### Post by bruno87 on 2015-12-11
Hi Guys,

I have fresh xubuntu instalation and trying to hide some shortcuts on left shortcut pane in Thunar. 
I would to hide "File system", "Network", "Trash" and "Desktop". To be honest i would to leave only User Home folder. 

I know that i can hide this by right click or in setting editor but i can not lock that option that nobody can change that. 

I tried to edit thunar.xml in /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/
and added: 

unlocked="rootlocal"

<property name="hidden-bookmarks" type="array" unlocked="rootlocal"> 

Now i can see in settings editor that hidden-bookmarks is locked but it still can be changed by right click in thunar.

Please help me with that.

Best regards,
Bruno

---

### Post by const2 on 2015-12-11
Sorry, didn't read your question properly first time. Thought You just can't hide them.

---

