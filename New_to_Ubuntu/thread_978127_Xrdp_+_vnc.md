---
title: "Xrdp + vnc"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by xecure on 2008-11-10
I have enabled Remote desktop viewing on my ubuntu laptop and installed the xrdp package so that I can connect from a windows PC via Remote Desktop. It connects with no problem but when I try to login (via sesman-Xvnc) it says my login info is correct but it tries to connect to local host port 5910 and then it gives me an error. To be more clear i added a screen show i was getting. Anyone have any idea what im doing wrong?

---

### Post by spiderbatdad on 2008-11-10
not familiar with sesman...but the default port should be 5900. Is that the problem?

---

### Post by xecure on 2008-11-11
it automatically connects to port 5910, how can i change it to 5900?

---

### Post by spiderbatdad on 2008-11-11
[http://linux.die.net/man/5/xrdp.ini](http://linux.die.net/man/5/xrdp.ini)

You should be able to tell the client to connect on 5900. If not then set 5910 in xrdp.ini

---

### Post by spider-byte on 2008-12-14
I ran into the same problem. Heres what i did and it worked great.

1. Simply installed xrdp and tightvncserver through synaptic.
2. restart (even though it doesnt tell you to)

That's it. I tried and tried but xrdp didnt work until i simply restarted the system and installed tightvncserver. Now it works great. I even tried on different systems just to verify that it works as expected. 

I think xrdp calls the vncserver service on port 5910, so if vncserver is not installed it will give that port 5910 error.

---

### Post by MockY on 2010-02-10
I had issues as well. All it took was a reboot of the system. Sounds odd to have to do that, but it worked.

---

