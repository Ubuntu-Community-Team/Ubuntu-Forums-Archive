---
title: "website hosted on local server not opening in LAN"
date: 2020-09-03
forum: New to Ubuntu
---

### Post by manpreetweb on 2020-09-03
[COLOR=#242729][FONT=Arial]I have a Ubuntu 20.04 Server with Apache. I have hosted a website like [/FONT][/COLOR][www.example.com]("http://www.example.com/")[COLOR=#242729][FONT=Arial]. This website is opening from the rest of the world as my domain's A record is pointing to my live ip. However i am not able to open that website within the LAN.[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-09-03
Welcome.

In your LAN it has the LAN's internal IP.

---

### Post by manpreetweb on 2020-09-03
LAN's ip is 192.168.x.x. However website is hosted using domain name [www.example.com](www.example.com). I want to open it as [www.example.com](www.example.com) within my LAN

---

### Post by CelticWarrior on 2020-09-03
Well, you can't, unless your router allows the DNS reversal (or something like that).

And may I ask what this has to do with Ubuntu?

---

### Post by TheFu on 2020-09-03
> **manpreetweb said:**
> LAN's ip is 192.168.x.x. However website is hosted using domain name [www.example.com](www.example.com). I want to open it as [www.example.com](www.example.com) within my LAN

a-setup your lan dns server to point [www.example.com](www.example.com) to the ip address for your web-server.
Or
b-setup the /etc/hosts file for all client machines on the lan to point [www.example.com](www.example.com) to the ip address for the web-server.

a is harder, since most people don''t have a dns setup.
b  is easier, but only for computers.  smartphones that are not rooted don't work.

---

### Post by SeijiSensei on 2020-09-04
On your LAN, what do you get when you run the command "host www.example.com" using your real domain name, of course.

Does it point to the outside address, to an address on the LAN, or does it return NXDOMAIN or something else?

For a couple of machines adding an entry to /etc/hosts is the easiest solution:
```
192.168.50.50     www.example.com
```

---

