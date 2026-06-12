---
title: "Proxy with file and printer server on one box.."
date: 2009-03-03
forum: Philippine Team
---

### Post by dodimar on 2009-03-03
I want to setup a server at home... I want it to server 3 main purposes:
[LIST]
[*]Proxy server - there are three computers connected to our internet
[*]File server - so I can access files from any PC
[*]Print Server - there is only one printer shared
[/LIST]

My question are:
[LIST=1]
[*]Can this be done on a single box?
[*]For Print server, my current printer is not Linux compatible, it never worked in Linux, how do I share a printer using a Linux print server if it is n't linux ready. BTW, all clients are Windows XP...
[*]what are the best applications I can use?
[/LIST]

For info, this will be the specs of this server...
[LIST]
[*]AMD Duron 1ghz 64kb L2 cache
[*]128mb RAM
[*]80Gb hard drive
[*]NIC = 1
[*]32mb Video Card (no need since this one will be headless)
[/LIST]

Thanks for the input....

---

### Post by raxso on 2009-03-03
> **dodimar said:**
> I want to setup a server at home... I want it to server 3 main purposes:
[LIST]
[*]Proxy server - there are three computers connected to our internet
[*]File server - so I can access files from any PC
[*]Print Server - there is only one printer shared
[/LIST]

My question are:
[LIST=1]
[*]Can this be done on a single box?
[*]For Print server, my current printer is not Linux compatible, it never worked in Linux, how do I share a printer using a Linux print server if it is n't linux ready. BTW, all clients are Windows XP...
[*]what are the best applications I can use?
[/LIST]


For info, this will be the specs of this server...
[LIST]
[*]AMD Duron 1ghz 64kb L2 cache
[*]128mb RAM
[*]80Gb hard drive
[*]NIC = 1
[*]32mb Video Card (no need since this one will be headless)
[/LIST]

Thanks for the input....

This can be done on a single PC. For the proxy server you can use squid, for the file you can install samba, but for the printer i don't think it can be done, cause you said it already that you printer does not work with linux. Just used windows xp printer sharing.. just my two cents..

---

### Post by loell on 2009-03-03
you can use squid and samba in one box.

edit--

eheh.. too late.. ;)

---

### Post by dodimar on 2009-03-03
Do I need two NICs for Squid?

---

### Post by dodimar on 2009-03-03
I just realized, that if my printer won't work on this (print server), it will defeat my purpose of having this server....

experiment... experiment...

---

