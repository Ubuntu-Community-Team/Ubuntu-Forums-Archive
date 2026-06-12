---
title: "python intra pc client-server - dbus alternative?"
date: 2011-03-27
forum: Programming Talk
---

### Post by giuspen on 2011-03-27
Hi,

I need to estabilish client-server communications on a single pc (no network) and the only option I found so far is to use dbus.

The problem is that python-dbus seems to work bad on wondows so far (my app is cross platform), furthermore I read that python-dbus api continues to change breaking code.

Is there an alternative to this, preferably using the python standard library?

I was considering the use of sockets and loopback 127.0.0.1 but this way I have to use a port risking another app is already using that port.

---

