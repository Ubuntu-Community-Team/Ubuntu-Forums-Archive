---
title: "error: untrusted X11 forwarding"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by ubun_tut on 2013-01-15
hi,

i am accessing my lab server, which is running Ubuntu 12.10, from my macbook pro. it was running ok, until i think i accidentally deleted some files while i was clearing out my home folder. since then, whenever i access the server, i have this error message:

[HTML]
warning: untrusted X11 forwarding setup failed: xauth key data not generated
warning: no xauth data; using fake authentication data for X11 forwarding
[/HTML]

i have read online somewhere that this is not a serious problem as it simply affects the display (the X server?) is that right?

if it is serious enough that i should correct it, can anyone tell me how to go about doing that? i have no root access.

thanks.

---

### Post by ubun_tut on 2013-01-16
Hi, anyone at all??

---

### Post by ubudog on 2013-01-16
Are you using ssh -Y?

If so, try using ssh -X.

---

### Post by ubun_tut on 2013-01-16
Hi, I am using ssh -X. I read that one way to deal with this is to use ssh -Y instead of ssh -X, but that seems to be sidestepping the problem instead of solving it.

---

