---
title: "VNC4 - Connection Reset by Peer?"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by freebullets on 2008-09-05
I followed this tutorial: [http://ubuntuforums.org/showthread.php?t=197964](http://ubuntuforums.org/showthread.php?t=197964)

When I type ```
vncviewer localhost:5901
``` It says ```
Connection reset by peer (501)
```

What did I do wrong?

---

### Post by knix on 2008-09-05
Bump
I'm not sure, try vncviewer localhost:1, since that's what the howto says.

---

### Post by freebullets on 2008-09-06
It says the same thing

---

### Post by Mister.Vash on 2008-09-06
Can you post the contents of your /etc/xinetd.d/Xvnc file?

---

### Post by freebullets on 2008-09-06
Also, is there a better alternative than the one used in this tutorial?  I remember in ubuntu, you just had to check a checkbox.

```
service Xvnc
{
	type = UNLISTED
	disable = no
	socket_type = stream
	protocol = tcp
	wait = yes
	user = root
	server = /usr/bin/Xvnc
	server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
	port = 5901
}
```

---

### Post by freak42 on 2008-09-06
what about:
```
vncviewer localhost
```
?

---

### Post by freebullets on 2008-09-07
Connection Refused

---

### Post by freebullets on 2008-09-07
bump

---

### Post by knix on 2008-09-08
Just tried it out per directions; I get the same reults. However, it works when I use 127.0.0.1 instead of localhost (they're pretty much the same).

---

### Post by freebullets on 2008-09-09
localhost:1 gives "Connection Reset by Peer"
localhost:5901 gives "Connection Reset by Peer"
127.0.0.1:1 gives "Connection Reset by Peer" after a few seconds
127.0.0.1:5901 gives "Connection Reset by Peer" after a few seconds

Connection refuses if I don't specify a port

---

### Post by rohit_ece on 2010-02-14
did anyone got it ???
i am trying same, but it says connction closed by peer

---

