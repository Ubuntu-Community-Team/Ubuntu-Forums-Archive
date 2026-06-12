---
title: "Change Local to WWW web server - Gutsy Server"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by moshazat on 2008-04-27
Hai:D

im a gutsy desktop edition user, now i currently try to create a server in my ubuntu desktop, and now i already can run phpnuke forum in local network, but my ip is still dynamic..

i want to ask a help, on how i can publish my local portal php webpage to World Wide Web... i already tried search n try some tutorial, but in the end it only crash my LAMP... 

i hope u can show me a tutorial for a beginner, on how to publish my local server webpage to wide web.. maybe starting with 

- on how to set a static ip
- how to choose which one of ip number from ifconfig
- or anything necessary...

i know that this is really high risk since it will involve about security... but i still want to learn n know basically about webpage server..

i hope u can share ur knowledge:)

---

### Post by nhandler on 2008-04-27
Look up dyndns or no-ip. Both are free services that will give you a subdomain that points to your ip. This will allow you to access your server from outside your network. They also have programs (that run on Ubuntu) that you can install which will make sure that the subdomain always points to your ip (even if it changes).

---

### Post by rubicon on 2008-04-27
I use ez-ipupdate, and it works flawlessly with dyndns.

Or - you could buy static IP from your ISP (this way you just can enter it in network-manager)
Or - you could buy VDS and get pro support for such needs ;)

---

### Post by moshazat on 2008-04-27
thanx :D i already can publish it now :D:D:D

---

