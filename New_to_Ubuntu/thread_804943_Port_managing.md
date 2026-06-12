---
title: "Port managing"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by shortridge11 on 2008-05-23
ubuntu desktop 8.04

hi all, i was trying to open up some ports, and i was using the System/Admin/Network tools to do a port scan, and i needed to open some ports.  I tried using the ufw, but when i enabled it and tried adding rules to allow ports, the scan didn't show it as open.  For example, i tried adding port 21 to be open for all by typing
sudo ufw allow 21

is that right?
if not, i'd appreciate a point towards some port managing application.  I'd like to turn the ufw on, but i'm afraid all my ports will be shut off.  Thanks

---

### Post by neurostu on 2008-05-23
try firestarter, its got a great GUI front end and you can tell it specifically which ports you want open, or what services to open ports for and it picks the default port for the service.

to install:
```

sudo apt-get install firestarter

```

---

### Post by The Cog on 2008-05-23
Why is it that when someone says they want to open a port, someone else always says they need to install a firewall? That is probably the opposite of what they want to do.

On a default install, all the ports are closed because there is nothing listening on them - that's all. To open a port, install a service that listens on that port. If you want port 21 open, install an FTP server.

You may want to install a firewall to prevent all and sundry connecting to it, in which case you will have to open the firewall for port 21 from the users you do want to connect to it. You don't have to install a firewall to make FTP work - you install a firewall to **stop** it working for anybody.

---

### Post by shortridge11 on 2008-05-24
I'm just trying to remote view my desktop, and remote viewer uses port 5900, but it's not open when i port scan it.  How do i open that port??

---

### Post by dstin1 on 2008-05-24
open the port on your dsl modem/router.  Here is a guide.

[http://portforward.com/routers.htm]("http://portforward.com/routers.htm")

---

### Post by The Cog on 2008-05-24
System_>Preferences->Remote Desktop.
Enable Allow other users to view your desktop.

Confirm that you can see port 5900 listed with the command
```
netstat -lnt
```
If 5900 is listed then the port is open and listening. 

If you have a firewall intalled then you will also have to check there that connections to 5900 are allowed through. Ultimately, all firewalls end up configuring iptables (they are all just front-ends). You can see the iptables rules with
```
sudo iptables -nvL
```
but they take a lot of work to understand.

---

