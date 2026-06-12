---
title: "how to set the gnome terminal as default in lubuntu"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-03-01
any ideas been searching on google but dto no avail.tks

---

### Post by vasa1 on 2013-03-01
> **rburkartjo said:**
> any ideas been searching on google but dto no avail.tks

This is probably a workaround rather than an answer, but you could edit the "Exec=" line in *lxterminal.desktop* file in */usr/share/applications* or, preferably, the one in *~/.local/share/applications* to point to *gnome-terminal* instead of to *lxterminal*.
Then, in *~/.config/openbox/lubuntu-rc.xml*, you could edit the current key combination for *lxterminal* to point to *gnome-terminal*.

BTW, why do you prefer gnome-terminal in Lubuntu? In what specific way is lxterminal inadequate?

---

### Post by rburkartjo on 2013-03-02
va tks i ended up just keeping the lxterminal as default when i use lubuntu.

---

