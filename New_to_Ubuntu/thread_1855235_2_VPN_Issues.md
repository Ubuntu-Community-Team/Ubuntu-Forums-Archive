---
title: "2 VPN Issues"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by d4m1r on 2011-10-05
Hey guys, 2 recent VPN issues I have run into on 11.04 and not sure if they are already documented:

1)You have to restart Network Manager before you able to connect to a configured VPN

2)VPN disconnects every hour or so but reconnects instantly when I go to connect it manually again

The second might be cause by Network Manager as well, or the Cisco VPN app (vpnc), or even Terminal Server Client (connecting to my Windows XP machine @ work). Are there some logs I can monitor for, and when it disconnects, I can check what is causing it?

Let me know!

---

### Post by collisionystm on 2011-10-05
Do you have Keep Alive enabled?

---

### Post by d4m1r on 2011-10-05
> **collisionystm said:**
> Do you have Keep Alive enabled?

Where do I check that? I don't see an option for that under Network Manager>VPN :-?

---

### Post by AskTell on 2011-10-05
this is all i could find
[http://www.linuxquestions.org/questions/linux-networking-3/keep-alive-ping-script-134705/](http://www.linuxquestions.org/questions/linux-networking-3/keep-alive-ping-script-134705/)

---

### Post by d4m1r on 2011-10-05
> **AskTell said:**
> this is all i could find
[http://www.linuxquestions.org/questions/linux-networking-3/keep-alive-ping-script-134705/](http://www.linuxquestions.org/questions/linux-networking-3/keep-alive-ping-script-134705/)


Thanks but I don't think it is an automatic thing..Sometimes after 1 hour, other times after 2. It is never because of inactivity because I am constantly using the connection when its open. Last thing I want to do is setup a cron job to ping an IP every 59 minutes lol...

Also, Terminal Server Client is NOT the issue because it works fine, it is the VPN connection that is being dropped randomly.....

---

