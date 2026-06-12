---
title: "[SOLVED] Unable to download packages?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by ghostier on 2008-06-08
When I tried to install some new software from the add/remove applications. It starts downloading and says 
```

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xsane/xsane_0.995-1ubuntu1_i386.deb
  404 Not Found
```

I'm think its a connection problem but i can connect to internet fine.

---

### Post by ibuclaw on 2008-06-08
It appears that the ubuntu repository has been taken down.

To connect to another one, change the "**Download from:**" server settings in Synaptic to another nearby server. 
It's under "**Settings>Repositories**" in the synaptic menu.

Regards
Iain

---

### Post by ghostier on 2008-06-08
Sorry, i'm new to this... I dont know what Synaptic is or where to find it..

---

### Post by drs305 on 2008-06-08
Synaptic is the ubuntu application installer. Click on System, Administration, Synaptic Package Manager. On the first tab, follow the directions tinivole gave you.

---

### Post by ghostier on 2008-06-08
...I fixed this problem by switching the servers using software sources from preferences.

---

