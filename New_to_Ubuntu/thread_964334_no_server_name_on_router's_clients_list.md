---
title: "no server name on router's clients list"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by mac-i-bear on 2008-10-30
ubuntu server 8.04.1
why would the server's name not shown on the router's clients list - the desktop name does

the router shows "unknown" on the ip address assigned to the server

have check the file "hosts" and it has the right name
so does "hostname"

---

### Post by aeiah on 2008-10-30
i think the reason is because the desktop package has avahi-daemon, which you wont have by default in ubuntu server.

---

### Post by mac-i-bear on 2008-10-31
would you be kind enough to walk me through on how to install that and getting to do what it needs to do - thanks a lot

---

### Post by mac-i-bear on 2008-10-31
> **aeiah said:**
> i think the reason is because the desktop package has avahi-daemon, which you wont have by default in ubuntu server.

sorry, i meant to include your text ....

---

