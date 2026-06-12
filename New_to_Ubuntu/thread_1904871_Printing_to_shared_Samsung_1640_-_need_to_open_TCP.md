---
title: "Printing to shared Samsung 1640 - need to open TCP port 631"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2012-01-05
Hi Guys,

I have two machines each running Ubuntu 11.10.
Both machines are on my wi-fi network.

Machine A has a Samsung ML-1640 attached to it via USB.
I have it set to share.

Machine B can discover the printer but is unable to connect to it.

The print server troubleshooter takes forever to run then finally comes up with a notice that says "Unable to connect to the server make sure TCP port 631 is open"

I've put machine A into the DMZ on the router and I get the same error.  This makes me think that it's not the router blocking the connection, but a firewall rule on machine A.

A long time ago I seem to remember issuing a terminal command that closed all ports so I think that is the reason I can't connect to the printer.

Does anyone know how I can change my this to allow only TCP port 631 open?

Update: I found the command after searching a bit more:
```
sudo ufw allow <port number> 
```
I can print now.

---

