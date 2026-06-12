---
title: "Permissions on Xwrapper.config"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Samerious on 2008-11-26
How would I get permissions to edit this file? I need to edit it so i can run programs in a separate xserver

---

### Post by Paqman on 2008-11-26
Alt-F2 (or open a terminal) and enter:

```

gksu gedit /etc/X11/Xwrapper.config

```

(You might want to check i've got that path right, i'm not at a Linux machine right now)

---

