---
title: "network-manager connections migration"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dameat on 2011-09-02
I just updated to 11.10 beta, and it seems that network-manager forgot about all my saved network connections. I can still see them in gconf-editor (system/networking/connections) but it looks as though the new network-manager 0.9 wants them installed in /etc/NetworkManager/system-connections/ . I'm assuming that something just messed up on my upgrade and some script that was supposed to migrate those settings didn't run - is anyone else seeing this issue? And does anyone know how to fix it? If it doesn't just affect me, I'll file a bug.

---

### Post by David D. on 2011-09-04
I had the same thing happen when I upgraded from 11.04 to 11.10.  Network Manager would see the networks available, but would ask for the key.  After the key was entered I would connect for a few seconds, then be disconnected.  Once I edited the connection I wanted and re-entered the connection information, I was able to maintain the connection.

---

